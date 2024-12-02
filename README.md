# Reimagine-Truth-NFT-SAMPLE-1

# Reimagine-Truth-NFT-SAMPLE public

Sample NFT Contract (ERC-721)
solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract TruthSeekersNFT is ERC721URIStorage, Ownable {
    uint256 public tokenCounter;
    string public baseURI;

    constructor(string memory _baseURI) ERC721("Truth Seekers Deck", "TSD") {
        tokenCounter = 0;
        baseURI = _baseURI;
    }

    function createNFT(address to, string memory tokenURI) public onlyOwner {
        uint256 tokenId = tokenCounter;
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, tokenURI);
        tokenCounter = tokenCounter + 1;
    }

    function _baseURI() internal view virtual override returns (string memory) {
        return baseURI;
    }
}
Example NFT Metadata (JSON)
This metadata file is stored as a JSON object on IPFS or a decentralized storage platform like Arweave and includes various properties for the NFT.

json
Copy code
{
  "name": "Truth Seeker #1",
  "description": "A unique NFT from the Truth Seekers Deck collection. Embark on a journey of knowledge, freedom, and enlightenment.",
  "image": "https://ipfs.io/ipfs/QmExampleHash", 
  "attributes": [
    {
      "trait_type": "Rarity",
      "value": "Legendary"
    },
    {
      "trait_type": "Power",
      "value": "50"
    },
    {
      "trait_type": "Color",
      "value": "Blue"
    },
    {
      "trait_type": "Special Ability",
      "value": "Reimagine Truth"
    }
  ]
}
Explanation of Components:
Smart Contract:

TruthSeekersNFT: An ERC-721 contract for minting NFTs with unique IDs.
createNFT(): A function that allows the contract owner to mint NFTs with unique metadata.
baseURI(): The base URI for the metadata associated with the NFTs.
Metadata:

The metadata is a JSON object that includes important properties such as the name, description, and image URL of the NFT.
You can store images on IPFS and link them in the metadata file to ensure decentralized storage.
The attributes field allows you to assign different characteristics like "Rarity," "Power," and other traits to the NFTs.
Sample NFT Image
For the NFT image (referred to in the metadata as https://ipfs.io/ipfs/QmExampleHash), you would need to upload an image (like a digital artwork, animation, or 3D model) to IPFS or a similar decentralized storage platform. The URL in the metadata would link to this image, ensuring it's permanently available in the decentralized web.
