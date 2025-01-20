---
description: A simpler way to build arbitrable applications.
---

# Arbitrable Proxy

The arbitrable proxy contract abstracts away most of the heavy lifting associated with implementing the ERC792 and ERC1497 standards from scratch in an arbitrable application. It abstracts away the evidence and appeal management logic from your contact, requiring you to handle just the dispute creation and ruling retrieval logic.

## Getting Started

### Step 1:

Import the IArbitrableProxy interface into your project

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

import "@kleros/erc-792/contracts/IArbitrator.sol";

/**
 *  @title IArbitrableProxy
 *  A general purpose arbitrable contract. Supports non-binary rulings.
 */
interface IArbitrableProxy {
    function arbitrator() external view returns (IArbitrator arbitrator);

    function createDispute(
        bytes calldata _arbitratorExtraData,
        string calldata _metaevidenceURI,
        uint256 _numberOfRulingOptions
    ) external payable returns (uint256 disputeID);

    struct DisputeStruct {
        bytes arbitratorExtraData;
        bool isRuled;
        uint256 ruling;
        uint256 disputeIDOnArbitratorSide;
    }

    function externalIDtoLocalID(
        uint256 _externalID
    ) external returns (uint256 localID);

    function disputes(
        uint256 _localID
    )
        external
        returns (
            bytes memory extraData,
            bool isRuled,
            uint256 ruling,
            uint256 disputeIDOnArbitratorSide
        );

    function submitEvidence(uint256 _localDisputeID, string calldata _evidenceURI) external;
}

```

#### Usage

```solidity
contract MyArbitrable {
    IArbitrableProxy arbitrableProxy = IArbitrableProxy(<ARBITRATOR_ADDRESS>);
}
```

### Step 2:

Create disputes through the proxy and paying the arbitration cost through the same transaction.

{% hint style="info" %}
The arbitration cost paid when calling the `createDispute()` function of the arbitrableProxy is the same as that of calling the same function on the final arbitrator (i.e. Kleros Court). The cost estimation is therefore best done by directly polling it from the final arbitrator (i.e. the [`arbitrationCost()` function of Kleros Liquid](https://etherscan.deth.net/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069#L1816))
{% endhint %}

```solidity
contract MyArbitrable {
    IArbitrableProxy arbitrableProxy = IArbitrableProxy(<ARBITRATOR_ADDRESS>);
    
    function foo(
        bytes calldata extraData, 
        string memory evidenceURI, 
        uint256 rulingOptions
        ) {
        uint256 disputeID = arbitrableProxy.createDispute{value: msg.value}(
            extraData, 
            evidenceURI, 
            rulingOptions
            );
            
        // do something with disputeID
    }
}
```

### Step 3:

Create a `fetchRuling` function.&#x20;

A key difference between using the proxy and implementing your own ERC792 arbitrable from scratch is that a rule function is not directly called in your contract by the arbitrator. The proxy stores the data of rulings locally in an array and its up to you to query the rulings relevant to your contract.

Let's first take a look at how rulings are stored on the arbitrable proxy then move on to how to implement a fetchRuling function in your contract.

```solidity
/// https://github.com/kleros/arbitrable-proxy-contracts/blob/master/contracts/ArbitrableProxy.sol

contract ArbitrableProxy is IDisputeResolver {
    // ...
    // ...
    // ...
    struct DisputeStruct {
        bytes arbitratorExtraData;
        bool isRuled;
        uint256 ruling;
        uint256 disputeIDOnArbitratorSide;
    }
    
    DisputeStruct[] public disputes;
    
    function rule(uint256 _externalDisputeID, uint256 _ruling) external override {
        uint256 localDisputeID = externalIDtoLocalID[_externalDisputeID];
        DisputeStruct storage dispute = disputes[localDisputeID];
        require(msg.sender == address(arbitrator), "Only the arbitrator can execute this.");
        require(_ruling <= numberOfRulingOptions[localDisputeID], "Invalid ruling.");
        require(dispute.isRuled == false, "This dispute has been ruled already.");

        dispute.isRuled = true;
        dispute.ruling = _ruling;

        Round[] storage rounds = disputeIDtoRoundArray[localDisputeID];
        Round storage lastRound = disputeIDtoRoundArray[localDisputeID][rounds.length - 1];
        // If only one ruling option is funded, it wins by default. Note that if any other ruling had funded, an appeal would have been created.
        if (lastRound.fundedRulings.length == 1) {
            dispute.ruling = lastRound.fundedRulings[0];
        }

        emit Ruling(IArbitrator(msg.sender), _externalDisputeID, dispute.ruling);
    }
}
```

```solidity
contract MyArbitrable {
    IArbitrableProxy arbitrableProxy = IArbitrableProxy(<ARBITRATOR_ADDRESS>);
    function foo(
        bytes calldata extraData, 
        string memory evidenceURI, 
        uint256 rulingOptions
        ) {
        uint256 disputeID = arbitrableProxy.createDispute{value: msg.value}(
            extraData, 
            evidenceURI, 
            rulingOptions
            );
            
        // do something with disputeID
    }
    
    function fetchRuling(uint256 disputeID) {
        (, bool isRuled, uint256 ruling) = arbitrableProxy.disputes(disputeID)
        
        // do something with ruling if isRuled
    }
}
```

And that's it! With this, you would have a fully trustless integration with Kleros Court for less than half the work of a fully ERC792 compliant integration.
