---
eip:
title:
author:
discussions-to:
status:
type:
category:
created:
---

## Simple Summary
A standard interface for ERC20 (or equivalent) token transfers between Ethereum and Layer 2 systems.

## Abstract
WIP

## Motivation
A shared interface between Ethereum and the various Layer 2 systems will improve interoperability and reduce overhead for both users and developers. Common tooling can be built and development time saved because things "just work" between various L2 ecosystems.

## Specification
```solidity
/**
 * @title ERCXXX
 * @dev Generic interface for moving tokens between L1 and L2.
 * Same interface should be usable on both L1 and L2.
 */
interface ERCXXX {
    /**
     * @dev Emitted when a token deposit is initialized.
     */
    event DepositInitiated(address indexed _from, address _to, uint256 _amount);
    
    /**
     * @dev Emitted when a token withdrawal is finalized.
     */
    event WithdrawalFinalized(address indexed _to, uint256 _amount);

    /**
     * @dev Triggers a deposit of the token amount into the other system 
     * (L2 if on L1, L1 if on L2).
     * @param _amount Number of tokens to deposit.
     */
    function deposit(uint256 _amount) external;
    
    /**
     * @dev Same as `deposit`, but you can specify the address that'll
     * receive the funds on the other chain.
     * @param _to Address to receive the deposited funds.
     * @param _amount Number of tokens to deposit.
     */
    function depositTo(address _to, uint256 _amount) external;
    
    /**
     * @dev Completes a withdrawal that was initiated on the other system.
     * Assumes this method is called by some other contract that verifies a
     * proof of validity for the withdrawal.
     * @param _to Address to receive the withdrawn funds.
     * @param _amount Withdrawal amount.
     */
    function finalizeWithdrawal(address _to, uint256 _amount) external;
}

```

## Rationale
This interface should ideally be generic enough to be applicable to most (if not all) Layer 2 systems while still remaining useful. In practice, Layer 2 systems have to deal with messy proof systems. Including the details of these proof systems would most likely limit the utility of this proposal.

## Backwards Compatibility
WIP

## Test Cases
WIP

## Reference Implementation
WIP

## Security Considerations
WIP

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
