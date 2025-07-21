---
description: Integrate PoH V2 to verify real humans in your application
---

# Proof of Humanity 2.0 Integration Guide

### Key Features

* **Soulbound IDs**: Persistent human identities that survive wallet changes
* **Multi-chain deployment**: Available on Ethereum mainnet and Gnosis chain
* **Cross-chain transfers**: Move identities between supported chains
* **Enhanced vouching**: Support for both on-chain and off-chain (EIP-712) vouching
* **V1 compatibility**: Seamless migration path from V1

### Core Concepts

#### Soulbound IDs

Proof of Humanity V2 introduces **soulbound IDs** that represent unique human identities. Unlike V1 where each registration corresponded to a specific wallet address, V2 uses unique humanity IDs (`pohID` or `humanityId`) that persist across wallet changes.

**Key principle:** `1 human → 1 wallet address ↔ 1 humanity`&#x20;

If a user loses access to their wallet, they can request removal of the lost address and register with a new one using the same PoH ID, preserving their reputation and assets tied to the identity.

**Recovery Process:**

```solidity
// 1. Human loses access to wallet
humanity.owner == lostAddress
isHuman(lostAddress) == true

// 2. Human requests removal of lost address
humanity.owner == address(0)
isHuman(lostAddress) == false

// 3. Human registers with new wallet address
humanity.owner == newAddress
isHuman(newAddress) == true
```

#### Multi-Chain Architecture

PoH V2 operates across multiple blockchains with a sophisticated state synchronization system:

* **Home Chain**: The primary chain where a humanity is claimed and managed
* **State Updates**: Humanity status synchronized across chains via bridge gateways
* **Universal IDs**: Humanity IDs are consistent across all supported chains
* **Transfer Mechanism**: Humanities can be transferred between chains with cooldown periods

{% hint style="info" %}
**Important**: A humanity can only have **one active home chain** at a time, but its state can be reflected on multiple chains.
{% endhint %}

#### Humanity Lifecycle

A humanity progresses through distinct states: \
**Unclaimed** → **Vouching** → **Resolving** → **Claimed** → **Renewal** → **Expired/Revoked**

### Contract Architecture

#### ProofOfHumanity Contract

* Core functionality similar to V1 with enhanced soulbound features
* Manages humanity claims, renewals, and revocations
* Handles vouching and challenge mechanisms with dispute resolution
* Supports both on-chain and off-chain (EIP-712) vouching

#### ProofOfHumanityExtended Contract

* Enhanced version deployed on Ethereum mainnet
* Includes **Fork Module** for V1 compatibility
* Allows seamless transition from V1 to V2

#### CrossChainProofOfHumanity Contract

* Manages cross-chain state updates and transfers
* Stores received state updates from other chains
* Handles humanity transfers between chains with transfer cooldowns
* Ensures consistency across multi-chain deployments

#### Bridge Gateways

* **AMB (Arbitrary Message Bridge)** gateways for cross-chain communication
* Enable secure message passing between chain instances
* Support both state updates and humanity transfers

### Deployment Addresses

#### Ethereum Mainnet

<table><thead><tr><th width="313.34375">Contract</th><th>Address</th></tr></thead><tbody><tr><td>ProofOfHumanityExtended</td><td>0xbE9834097A4E97689d9B667441acafb456D0480A</td></tr><tr><td>CrossChainProofofHumanity</td><td>0xa478095886659168E8812154fB0DE39F103E74b2</td></tr><tr><td>AMB Bridge Gateway</td><td>0xddafACf8B4a5087Fc89950FF7155c76145376c1e</td></tr><tr><td>Fork Module</td><td>0x068a27Db9c3B8595D03be263d52c813cb2C99cCB</td></tr></tbody></table>

#### Gnosis Chain

<table><thead><tr><th width="281.46875">Contract</th><th>Address </th></tr></thead><tbody><tr><td>ProofOfHumanity</td><td>0xa4AC94C4fa65Bb352eFa30e3408e64F72aC857bc</td></tr><tr><td>CrossChainProofOfHumanity</td><td>0x16044E1063C08670f8653055A786b7CC2034d2b0</td></tr><tr><td>AMB Bridge Gateway</td><td>0x6Ef5073d79c42531352d1bF5F584a7CBd270c6B1</td></tr></tbody></table>

### Interface Definitions&#x20;

Core Interface

```solidity
interface IProofOfHumanity {
    // Core verification functions
    function isHuman(address _account) external view returns (bool);
    function isClaimed(bytes20 _humanityId) external view returns (bool);
    function humanityOf(address _account) external view returns (bytes20);
    function boundTo(bytes20 _humanityId) external view returns (address);
    
    // Detailed information function
    function getHumanityInfo(bytes20 _humanityId) external view returns (
        bool vouching,              // Is this humanity currently vouching for someone
        bool pendingRevocation,     // Is there a pending revocation request
        uint48 nbPendingRequests,   // Number of pending requests in challenging phase
        uint40 expirationTime,      // When the humanity expires
        address owner,              // Current owner address
        uint256 nbRequests          // Total number of requests made
    );
    
    // Statistics and request information
    function getClaimerRequestId(address _claimer) external view returns (uint256);
    function getNumberOfVouches(bytes20 _humanityId, uint256 _requestId) external view returns (uint256);
    function getHumanityCount() external view returns (uint256);
}
```

#### Vouching Interface

```solidity
interface IProofOfHumanityVouching {
    
    struct SignatureVouch {
        uint40 expirationTime; // Time when the signature expires
        uint8 v;               // 'v' value of the signature  
        bytes32 r;             // 'r' value of the signature
        bytes32 s;             // 's' value of the signature
    }
    
    // Basic vouching functions
    function addVouch(address _account, bytes20 _humanityId) external;
    function removeVouch(address _account, bytes20 _humanityId) external;
    function vouches(address _voucher, address _claimer, bytes20 _humanityId) external view returns (bool);
    
    // Advanced vouching with signature support
    function advanceState(
        address _claimer,
        address[] calldata _vouches,
        SignatureVouch[] calldata _signatureVouches
    ) external;
}
```

#### Cross-Chain interface

```solidity
interface ICrossChainProofOfHumanityView {
    // View functions (same as main interface)
    function isHuman(address _account) external view returns (bool);
    function isClaimed(bytes20 _humanityId) external view returns (bool);
    function boundTo(bytes20 _humanityId) external view returns (address);
    function humanityOf(address _account) external view returns (bytes20);
    
    // Cross-chain operations
    function updateHumanity(address _bridgeGateway, bytes20 _humanityId) external;
    function transferHumanity(address _bridgeGateway) external;
       
    // Receive functions (called by bridge)
    function receiveUpdate(address _owner, bytes20 _humanityId, uint40 _expirationTime, bool _isActive) external;
    function receiveTransfer(address _owner, bytes20 _humanityId, uint40 _expirationTime, bytes32 _transferHash) external;
}

```

#### Request Management Interface

```solidity
interface IProofOfHumanityRequests {
   enum Party {
        None,
        Requester,
        Challenger
    }

    enum Reason {
        None,
        IncorrectSubmission,
        IdentityTheft,
        SybilAttack,
        Deceased
    }
    
     // Request creation
    function claimHumanity(bytes20 _humanityId, string calldata _evidence, string calldata _name) external payable;
    function renewHumanity(string calldata _evidence) external payable;
    function revokeHumanity(bytes20 _humanityId, string calldata _evidence) external payable;
    
    // Request management
    function fundRequest(bytes20 _humanityId, uint256 _requestId) external payable;
    function withdrawRequest() external;
    function executeRequest(bytes20 _humanityId, uint256 _requestId) external;
    
    // Challenges and disputes
    function challengeRequest(
        bytes20 _humanityId,
        uint256 _requestId,
        Reason _reason,
        string calldata _evidence
    ) external payable;
    
    function fundAppeal(address _arbitrator, uint256 _disputeId, Party _side) external payable;
    
    // Evidence and fee management
    function submitEvidence(bytes20 _humanityId, uint256 _requestId, string calldata _evidence) external;
    function withdrawFeesAndRewards(
        address payable _beneficiary,
        bytes20 _humanityId,
        uint256 _requestId,
        uint256 _challengeId,
        uint256 _round
    ) external;
}
```

### Quick Start Integration

#### 1. Install Interface

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

interface IProofOfHumanity {
    function isHuman(address _account) external view returns (bool);
    function humanityOf(address _account) external view returns (bytes20);
    function isClaimed(bytes20 _humanityId) external view returns (bool);
    function boundTo(bytes20 _humanityId) external view returns (address);
}
```

#### 2. Basic Integration

```solidity
contract MyDApp {
    IProofOfHumanity public immutable poh;
    
    constructor(address _pohAddress) {
        poh = IProofOfHumanity(_pohAddress);
    }
    
    modifier onlyHuman() {
        require(poh.isHuman(msg.sender), "Must be verified human");
        _;
    }
    
    function humanOnlyFunction() external onlyHuman {
        // Your logic here
    }
}
```

#### 3. Chain Selection

Choose the appropriate contract address based on your deployment chain:

```solidity
// For Ethereum mainnet
address constant POH_ETHEREUM = 0xbE9834097A4E97689d9B667441acafb456D0480A;

// For Gnosis chain  
address constant POH_GNOSIS = 0xa4AC94C4fa65Bb352eFa30e3408e64F72aC857bc;
```

#### Method 1: Basic Human Verification

**Use case**: Simple verification that an address belongs to a verified human.

**Implementation Example**

```solidity
contract BasicVerification {
    IProofOfHumanity public immutable poh;
    
    constructor(address _pohAddress) {
        poh = IProofOfHumanity(_pohAddress);
    }
    
    function verifyHuman(address _user) external view returns (bool) {
        return poh.isHuman(_user);
    }
    
    function getHumanityInfo(address _user) external view returns (
        bool isVerified,
        bytes20 humanityId
    ) {
        humanityId = poh.humanityOf(_user);
        isVerified = humanityId != bytes20(0);
    }
}
```

#### Method 2: Soulbound Identity Integration

**Use Case**: Applications requiring persistent identity across wallet changes (reputation systems, social platforms, DAOs).

**Implementation**

```solidity
contract SoulboundIntegration {
    IProofOfHumanity public immutable poh;
    
    struct UserProfile {
        uint256 registrationTime;
        uint256 reputation;
        string username;
        bool isActive;
    }
    
    // Store data by humanity ID, not address
    mapping(bytes20 => UserProfile) public profiles;
    mapping(bytes20 => address) public currentAddress;
    
    event ProfileCreated(bytes20 indexed humanityId, address indexed user);
    event AddressUpdated(bytes20 indexed humanityId, address indexed oldAddress, address indexed newAddress);
    
    function createProfile(string calldata _username) external {
        //First verify user is actually human
        require(poh.isHuman(msg.sender), "Must be verified human");
        
        //Then get their humanity ID
        bytes20 humanityId = poh.humanityOf(msg.sender);
        require(humanityId != bytes20(0), "Failed to get humanity ID");
        require(!profiles[humanityId].isActive, "Profile already exists");
        
        profiles[humanityId] = UserProfile({
            registrationTime: block.timestamp,
            reputation: 0,
            username: _username,
            isActive: true
        });
        
        currentAddress[humanityId] = msg.sender;
        emit ProfileCreated(humanityId, msg.sender);
    }
    
    function updateReputation(address _user, uint256 _newReputation) external {
        //Verify user is still human before updating
        require(poh.isHuman(_user), "User must be verified human");
        
        bytes20 humanityId = poh.humanityOf(_user);
        require(profiles[humanityId].isActive, "Profile not found");
        
        // Update address if it changed
        if (currentAddress[humanityId] != _user) {
            emit AddressUpdated(humanityId, currentAddress[humanityId], _user);
            currentAddress[humanityId] = _user;
        }
        
        profiles[humanityId].reputation = _newReputation;
    }
    
    function getProfile(address _user) external view returns (UserProfile memory) {
        bytes20 humanityId = poh.humanityOf(_user);
        return profiles[humanityId];
    }
    
    function getProfileByHumanityId(bytes20 _humanityId) external view returns (UserProfile memory) {
        return profiles[_humanityId];
    }

 
    //Additional helper functions for better integration
    function isProfileActive(address _user) external view returns (bool) {
        if (!poh.isHuman(_user)) return false;
        bytes20 humanityId = poh.humanityOf(_user);
        return profiles[humanityId].isActive;
    }
    
    function getActiveHumanityId(address _user) external view returns (bytes20) {
        require(poh.isHuman(_user), "User not verified");
        return poh.humanityOf(_user);
    }
    
    //Handle humanity expiration/revocation
    function deactivateExpiredProfile(bytes20 _humanityId) external {
        require(profiles[_humanityId].isActive, "Profile not active");
        
        // Check if humanity is still claimed
        address currentOwner = poh.boundTo(_humanityId);
        if (currentOwner == address(0)) {
            profiles[_humanityId].isActive = false;
        }
    }
}
```

#### Method 3: Cross-Chain Integration

**Use Case**: Applications operating across multiple chains.

**Multi-Chain Verification**

```solidity
interface ICrossChainProofOfHumanity {
    function isHuman(address _account) external view returns (bool);
    function isClaimed(bytes20 _humanityId) external view returns (bool);
    function humanityOf(address _account) external view returns (bytes20);
    function boundTo(bytes20 _humanityId) external view returns (address);
}

contract CrossChainDApp {
    IProofOfHumanity public immutable pohMain;
    ICrossChainProofOfHumanity public immutable pohCrossChain;
    
    constructor(address _pohMain, address _pohCrossChain) {
        pohMain = IProofOfHumanity(_pohMain);
        pohCrossChain = ICrossChainProofOfHumanity(_pohCrossChain);
    }
    
    function isVerifiedHuman(address _account) public view returns (bool) {
        // Check both main contract and cross-chain state
        return pohMain.isHuman(_account) || pohCrossChain.isHuman(_account);
    }
    
    function getUniversalHumanityId(address _account) public view returns (bytes20) {
        bytes20 humanityId = pohMain.humanityOf(_account);
        if (humanityId == bytes20(0)) {
            humanityId = pohCrossChain.humanityOf(_account);
        }
        return humanityId;
    }
    
    function getHumanityOwner(bytes20 _humanityId) public view returns (address) {
        address owner = pohMain.boundTo(_humanityId);
        if (owner == address(0)) {
            owner = pohCrossChain.boundTo(_humanityId);
        }
        return owner;
    }
}
```

### Advanced Integration Patterns

#### Event Monitoring

Monitor important PoH events for real-time updates:

```solidity
contract EventMonitor {
    IProofOfHumanity public immutable poh;
    
    mapping(bytes20 => bool) public activeHumanities;
    mapping(address => bytes20) public humanityToUser;
    
    event HumanityStatusChanged(bytes20 indexed humanityId, address indexed user, bool isActive);
    event HumanityAddressUpdated(bytes20 indexed humanityId, address indexed oldUser, address indexed newUser);
    
    constructor(address _pohAddress) {
        poh = IProofOfHumanity(_pohAddress);
    }
    
    // Call when monitoring HumanityClaimed events
    function handleHumanityClaimed(bytes20 humanityId, address user) external {
        require(poh.isClaimed(humanityId), "Humanity not claimed");
        activeHumanities[humanityId] = true;
        humanityToUser[user] = humanityId;
        emit HumanityStatusChanged(humanityId, user, true);
    }
    
    // Call when monitoring HumanityRevoked events  
    function handleHumanityRevoked(bytes20 humanityId, address user) external {
        activeHumanities[humanityId] = false;
        delete humanityToUser[user];
        emit HumanityStatusChanged(humanityId, user, false);
    }
}  
```

#### Detailed State Queries

For applications requiring comprehensive humanity information:

```solidity
interface IProofOfHumanityDetailed {
    function getHumanityInfo(bytes20 _humanityId) external view returns (
        bool vouching,              // Currently vouching for someone
        bool pendingRevocation,     // Has pending revocation request
        uint48 nbPendingRequests,   // Number of pending requests
        uint40 expirationTime,      // When humanity expires
        address owner,              // Current owner address
        uint256 nbRequests          // Total requests made
    );
}

contract DetailedIntegration {
    IProofOfHumanityDetailed public immutable poh;
    
    struct HumanityStatus {
        bool isValid;
        bool canVouch;
        bool isPending;
        uint256 timeToExpiry;
        address currentOwner;
    }
    
    constructor(address _pohAddress) {
        poh = IProofOfHumanityDetailed(_pohAddress);
    }
    
    function getHumanityStatus(bytes20 _humanityId) external view returns (HumanityStatus memory) {
        (
            bool vouching,
            bool pendingRevocation,
            uint48 nbPendingRequests,
            uint40 expirationTime,
            address owner,
        ) = poh.getHumanityInfo(_humanityId);
        
        bool isValid = owner != address(0) && block.timestamp < expirationTime;
        bool canVouch = isValid && !vouching && !pendingRevocation;
        bool isPending = pendingRevocation || nbPendingRequests > 0;
        uint256 timeToExpiry = expirationTime > block.timestamp ? 
                              expirationTime - block.timestamp : 0;
        
        return HumanityStatus({
            isValid: isValid,
            canVouch: canVouch,
            isPending: isPending,
            timeToExpiry: timeToExpiry,
            currentOwner: owner
        });
    }
}
```

#### Registration Vouching Integration

**Understanding PoH's Vouching System:**

PoH's vouching system is **exclusively for the registration process** - when new people are trying to become verified humans.&#x20;

**How Registration Vouching Works:**

1. Someone calls `claimHumanity()` to register as a human
2. Existing verified humans call `addVouch()` to support them
3. Once enough vouches are collected, the request can advance to the resolving phase
4. The person either becomes verified or gets challenged

### Migration from V1

#### V1 Compatibility

The `ProofOfHumanityExtended` contract includes automatic V1 compatibility through the Fork Module:

* ✅ V1 registrations continue to work
* ✅ No immediate migration required
* ✅ Seamless transition available
* ✅ `isHuman()` checks both V1 and V2

#### Migration Support Implementation

```solidity
contract MigrationHelper {
    IProofOfHumanity public immutable pohV2;
    
    constructor(address _pohV2Address) {
        pohV2 = IProofOfHumanity(_pohV2Address);
    }
    
    function getRegistrationVersion(address _user) external view returns (string memory) {
        if (!pohV2.isHuman(_user)) {
            return "not_registered";
        }
        
        bytes20 humanityId = pohV2.humanityOf(_user);
        
        // V1 users have humanity ID equal to their address
        if (humanityId == bytes20(_user)) {
            return "v1";
        }
        
        return "v2";
    }
    
    function shouldMigrate(address _user) external view returns (bool) {
        if (!pohV2.isHuman(_user)) return false;
        
        bytes20 humanityId = pohV2.humanityOf(_user);
        return humanityId == bytes20(_user); // V1 indicator
    }
    
    function isHumanAnyVersion(address _user) external view returns (bool) {
        // Automatically checks both V2 and V1 via Fork Module
        return pohV2.isHuman(_user);
    }
}
```

#### Migration Benefits

Migrating from V1 to V2 provides:

* **Soulbound identity**: Persistent across wallet changes
* **Cross-chain support**: Use identity on multiple chains
* **Enhanced security**: Improved dispute and vouching mechanisms
* **Future compatibility**: Access to new features and integrations

### Quick Reference

#### Essential Functions

```solidity
// Basic verification
function isHuman(address _account) external view returns (bool);
function humanityOf(address _account) external view returns (bytes20);

// Humanity info
function isClaimed(bytes20 _humanityId) external view returns (bool);
function boundTo(bytes20 _humanityId) external view returns (address);

// Detailed info (if needed)
function getHumanityInfo(bytes20 _humanityId) external view returns (
    bool vouching, bool pendingRevocation, uint48 nbPendingRequests,
    uint40 expirationTime, address owner, uint256 nbRequests
);
```

Contract Addresses Quick Copy

```solidity
// Ethereum Mainnet
address constant POH_ETHEREUM = 0xbE9834097A4E97689d9B667441acafb456D0480A;
address constant CROSSCHAIN_ETHEREUM = 0xa478095886659168E8812154fB0DE39F103E74b2;

// Gnosis Chain  
address constant POH_GNOSIS = 0xa4AC94C4fa65Bb352eFa30e3408e64F72aC857bc;
address constant CROSSCHAIN_GNOSIS = 0x16044E1063C08670f8653055A786b7CC2034d2b0;
```

### Support Resources

* **Documentation**: [Proof of Humanity Docs](https://proofofhumanity.id/)
* **GitHub**: [PoH V2 Repository](https://github.com/Proof-Of-Humanity/proof-of-humanity-v2-contracts)
* **Support:** contact@kleros.io
* **Forum**: [PoH Governance](https://gov.proofofhumanity.id/)
