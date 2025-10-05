
## Formal Methods


- the foundations, method, and tools for developing and reasoning about systems
- they allow us to rigorously and formally check whether a system satisfies defined security properties
- can also be used to identify vulnerabilities in systems
- can be applied to software or hardware (or a combination)


## A Recipe for Formal Methods

1. please specify:
	the system
	the adversarial environment in which the system operates
	the security properties that the system should satisfy

2. Choose a 'specification' language
3. verify the security properties



## 2: Defining the adversarial environment

- an adversary model defines a class of attackers in terms of their apabilities:
	- Are we protecting against a remote attacker or an attacker with physical access to devices
	- is the attacker capable of active attacks or passive attacks only?
	- can the attacker corrupt/control protocol participants?
- The adversary model must relate to real-world attacker capabilities


## 3: Defining the security properties


- system correctness
- safety properties
	- Ensuring that something "bad" doesnt happen during protocol execution
	- data integrity, for example
- Indistinguishably properties
	- an attacker cannot distinguish between two protocol runs
	- confidentiality, anonymity, for example


## Benefits and Limitations of Formal Methods

- Benefits:
	- Places system development on *firm mathematical grounding.*
	- addresses *Inadequacies in the "code, penetrate and patch* approach where systems do not necessarily meet their specification
- Limitations: 
	- Formal methods *verifies properties of models,* not the actual systems. if the model is not accurate, the results may not be accurate
	- Formal methods may not specify all system requirements, or may specify requirements incorrectly



## Formal Methods for Protocol Design

- there are three main methods that can be used to analyse protocol design:
	- Symbolic methods
	- stochastic methods
	- computational methods


## Symbolic Methods 

- **Possibilistic** security definitions
- Assumes the Dolev-Yao attack model: an active network adversary that can access and manipulate messages, but cryptography is assumed to work perfectly

## Computational Methods

- adversary is modelled as a probabilistic polynomial-time Turing machine
- several techniques for constructing security proofs
- detailed and accurate models, but formalisation and construction of proofs is more difficult than in the symbolic model
- example: CryptoVerif

