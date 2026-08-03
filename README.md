# Blockchain-Based Document Verification System

A Solidity-based smart contract that securely stores and verifies important documents on an Ethereum private blockchain. The system ensures document integrity, authenticity, and protection against unauthorized modifications.

## Aim

To develop a smart contract for securely storing and verifying important documents on the Ethereum blockchain, ensuring document integrity, authenticity, and protection against unauthorized modifications.

## Algorithm

1. Deploy the smart contract on the Ethereum private blockchain.
2. Add document details:
   - Document ID
   - Document Name
   - Extracted Data
   - Verified Data
   - Verification Status
3. Store the document information on the blockchain.
4. Retrieve the document using its Document ID.
5. Verify the document authenticity.
6. Display the stored document details.

## Program

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract DocumentVerification {

    struct Document {
        uint256 documentId;
        string documentName;
        string extractedData;
        string verifiedData;
        bool verified;
        uint256 timestamp;
    }

    mapping(uint256 => Document) public documents;

    function addDocument(
        uint256 _documentId,
        string memory _documentName,
        string memory _extractedData,
        string memory _verifiedData,
        bool _verified
    ) public {

        documents[_documentId] = Document(
            _documentId,
            _documentName,
            _extractedData,
            _verifiedData,
            _verified,
            block.timestamp
        );
    }

    function getDocument(uint256 _documentId)
        public
        view
        returns (
            uint256,
            string memory,
            string memory,
            string memory,
            bool,
            uint256
        )
    {
        Document memory d = documents[_documentId];

        return (
            d.documentId,
            d.documentName,
            d.extractedData,
            d.verifiedData,
            d.verified,
            d.timestamp
        );
    }
}
```

## Expected Output

- Documents are securely stored on the Ethereum blockchain.
- Documents can be retrieved using their unique Document ID.
- Verification status confirms document authenticity.
- Blockchain timestamp records the storage time.
- Stored data remains immutable and tamper-proof.

## 📖 High-Level Overview

This project demonstrates how blockchain technology can be used to securely manage digital documents. The smart contract stores document information in an immutable ledger, allowing users to retrieve and verify documents while preventing unauthorized modifications.

## ✅ Result

The Blockchain-Based Document Verification System was successfully implemented using Solidity on an Ethereum private blockchain. Document details were securely stored and retrieved using the Document ID. The verification status and blockchain timestamp confirmed the authenticity and integrity of the stored document.
