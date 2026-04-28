# Upgradeable-Storage-V1
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract StorageV1 {
    uint256 public value;
    address public admin;

    event ValueUpdated(uint256 oldValue, uint256 newValue);

    constructor() {
        admin = msg.sender;
    }

    function setValue(uint256 _newValue) public {
        require(msg.sender == admin, "Only admin");
        uint256 oldValue = value;
        value = _newValue;
        emit ValueUpdated(oldValue, _newValue);
    }
}
