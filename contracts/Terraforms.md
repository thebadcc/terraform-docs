<style>
ul#menu li {
  display:inline;
}
</style>

:::
<ul id="menu">
  <li><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path xmlns="http://www.w3.org/2000/svg" style="opacity:0.963" fill="#21325b" d="M 54.5,-0.5 C 58.5,-0.5 62.5,-0.5 66.5,-0.5C 93.181,3.51828 110.848,18.3516 119.5,44C 118.906,46.7902 117.739,49.2902 116,51.5C 109.93,58.2404 103.263,64.2404 96,69.5C 95.6667,56.5 95.3333,43.5 95,30.5C 94.5,29.3333 93.6667,28.5 92.5,28C 87.7133,27.1215 83.0466,27.4548 78.5,29C 77.6743,45.426 77.1743,61.926 77,78.5C 75.1535,81.0072 72.6535,82.3406 69.5,82.5C 69.6666,69.1625 69.4999,55.8292 69,42.5C 68.5,42 68,41.5 67.5,41C 63.1667,40.3333 58.8333,40.3333 54.5,41C 53.3333,41.5 52.5,42.3333 52,43.5C 51.6667,58.1667 51.3333,72.8333 51,87.5C 49.005,89.747 46.505,90.747 43.5,90.5C 43.6665,78.8286 43.4999,67.1619 43,55.5C 42.5,55 42,54.5 41.5,54C 36.8333,53.3333 32.1667,53.3333 27.5,54C 26.8742,54.7504 26.3742,55.5838 26,56.5C 25.6667,68.5 25.3333,80.5 25,92.5C 14.6817,98.5742 7.68166,95.9075 4,84.5C 2.16036,79.1258 0.660356,73.7925 -0.5,68.5C -0.5,63.5 -0.5,58.5 -0.5,53.5C 5.94861,23.3846 24.2819,5.38464 54.5,-0.5 Z"/><path xmlns="http://www.w3.org/2000/svg" style="opacity:0.986" fill="#979695" d="M 122.5,56.5 C 122.5,59.1667 122.5,61.8333 122.5,64.5C 117.5,98.1667 98.1667,117.5 64.5,122.5C 62.1667,122.5 59.8333,122.5 57.5,122.5C 45.4403,121.42 34.4403,117.254 24.5,110C 57.0947,105.28 85.5947,92.1136 110,70.5C 113.716,66.4518 117.05,62.1185 120,57.5C 120.671,56.7476 121.504,56.4142 122.5,56.5 Z"/></svg>
</li>
</ul> 
:::

+++ Read

+++ Write

+++ Code

=== Ownable.sol 
``` 
// SPDX-License-Identifier: MIT
// OpenZeppelin Contracts v4.4.0 (access/Ownable.sol)

pragma solidity ^0.8.0;

import "../utils/Context.sol";

/**
 * @dev Contract module which provides a basic access control mechanism, where
 * there is an account (an owner) that can be granted exclusive access to
 * specific functions.
 *
 * By default, the owner account will be the one that deploys the contract. This
 * can later be changed with {transferOwnership}.
 *
 * This module is used through inheritance. It will make available the modifier
 * `onlyOwner`, which can be applied to your functions to restrict their use to
 * the owner.
 */
abstract contract Ownable is Context {
    address private _owner;

    event OwnershipTransferred(address indexed previousOwner, address indexed newOwner);

    /**
     * @dev Initializes the contract setting the deployer as the initial owner.
     */
    constructor() {
        _transferOwnership(_msgSender());
    }

    /**
     * @dev Returns the address of the current owner.
     */
    function owner() public view virtual returns (address) {
        return _owner;
    }

    /**
     * @dev Throws if called by any account other than the owner.
     */
    modifier onlyOwner() {
        require(owner() == _msgSender(), "Ownable: caller is not the owner");
        _;
    }

    /**
     * @dev Leaves the contract without owner. It will not be possible to call
     * `onlyOwner` functions anymore. Can only be called by the current owner.
     *
     * NOTE: Renouncing ownership will leave the contract without an owner,
     * thereby removing any functionality that is only available to the owner.
     */
    function renounceOwnership() public virtual onlyOwner {
        _transferOwnership(address(0));
    }

    /**
     * @dev Transfers ownership of the contract to a new account (`newOwner`).
     * Can only be called by the current owner.
     */
    function transferOwnership(address newOwner) public virtual onlyOwner {
        require(newOwner != address(0), "Ownable: new owner is the zero address");
        _transferOwnership(newOwner);
    }

    /**
     * @dev Transfers ownership of the contract to a new account (`newOwner`).
     * Internal function without access restriction.
     */
    function _transferOwnership(address newOwner) internal virtual {
        address oldOwner = _owner;
        _owner = newOwner;
        emit OwnershipTransferred(oldOwner, newOwner);
    }
}
```
=== Panel 2
Content 2
===

+++
