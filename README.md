# Smart Contracts, December 5th 2021 (Starting)

Smart contracts are the key element of Ethereum. In them any algorithm can be encoded. Smart contracts can carry arbitrary state and can perform any arbitrary computations. They are even able to call other smart contracts.

This gives the scripting facilities of Ethereum tremendous flexibility. Smart contracts are run by each node as part of the block creation process. Just like Bitcoin, block creation is the moment where transactions actually take place, in the sense that once a transaction takes place inside a block, global blockchain state is changed. Ordering affects state changes, and just like in Bitcoin, each node is free to choose the order of transactions inside a block.

## Witnesses

SLA agreements suffer from lacking a trustworthy platform for automatic enforcement. There's no real way you can write `policies` and enforce them, meaning more binary - we as some contracts have some ambiguity, and this is where things start getting expensive via lawyers, lawsuits, etc. Wouldn't it be great if we can prevent that from happening in the first place?  

The emerging blockchain technique brings in an immutable solution for tracking transactions among business partners. However, it is still very challenging to prove the credibility of possible violations in the SLA before recording them onto the blockchain. I feel like a witness model using GT (game theory) and the smart contract techniques could earnestly be a start. 

Witnesses gain revenue as an incentive for performing these duties, and the payoff function is carefully designed in a way that trustworthiness is guaranteed: in order to get the maximum profit, the witness has to always tell the truth.

In addition, an unbiased sortition algorithm is proposed to ensure the randomness of the independent witnesses selection from the decentralized witness pool, to avoid possible unfairness or collusion. An auditing mechanism is also introduced in the paper to detect potential irrational or malicious witnesses.

After hours of research, I found that **Efficient Distributed Sharding (EDS)** would be an innovative sharding scheme that makes shards sufficiently large and strongly bias-resistant via a combination of a client-server randomness scavenging mechanism and leader election via cryptographic sortition.

## Sortition Sample 

```sol
   function montanaSmartContract() public view {
        uint256 p;
        uint256 root;
        uint8 i;
        uint256 a;

        // a > p for small p
        for (i = 0; i < smallOddPrimes.length; i++) {
            p = smallOddPrimes[i];
            for (a = p + 1; a < p + 10; a++) {
                root = a.modSqrt(p);
                if (root != 0) {
                    require(
                        a % p == (root * root) % p,
                        "Invalid modular square root for a > p"
                    );
                }
            }
        }
    }
}
```

There's obviously still methods I can use that seem familiar from JavaScript, like `slice()`. 

## The Parallels of Witnesses and Radio Trunking 

Lately I've also been looking into [Radio Trunking](https://en.wikipedia.org/wiki/Trunking) and how that works. You'll see in this diagram, the parallels are certainly there:

<img width="607" alt="witnesses" src="https://user-images.githubusercontent.com/20936398/144744243-fbddac4d-fcaa-4939-ad71-f474144f9469.png">

## Practical Implementation 

The theory is, no pun intended here, is that using Game Theory, the witness then has to offer honest monitoring services in order to maximixe the end user's revenue. 

There needs to be a prototype system using smart contracts via Ethereum, if we are ever going to realize this witness model, and of course the SLA enforcement lifecycle.

## Things to work out 

* Violations Confirmation: (Violation Confirmation, is the the result of a strategy profile in a `N-witness game`, the service violation
is confirmed, only when `WReport` > || `M` where `1` `< N/2 < M < N, N, M`. Otherwise, it is treated as if there was no violation, in which case makes the witness method moot. 

<img width="530" alt="algo" src="https://user-images.githubusercontent.com/20936398/144744417-2c1804a6-2b2a-465e-95e6-3d54ab5b39c4.png">

## Truffle 

Using similar `git` methodology, I ran: 

```bash
truffle init
```

This initializes an empty Ethereum project in the current folder structured as:

```bash
├── app
│   ├── contracts/
│   │   ├── migrations/
│   ├── test/
│   ├── montanascripts/
│   ├── truffle-config.js
```
## Promise testing 

Some sample JS code I quickly wrote out: 

```javascript
const MontanaContract = artifacts.require("MontanaContract");
contract("Testing MontanaContract", accounts => {
    // test the constructor
    it("Should test the constructor", function() {});
});
```
When you call a smart contract function with Web3 you get as result a `JavaScript Promise object`:
* `const promise = contract.function_name(params);`

When a Promise is completed, we can use its result within the `then` statement:
* `promise.then( (result) => {// use your result here})`
