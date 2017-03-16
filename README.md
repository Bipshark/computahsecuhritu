# Plugglapp, jajamensan

##  Security attributes
There are __PROTECTIVE__ attributes and __BEHAVIOURAL__ attributes.

__Protective__ are the attributes that influence security before a threat has reached the system.

__Behavioural__ are the attributes that play their part if some threat has reached the system.

### Most Important (CIA)
* __Confidentiality:__ Prevent disclosure of information to unauthorized parties. Behavioural 
* __Integrity:__ Absence of improper system alteration : Preventing unauthorized modification. Protective
* __Availability:__ Readiness for correct service to authorized users. Behavioural

### Others
* __Possession/Control:__ Authorized possession/control.
* __Authenticity:__ That the author of something really is that author.
* __Utility:__ Usefulness. Example: Encrypting data and losing the decryption key. The data fulfills all of the above but is not useful!
* __Safety:__ Absence of catastrophic consequences on the user(s) and the environment.
* __Accessibility:__ How difficult the system is to access. (Example: GPG is hard to use, SSL is not)
* __Maintainability:__ Ability for a process to undergo modifications and repairs.
* __Reliability:__ Continuity of correct service. Behavioural

Trick to remember: P A U S A M R C I A - Pausa Mister CIA

![](http://dl.dropboxusercontent.com/u/2548996/Screenshots/Screen%20Shot%202016-03-14%20at%2020.09.16.png)

![screenshot from 2016-03-16 13 55 47](https://butt.githubusercontent.com/assets/6649265/13812913/ef367b6c-eb7e-11e5-9671-05d7c6c1fd94.png)

##  Protection mechanisms
Passive Attack: Eavesdropping

Active Attack: Modify/Fake Data


* __THREAT REDUCTION:__ Legal protection, security check-ups, education
* __BOUNDARY PROTECTION:__ Shield cables, encryption, locks, access control
* __RECOVERY:__ Antivirus, supervision, intrusion detection, encryption of stored data


## Authentication procedure

1. __Identification__ of the user (who is it?)
2. Provision of some kind of __authentication information__, which is secret and unforgeable.
3. __Transmission__ of the authentication information to the system through a secure channel.
4. __Validation__ of the authentication information with some reference information (proof of correctness).

Usually, the transmission channel is the weakest link. 

The authentication information can be of __3 different, generic types__, based on something that is unique for the user:

* Something you __KNOW__ (e.g password, PIN code)
* Something you __HAVE__ (e.g smartcard)
* Something you __ARE (DO)__ (e.g fingerprint), (biometrical methods, something characteristic about you)
* (__WHERE__ you are can also be used in some situations)

In general, something that you have is called a _token_. i.e. something that is used for authentication.

A __capability__ is an unforgeable token that gives the possessor certain _rights_ (to an object) - __authorization__

## Ethics

#### Consequence-based theory
The __teleological theory__ of ethics focuses on the _consequences of actions_. Choose the action (among some set) that will result in the __greatest good and the least harm__.

There are two forms of teleology
* Egoism – relates to the person taking the action
* Utilitarianism – relates to everybody, the whole "universe"

#### Rule-based theory
The __deontology theory__ is founded in a _sense of duty_. Certain things are inherently good, i.e. good (or bad) in
themselves, e.g. truth, justice, freedom, peace, etc.

There is a special form of deontology, __rule-deontology__ that believes that there are a set of __universal, self-evident rules__ that should specify our proper conduct

## Kerberos

* Ticket - a token used by the user, so that his identity can be securely transferred to the server. It contains the necessary information needed for the user and server to be able to communicate (e.g. crypto keys). ONe ticket for each service is generated, often valid for hours.
* Authenticator - a one-time token showing that the user the user has the permission to use a service (one ticker per session, short lifetime ~5 min, to prove user´s identity)
* Session key - a temporaty key for the commmunication between the user and the service 
* Life time - the lifetime of a ticket
* Time stamp - the time when the ticket was created
* Nonce - a random number, to prevent replay attacks

**T**ime **O**f **C**heck to **T**ime **O**f **U**se

Class of software bug caused by changes in a system between the __checking__ of a condition (such as a security credential) and the __use__ of the results of that check. This is one example of a __race condition__. For example, checking if a file is a valid file and then using the file. Between the check and the usage some attacker can switch out/modify the file, actually making it invalid, but it will still be used.

## Clark-Wilson model
Ensures integrity

#### 2 Central Principles
* Well-formed transactions: users manipulate data only in constrained ways. Only legitimate accesses are allowed.
* Separation of duty: the system associates with each user a valid set of programs they can run and prevents unauthorized modifications, thus preserving integrity and consistency with the real world. (Introduced by Lee, Nash & Poland)

#### Principal Components
* __Constrained Data Items (CDI)__ Objects that are subject to strict integrity controls
* __Unconstrained Data Items (UDI)__ Unchecked data items
* __Integrity Verification Procedures (IVPs)__ Assures that all CDIs conform to some application-specific model of integrity & consistency.
* __Transformation Procedures (TPs)__ System transactions that change the set of CDIs from one state to another.
* Enforces integrity by means of **certification-** & **enforcement-rules** on TPs
* Authentication: identity of all users must be properly authenticated.
* Audit: modifications should be logged to record every program executed and by whom, in a way that cannot be subverted.


## Chinese Wall policy
Prevent flow of information between companies that may have conflicting interests, eg. competing.

* __Subjects__ : Entities that may wish to access information
* __Information__: Corporate information, three levels:
 1. Objects: Individual items of information
 2. Datasets: All objects that concern the same corporation
 3. Conflict of Interest: All datasets whose corporation are in competition

#### Access Rules:
__Simple Security Rule:__ A subject S can only read object O if:
* O is in the same DS as an object already accessed by S, or
* O belongs to a CI which S has not yet accessed

__*-property rule:__ A subject S can only modify object O if:
* S can read O according to the Simple Security Rule and,
* All objects that S can read are in the same DS as O


## Bell-Lapadula

#### Security levels
A security level is a (c, s) pair:
* c = classification – E.g., unclassified, secret, top secret
* s = category-set – E.g., Nuclear, Crypto
* (c1, s1) dominates (c2, s2) `iff c1 ≥ c2 and s2 ⊆ s1`
* L1 dominates L2 sometimes written L1 ⊒ L2 or L2 ⊑ L1

#### Security properties
The simple security or ss-property:
* For any (S, O, A) ∈ b, if A includes observation, then level(S) must dominate level(O)
* E.g., an unclassified user cannot read a top-secret document

The star security or *-property:
* If a subject can observe O1 and modify O2, then level(O2) dominates level(O1)
* E.g., cannot copy top secret file into secret file
* More precisely, given (S, O, A) ∈ b:

  * if A = r then current-level(S) ⊒ level(O) (“no read up”)
  * if A = a then current-level(S) ⊑ level(O) (“no write down”)
  * if A = w then current-level(S) = level (O)

![](http://dl.dropboxusercontent.com/u/2548996/Screenshots/Screen%20Shot%202016-03-14%20at%2014.51.55.png)

## Salami-attack

In information security, a salami attack is a series of minor attacks that together results in a larger attack.

## Morris worm

1. rsh attack
2. fingerd attack
3. sendmail debug attack

## Common Criteria

#### Protection Profile (PP)
* An implementation independent description of security objectives and requirements for a category of products
* "Describes what is needed/demanded!"
* Constitutes a security objective
* Usually created by a customer, interest group, authority etc.
* Normally certified

#### Security Target (ST)
* A implementation dependent description of a product or a system
* Includes the security objectives which are fulfilled by the product/system
* Which threats the product/system meet
* Also includes a description of the roles, policies, assumptions for the environment etc. that are assumed
* "Describes what is offered!"
* Is usually the answer of the developer to one/more PPs
* Must be produced for a evaluation of a product

#### Target Of Evaluation (TOE)
* The product / system to be evaluated, or the part of the product / system to be evaluated
* Defined in the Security Target
* Physical and logical boundaries / interfaces to the environment should be specified
* Can be difficult to define, especially for systems!

#### Assurance requirements
* Describes
  * What the developer shall do
  * What shall be proven and presented
  * What the evaluator shall verify/inspect
* Are divided into seven Evaluation Assurance Levels
  * EAL1 – Functionally tested
  * EAL2 – Structurally tested
  * EAL3 – Methodically tested and checked
  * EAL4 – Methodically designed, tested, and reviewed
  * EAL5 – Semiformally designed and tested
  * EAL6 – Semiformally verified design and tested
  * EAL7 – Formally verified design and tested
* Are divided into six assurance classes

![](http://dl.dropboxusercontent.com/u/2548996/Screenshots/Screen%20Shot%202016-03-14%20at%2016.24.46.png)

## Special file permissions
* setuid - changes the effective user id of the user to the owner of the program
  * `chmod u+s f1`
  * `chmod 4744 f1`
* setgid - changes the effective group id of the user to the group of the program
  * `chmod g+s f1`
  * `chmod 2744 f1`
* sticky bit - ensures the deletion of files by only file owner in a public writable directory
  * `chmod +t f1`
  * `chmod 1744 f1`

## Cryptography

#### Diffie–Hellman key exchange (D–H)

Uses a trapdoor function. Meaning that it's easy to calculate one way but hard/impossible to go the other way.
f(x) = A^x mod p : it's easy to calculate f(x) given the other variables, but it's hard to calculate x given the other variables.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Diffie-Hellman_Key_Exchange.svg/500px-Diffie-Hellman_Key_Exchange.svg.png)

## Unix

#### Passwords
Stored in /etc/shadow - Only root has access

![](https://butt.githubusercontent.com/assets/6649265/13758028/894d5a58-ea27-11e5-8db5-7c3f05234de4.PNG)

## Insiders

* The ordinary user
* The former user
* Maintenance personnel (system administrator, etc)
* The designer (backdoors, trojan horses)

#### Threats

## Side channel attack
Side-channel attack is any attack based on information gained from the physical implementation of a cryptosystem.

* Timing information
* Power consumption
* Electromagnetic leaks 
* Sound

## Metrics

### Scales
* Nominal
* Ordinal
* Interval
* Ratio
* Absolute

#### Security Metrication Basics - Example "System Security"
1. Define the concept => System Security
2. Define suitable attribute for metrication => The effort expended to make breaches
3. Select method for assessing the magnitude of this attribute => Based on controlled intrusion experiments
4. Select a method for how to do this assessment in a practical way => Use students & log activities

#### General Methods for ”measuring” security
* Evaluation/Certification (according to some standard): classification of the system in classes based on design characteristics and security mechanisms. “The ‘better’ the design is, the more secure the system”
* Risk analysis: estimation of the probability for specific intrusions and their consequences and costs. Trade-off towards the corresponding costs for protection.
* Penetration tests:
Finding vulnerabilities by using “Tiger teams”. (But you never find them all….)
* Vulnerability assessment: includes methods for finding system vulnerabilities
* Effort-based approach (based on “simulated” attacks): a statistical metric of system security based on the effort it takes to make an intrusion. “The harder to make an intrusion, the more secure the system”
* Weakest adversary: which is the weakest adversary that can compromise the system?
* MTTC (Mean Time To Compromise): calculates the statistical mean time to an intrusion

#### Special Cases for measuring security
* Cryptographic Strength: the effectiveness of cryptos
* Privacy measures: extent that the system will leak information


## Risk Treatment Alternatives
* Risk acceptance
* Risk avoidance
* Risk transferal
* Reduce consequence
* Reduce likelihood

## OS Security

#### Layers of a computer system
1. Applications
2. Services
3. Operating System
4. OS Kernel
5. Hardware

- The security of a layer could be compromised by attacks from lower levels.

#### The basis of OS protection is separation. The separation can be of four different kinds:
* Physical: physical objects, such as CPU’s, printers, etc.
* Temporal: execution at different times
* Logical: domains, each user gets the impression that she is ”alone” in the system
* Cryptographic: hiding data, so that other users cannot understand them

#### Trusted OS Concepts
* Kernel - Performs the lowest level functions
* Security Kernel - Enforces the security mechanisms of the entire OS
* Reference Monitor (RM) - Part of the Security Kernel that controls access to objects
* Trusted Computing Base (TCB) - Is everything in the OS necessary to enforce the security policy

## Nice links
http://www.slideshare.net/aouyang/2-security-architecturedesign-11860029
