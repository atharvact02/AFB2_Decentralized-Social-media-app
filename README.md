# IITISoC--AFB2_Decentralized-Social-media-app

___

## **Team** :

1. Aaditya Bindal (Team Leader)
2. Atharva Tayshete
3. Utkarsh Verma

## **Primary Mentor** : Ashwin Jino V

## **Secondary Mentor** : Nilay Ganvit
___
## **Project Overview** :

This is a decentralized twitter(named ‘Dwitter’) which has basic features of Twitter and UI resembling that of Tumblr. There is also an option to send tokens through the ‘tip’ feature <br /> 
The basic work of authentication is being done using metamask. The core of any dApp(decentralized app) is the smart contract which we write in language: Solidity and deploy it via Hardhat
```Solidity
    pragma solidity ^0.8.0;
    import "hardhat/console.sol";
   ….
```
We have used ERC721URIStorage, which allows us to use the mint functionality. It allows the storage for token URIs, which means that URIs are not stored on a chain. This makes storage efficient and makes the contract more gas-friendly. </br>
```Solidity
    contract Decentratwitter is ERC721URIStorage {
    uint256 public tokenCount;
    uint256 public postCount;
    …..
```   
The mint function function which basically mints NFT of the profile pic
```
    function mint(string memory _tokenURI) external …..
```
The code below can be said to be the core of the smart contract
```function uploadPost(string memory _postHash) external {
        // Check that the user owns an nft
        require(
            balanceOf(msg.sender) > 0,
            "Must own a decentratwitter nft to post"
        );
        // Make sure the post hash exists
        require(bytes(_postHash).length > 0, "Cannot pass an empty hash");
        // Increment post count
        postCount++;
        // Add post to the contract
        posts[postCount] = Post(postCount, _postHash, 0, payable(msg.sender));
        // Trigger an event
        emit PostCreated(postCount, _postHash, 0, payable(msg.sender));
    }
```
This function does the function of ‘tipping posts’.The logic written in 2nd line below restricts sending tip to yourself.</br>
```
    function tipPostOwner(uint256 _id) external payable { 
    require(_post.author != msg.sender, …..
```
This acts as the memory block of the website and extracts the posts from BlockChain  </br>
```Solidity
    function getAllPosts() external view returns (Post[] memory _posts) {......
```    
This function helps to put NFT as a profile picture if you already own a one on that wallet</br>
```Solidity
    function getMyNfts() external view returns (uint256[] memory _ids)....
```
___
## **Skills** : 
* HTML
* CSS
* ReactJS
* Solidity
___
## **Technologies used** :
* Remix
* Infura(IPFS)
* HardHat
* Metamask
* Ethereum Blockchain
* Node.js
* ERC721(For NFTs)
___
## **Preview** :
![0.css](/Changepfp_or_id.jpeg)
___
![1.css](/metamask.jpeg)
___
![2.css](/twoaccount.jpeg)
___
![3.css](/Console.jpeg)
___
![4.css](/Initialization.jpeg)
___

## **Download Links** : 
You can access our project from your local machine !
>https : https://github.com/atharvact02/AFB2_Decentralized-Social-media-app.git 

```bash
    git clone https://github.com/atharvact02/AFB2_Decentralized-Social-media-app.git
```
___
## **Setup** :
### 1. Clone/Download the Repository

### 2. Install Dependencies:
```
$ cd decentratwitter
$ npm install
```
### 3. Boot up local development blockchain
```
$ cd decentratwitter
$ npx hardhat node
```

### 4. Connect development blockchain accounts to Metamask
- Copy private key of the addresses and import to Metamask
- Connect your metamask to hardhat blockchain, network 127.0.0.1:8545.
- If you have not added hardhat to the list of networks on your metamask, open up a browser, click the fox icon, then click the top center dropdown button that lists all the available networks then click add networks. A form should pop up. For the "Network Name" field enter "Hardhat". For the "New RPC URL" field enter "http://127.0.0.1:8545". For the chain ID enter "31337". Then click save.  


### 5. Run deploy script to migrate smart contracts
`$ npx hardhat run scripts/deploy.js --network localhost`

### 6. Run Tests
`$ npx hardhat test`

### 7. Launch Frontend
`$ npm run start`
 
___
# Thank You for your time !

