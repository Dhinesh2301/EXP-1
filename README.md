### Experiment 2: Decentralized Certificate Verification

```
Name : DHINESH R
Reg. No : 212223220019
```

## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
# Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
## Output
### Issue Certificate
<img width="432" height="796" alt="image" src="https://github.com/user-attachments/assets/ad3c6df0-dd1f-4738-9cb3-b392d0864728" />


### True
<img width="430" height="812" alt="image" src="https://github.com/user-attachments/assets/41e0949e-e5fe-40ec-9f7a-c528b51458cd" />



### False
<img width="438" height="757" alt="image" src="https://github.com/user-attachments/assets/544a4950-bf45-4d6c-abe2-231dd67444b8" />

# Result:
Smart contract for issuing and verifying certificate on Ethereum is successfully executed.
