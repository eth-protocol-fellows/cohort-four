## Motivation
(What problem is your project is solving? Why is it important and what area of the protocol will be affected?)
### My Goal
My goal for EFP is to deepen my understanding on Ethereum and explore how to improve its privacy protection with cryptographic techniques. In my previous experience, I participated into many large-scale transactional system designs. Most of them have public transactions for verification and auditing purpose, but also have private transactions to protect the privacy of senders and receivers (in a regualated way). There is no doubt that as Ethereum becoming to a world computer, there are many use cases requiring privacy protection on transactions. I think this is a must-have (glad to see Valtalik has the same vision in his "Three Transition" blog). Then the question is how, especially as a forward compatible solution on top of the exisitng design of Ethereum. This is my major mission through EFP and I do believe it will be a great contribution to Ethereum Ecosystem.
### Success Metrics
- Identify and study the state of the art of privacy-preserving transaction mechnisims on Ethereum (Stealth Address and others) 
- Propose and implement an improvement of existing mechnisims
- Benchmark and study to what extends the improvement is
- Explore the integration with Ethereum systems

## Background
In the Ethereum ecosystem, privacy stands as one of the most significant and unresolved challenges. On a public blockchain like Ethereum, all information, including ENS names (Ethereum Name Service), POAPs (Proof of Attendance Protocol), NFTs (Non-Fungible Tokens), and transaction data, is inherently public. This transparency is a fundamental characteristic of public blockchains, enabling anyone to access and verify the data recorded on the blockchain. Thus, it highlights the importance of privacy-enhancing technologies and protocols to protect sensitive information and user identities in certain applications and use cases. 
One of the key solutions to privacy protection in Ethereum is to cut off the public association of the receipt's address. The Stealth Address (SA) prevents the public association of a blockchain transaction with the recipient's wallet address. SA effectively conceals the actual destination address of the transaction. It is critical to protect the privacy of recipients and cut off social engineering attacks on transaction flow. 
Based on our knowledge, all research did not resolve to meet overall requirements on 
- protect privacy on Ethereum,
- prevent quantum computing attacks, 
- reuse SA rather than creating many.

## Project description
(What is your proposed solution?)

Based on Dual Key Stealth Address Protocol (DKSAP), we contribute further to propose FHE-DKSAP: a SA protocol with Fully Homomorphic Encryption (FHE). FHE-DKSAP has the following primary advantages:
- FHE-DKSAP replaces EC with FHE to improve security level. FHE constructs the lattice cryptographic, and born to equip FHE-DKSAP to prevent quantum computing attacks. 
- Therefore, SA in FHE-DKSAP is secured to be reused and there is no need to generate large amounts of SA to reduce the complexity and difficulty of SA adoption.
- Compared to the dual-key design in EIP-5564, our design in FHE-DKSAP, can help the receiver outsource the computation of checking the entire chain for SA containing assets without revealing his view key.


## Specification
(How will you implement your solutions? Give details and more technical information on the project.)

### Thetoratical proposal 
We resolve challenges by adopting FHE into DKSAP, and name our new design as FHE-DKSAP. The overview can be found in the following figure. 
This content is only supported in a Lark Docs
We present FHE-DKSAP with details as below:
1. Bob (receiver) creates two key pairs: $(sk_2, PK_2)$ and $(sk_b, PK_b)$. 
- $sk_2$ is a randomly generated Ethereum wallet private key for SA spending purpose. It does not need to register on Ethereum before use and is not Bob's wallet private key.
- A SA spending wallet address public key $PK_2$ is generated using $sk_2$. It follows standard Ethereum address conversion from  $sk_2$ to $PK_2$. As said, the final wallet address by $PK_2$ does not need to register on Ethereum before use.
- $sk_b$ is the FHE private key for SA encryption and decryption. 
- $PK_b$ is used to encrypt the value of $sk_2$ to get the ciphertext $C_2$. Because FHE prevents quantum computing attacks, it is safe to encrypt $sk_2$ into $C_2$.
- Bob publicly shares $PK_2$, $PK_b$, and the ciphertext $C_2$.
2. Alice (sender) generates a key pair $(sk_1, PK_1)$ randomly for each SA transaction. 
- $sk_1$ is Ethereum ephemeral and the public key or wallet address does not need to register on Ethereum before use.
- She combines the two public keys for Ethereum wallet generation, $PK_1$ and $PK_b$, to obtain $PK_z$. 
- The Stealth Address (SA) is generated based on $PK_z$ by following standard Ethereum address conversion.
- Alice encrypts the secret key $sk_1$ using Bob's FHE public key $PK_b$, resulting in the ciphertext $C_1$. Alice then broadcasts C1, so that Bob is able to get it in an untrackable manner.
- Alice can not know SA's private key, as nobody can guess private key from public key $PK_z$. It means Alice only knows where to send SA transactions, but never be able to login to this SA wallet. 
3. Bob receives the ciphertext $C_1$ and adds two ciphertexts ($C_1$, $C_2$) together to get the $C$. 
- With the additive homomorphism, he can decrypt the ciphertext $C$ with his FHE private key $sk_b$. The FHE decryption result is the private key $sk_z$ to the wallet that receives the sent from Alice. 
- Then, he can generate the stealth address with $sk_z$ and decrypt it with the private key, which only bob owns.So Bob is capable of transferring its balance with the private key $sk_z$ for SA wallet .

### Practical Implementation 
(will link to a github)

The standardization of non-interactive stealth address generation presents the potential to significantly improve the privacy capabilities of the Ethereum network and other EVM-compatible chains by allowing recipients to remain private when receiving assets. By offering a foundational implementation with multiple cryptographic schemes, recipients are granted to receive the transaction in FHE full privacy way. 
1. Initial Implementation of SECP256k1

The SECP256k1 elliptic curve is defined with the equation y^2 = x^3 + 7 (mod p) over the finite field Z(2)(256)(-2)(32)(-977), which means the X and Y coordinates are 256-bit integers modulo a large number. 
Now let us understand the parameters settings: 

- Generator point G: The set formed by the product of P is also a group, called a cyclic subgroup, and P is called the generator or base point of the cyclic subgroup.
- Order n: The number of elements in a cyclic subgroup is called the order of the subgroup. 

The following reference is divided into three sections:
- Public key and secret key generations: 
- ECDH algorithm
- Stealth private key derivation

Public key and secret key generations:

PK_scan = G * sk_scan, PK_spend = G * sk_spend, R = G * s 

All the private keys only have one part, and the G contains (x,y) . Thus, all the public keys are with (x,y) two parts.

The output is similar like this:

Alice’s private key: 0xe32868331fa8ef0138de0de85478346aec5e3912b6029ae71691c384237a3eeb

Alice’s public key: (0x86b1aa5120f079594348c67647679e7ac4c365b2c01330db782b0ba611c1d677, 0x5f4376a23eed633657a90f385ba21068ed7e29859a7fab09e953cc5b3e89beba)

- ECDH algorithm: ss = r * PK_scan = R * sk_scan

sk_scan and r are secret keys with only one part. R and PK_scan are public keys with two parts, thus the shared secret key is two parts as well. For example: 
Shared secret: (0x3e2ffbc3aa8a2836c1689e55cd169ba638b58a3a18803fcf7de153525b28c3cd, 0x43ca148c92af58ebdb525542488a4fe6397809200fe8c61b41a105449507083)

- Key blinding algorithm:

public key of the address: S_sa = h(ss) * G + P_spend

h(ss) uses keccak-256 and the output is 256 bits as well as our private key. Private key, only bob has: s_sa = p_spend + H(ss) (1 part) 
Both the p_send and H(ss) are 256 bits, thus the whole private key is 256 bits. 
s_sa can decrypt the S_sa for the following reason:

S_sa = s_sa * G (according to EC key generation policy)
h(ss) * G + P_spend = h(ss) * G + p_spend G = (h(ss) +p_spend)  G 

2. FHE-DKSAP with Paillier
To use Paillier, we should use the library: from the import paillier and after that, the key processes include three steps:
- Bob secret key generation and encryption
- Alice secret key generation and encryption
- Bob's final key recovery and stealth address generation

Managing new types of key pairs, such as those introduced by FHE-DKSAP with Paillier, presents a significant consideration for wallet implementations. In the FHE-DKSAP scheme, storing the secret key of FHE directly within eth wallet is not a feasible approach. To establish a suitable storage solution, it becomes imperative to place this private key in a public domain, such as on blockchain. When necessitated, the FHE private key can then be decrypted using the wallet's secret key. Conversely, the public key of FHE, just like the public key of other common EOA, can be directly imported into eth wallet.

## Roadmap
(What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them.)
- Finalize the proposal of the project (Done)
- Publish the early study to Ethereum research (Done)
- Implement the proposal (ing)
- Complete the benchmark (ing)
- Finalize the research proposal with benchmark evaluation
- Revise/propose EIP
- Implement use cases

## Possible challenges
(What are the limitations and issues you may need to overcome?)

The communication cost, computation cost and the complexity of implementing fully homomorphic encryption. Meanwhile, most FHE schemes can only support 64 bites. However, our stealth address is 256 bits. The problem lies in how to extend the length for FHE.

## Goal of the project
(What does success look like? Describe the end goal of the project, scope, state and impact for the project to be considered finished and successful.)

- It protects privacy of stealth addresses by computing over ciphertext. 
- Compared to DKSAP and BasedSAP, our design removes the risk of leakages on keys and personal information. 
- Meanwhile, it can prevent quantum computing attacks as well.
  
## Collaborators

## Fellows
(Are there any fellows working with you on this project?)
@Mason-Mind

## Mentors
(Which mentors are helping you with the project?)

@nerolation

## Resources
(Provide links to repositories, PRs and other resources which constitute the project.)

1. An incomplete guide to stealth addresses https://vitalik.ca/general/2023/01/20/stealth.html
