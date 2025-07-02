// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/IERC20.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";
import "@chainlink/contracts/src/v0.8/interfaces/VRFCoordinatorV2Interface.sol";
import "@chainlink/contracts/src/v0.8/VRFConsumerBaseV2.sol";

contract LuckyLoop is VRFConsumerBaseV2 {
    // ...

    // Mapping of user addresses to their entry status
    mapping(address => bool) public entries;

    // Array of all entries
    address[] public entryList;

    // Entry fee
    uint256 public entryFee;

    // Prize pool wallet
    address public prizePoolWallet;

    // Profit wallet
    address public profitWallet;

    // VRF Coordinator
    VRFCoordinatorV2Interface public vrfCoordinator;

    // ...

    constructor(
        address _prizePoolWallet,
        address _profitWallet,
        uint256 _entryFee,
        address _vrfCoordinator,
        bytes32 _keyHash,
        uint64 _subscriptionId
    ) VRFConsumerBaseV2(_vrfCoordinator) {
        prizePoolWallet = _prizePoolWallet;
        profitWallet = _profitWallet;
        entryFee = _entryFee;
        vrfCoordinator = VRFCoordinatorV2Interface(_vrfCoordinator);
        keyHash = _keyHash;
        subscriptionId = _subscriptionId;
    }

    function enterLottery() public payable {
        // Check if the user has already entered
        require(!entries[msg.sender], "You have already entered the lottery");

        // Check if the entry fee is paid
        require(msg.value >= entryFee, "Insufficient entry fee");

        // Add the user to the entry list
        entries[msg.sender] = true;
        entryList.push(msg.sender);

        // Split the entry fee
        splitEntryFees(msg.value);
    }

    function selectWinner() public {
        // Request a random number from the VRF Coordinator
        vrfCoordinator.requestRandomness(subscriptionId, keyHash, 1000000);
    }

    function fulfillRandomness(uint256 _randomness) internal override {
        // Select a winner based on the random number
        uint256 winnerIndex = _randomness % entryList.length;
        address winner = entryList[winnerIndex];

        // Distribute the prize to the winner
        distributePrize(winner);
    }

    function distributePrize(address _winner) internal {
        // Transfer the prize to the winner's wallet
        payable(_winner).transfer(address(this).balance);
    }

    function splitEntryFees(uint256 _entryFee) internal {
        // Split the entry fee between the prize pool wallet and the profit wallet
        uint256 prizePoolShare = _entryFee / 2;
        uint256 profitShare = _entryFee - prizePoolShare;

        payable(prizePoolWallet).transfer(prizePoolShare);
        payable(profitWallet).transfer(profitShare);
    }
}
