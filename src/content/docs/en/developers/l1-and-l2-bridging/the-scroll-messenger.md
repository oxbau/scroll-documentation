---
section: developers
date: Last Modified
title: "The Scroll Messenger"
lang: "en"
permalink: "todo"
excerpt: "The Scroll Messenger documentation for arbitrary message passing between L1 and L2."
---

# The Scroll Messenger

You can send arbitrary messages from L1 to L2 or vice versa through the Scroll Messenger contracts. This means we can execute functions on another chain in a secure and permissionless way. If you want to send a message from L1 to L2, use the messenger smart contract deployed on L1. If you want to send a message from L2 to L1, use the contract deployed on L1.

{% hint style="warning" %}
When sending a transaction through the **Scroll Messenger** deployed on L1 and L2, the resulting transaction sender (`CALLER` or `msg.sender`) will be the Messenger Contract address deployed on the receiving chain. In future Scroll versions, enforced transactions will be introduced as a L1 contract. Sending enforced transactions will allow setting the sender on L2 as the original one on L1. It will also allow 3rd parties to relay signed transactions and also setting the&#x20;
{% endhint %}

## Messenger API

Please visit the [npm library](https://www.npmjs.com/package/@scroll-tech/contracts?activeTab=code) for the complete Scroll contract API documentation.

### sendMessage

```solidity
function sendMessage(
  address target,
  uint256 value,
  bytes calldata message,
  uint256 gasLimit,
  address refundAddress
) external payable;
```

Sends arbitrary data from one chain to another. It allows us to execute functions cross-chain.

<table><thead><tr><th width="180">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>target</td><td>The address of account who receive the message. The receiver can be either a smart contract or a EOA wallet.</td></tr><tr><td>value</td><td>The amount of ether passed when call target contract.</td></tr><tr><td>message</td><td>The content of the message. This is the arbitrary calldata to be executed.</td></tr><tr><td>gasLimit</td><td>Gas limit required to complete the message relay on corresponding chain.</td></tr><tr><td>refundAddress</td><td>The address of account who will receive the refunded fee.</td></tr></tbody></table>