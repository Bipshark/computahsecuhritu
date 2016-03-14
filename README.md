# Plugglapp, jajamensan

## Authentication procedure

1. __Identification__ of the user (who is it?)
2. __Provision__ of some kind of authentication information, which is secret and unforgeable.
3. __Transmission__ of the authentication information to the system through a secure channel.
4. __Validation__ of the authentication information with some reference information (proof of correctness).

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

**T**ime **O**f **C**heck to **T**ime **O**f **U**se

Class of software bug caused by changes in a system between the __checking__ of a condition (such as a security credential) and the __use__ of the results of that check. This is one example of a __race condition__.

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

#### Special file permissions
* setuid - changes the effective user id of the user to the owner of the program
  * chmod u+s f1
  * chmod 4744 f1
* setgid - changes the effective group id of the user to the group of the program
  * chmod g+s f1
  * chmod 2744 f1
* sticky bit - ensures the deletion of files by only file owner in a public writable directory
  * chmod +t f1
  * chmod 1744 f1
