# Smart Contracts, December 5th 2021 (Starting)

Smart contracts are the key element of Ethereum. In them any algorithm can be encoded. Smart contracts can carry arbitrary state and can perform any arbitrary computations. They are even able to call other smart contracts.

This gives the scripting facilities of Ethereum tremendous flexibility. Smart contracts are run by each node as part of the block creation process. Just like Bitcoin, block creation is the moment where transactions actually take place, in the sense that once a transaction takes place inside a block, global blockchain state is changed. Ordering affects state changes, and just like in Bitcoin, each node is free to choose the order of transactions inside a block.

## Witnesses

SLA agreements suffer from lacking a trustworthy platform for automatic enforcement. There's no real way you can write `policies` and enforce them, meaning more binary - we as some contracts have some ambiguity, and this is where things start getting expensive via lawyers, lawsuits, etc. Wouldn't it be great if we can prevent that from happening in the first place?  

The emerging blockchain technique brings in an immutable solution for tracking transactions among business partners. However, it is still very challenging to prove the credibility of possible violations in the SLA before recording them onto the blockchain. I feel like a witness model using GT (game theory) and the smart contract techniques could earnestly be a start. 

Witnesses gain revenue as an incentive for performing these duties, and the payoff function is carefully designed in a way that trustworthiness is guaranteed: in order to get the maximum profit, the witness has to always tell the truth.

In addition, an unbiased sortition algorithm is proposed to ensure the randomness of the independent witnesses selection from the decentralized witness pool, to avoid possible unfairness or collusion. An auditing mechanism is also introduced in the paper to detect potential irrational or malicious witnesses.
