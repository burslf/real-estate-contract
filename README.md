
# Real Estate Agency Smart Contract
## Overview
This is a smart contract for a real estate agency that allows minting, buying and selling properties on the blockchain. It is built on the Ethereum platform and uses the ERC-1155 token standard for non-fungible tokens.

## Features V1
The smart contract has the following features:

* Minting Properties: Property owners can mint new properties by paying the required agency fees.
* Buying Properties: Buyers can purchase properties by paying the required amount in Ether.
* IPFS Integration: The contract integrates with IPFS to store property metadata and make it available to buyers.
* Revenue Sharing: The contract keeps track of the revenue generated by each property and allows owners to withdraw their share.
* Agency Fees: The contract charges a percentage of the minting price as agency fees, which are collected by the contract owner.
* NFT Receipt: After a user buy a property, a NFT will get into his wallet with some metadata (can be set via IPFS and set to the contract using the `setIpfsHash(uint256 tokenId, uint256 subId, string memory hash)` - the hash can be an empty string.)

## Functions V1

`initialize(uint256 _agencyFees) external initializer`
Initializes the contract with the specified agency fees percentage.

`setAgencyFees(uint256 _agencyFees) external onlyOwner`
Sets the agency fees percentage.

`mintProperty(uint256 _price) external payable`
Mints a new property by paying the required agency fees. The price of the property is set to _price and the caller becomes the owner.

`buyProperty(uint256 _id) external payable`
Buys a property by paying the required amount in Ether. The buyer becomes the new owner of the property.

`setIpfsHash(uint256 tokenId, uint256 subId, string memory hash) public onlyOwner`
Sets the IPFS hash for the specified property and sub-ID.

`tokenURI(uint256 tokenId, uint256 subId) public view returns (string memory)`
Returns the IPFS hash for the specified property and sub-ID. This represent the IPFS hash of the metadata to the NFT receipt

`withdrawRevenue(uint256 _amount) public`
Allows property owners to withdraw their revenue share.

`withdrawFees() external onlyOwner`
Allows the contract owner to withdraw the agency fees collected.


## Features V2
The V2 contarct has the following additional features:

* Buying Shares: Buyers can purchase shares of properties by paying the required amount in Ether.

* Selling Shares: Owners can sell their shares of properties to other users.

## Functions V2

Same as previously, with additional:

### Buying and Selling Shares

`buyShares(uint256 _id, uint256 _shares) external payable`
Buys a specified amount of shares of a property by paying the required amount in Ether. The buyer becomes the new owner of the shares.

`buySharesFrom(uint256 _id, uint256 _shares, address _seller) external payable`
Buys a specified amount of shares of a property from a seller by paying the required amount in Ether. The buyer becomes the new owner of the shares.

`setShareOwnerSelling(uint256 _id, uint256 _amount) public`
Sets the amount of shares that the caller is willing to sell for a specified property.



## Usage
### Remix
#### To use the contract in Remix:

Open Remix and create a new file named RealEstateAgency.sol.

Copy the contract code and paste it into RealEstateAgency.sol.

Compile the contract by selecting in the left sidebar, then selecting the contract file and clicking the Compile button.

![image](https://user-images.githubusercontent.com/61319421/228345016-5b84d2a8-dff7-4722-adf9-c8c8f85dd1a7.png)

Deploy the contract =in the left sidebar, then selecting the contract file and clicking the Deploy & Run Transactions button.

![image](https://user-images.githubusercontent.com/61319421/228345192-857eb1aa-08d4-44eb-bfa1-f7054a7b89d5.png)

##### Initialization
To initialize the contract:

Call the initialize function with the desired agency fees percentage.

![image](https://user-images.githubusercontent.com/61319421/228345302-5d185bd7-1f60-4a5c-8d71-e8a724697a7e.png)

By default 100 value correspond to 1%, so setting 50 will represent 0.5%. The reason is because there is no decimal in solidity.

Mint new properties by calling the mintProperty function with the desired price.
Buy properties by calling the buyProperty function with the desired ID and amount of Ether.


## Gas & Transaction Fees

### Contract Deployment

![image](https://user-images.githubusercontent.com/61319421/228852172-748a6d14-e35f-4d44-b528-230745c5dd04.png)


### Mint Property

![image](https://user-images.githubusercontent.com/61319421/228852246-864b55eb-d2b0-4e76-9d29-30618922d7a9.png)

### Buy Shares From Seller

![image](https://user-images.githubusercontent.com/61319421/228852370-e9c135af-88cd-4ee7-98fd-3f64e60e2dcf.png)


### Withdraw Revenues

![image](https://user-images.githubusercontent.com/61319421/228852415-caae4690-ea36-4b2a-b174-c7099c0aa628.png)


### Withdraw Fees

![image](https://user-images.githubusercontent.com/61319421/228852468-1f12889b-a192-4005-a49f-ae996293c5e1.png)


### Mint Property



