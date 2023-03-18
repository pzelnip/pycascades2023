# Pycascades 2023

## Kickoff

First hybrid version

-----

## Python Syntactic Sugar

<https://2023.pycascades.com/program/talks/pythons-syntactic-sugar/>

Brett Cannon

What is Syntactic Sugar?

Distill down what are the fundamental bits of Python

List comp with locals)()

11 pieces you can't live without

1. Integers
2. function calls
3. while
4. try/except
   1. all other parts are optional (ex else, finally)
5. def
6. return
7. yield
8. Assignment
9. global
10. nonlocal
11. del

"A Turing machine with Python flourishes"

Simple unraveling

83 pieces of syntax to get rid of, 4 examples to give a flavour

Attribute acccess (x.y)

language spec can make things interesting, decorator example

Special (magic, dunder) methods, negate example

Binary operators

<https://snarky.ca/tag/syntactic-sugar/>

--

## Implementing Distributed Tracing

<https://2023.pycascades.com/program/talks/implementing-distributed-tracing/>

Zach Lipp

<https://lippingoff.netlify.app/talks/pycascades_2023>

traces vs spans, traces are made up of spans, tags/attributes record info about spans, no schemas

opentelemetry client (used to be opentracing)

have to manually propagate headers

Pros/cons slide is great

--

## Security Best Practices for Django Applications

<https://2023.pycascades.com/program/talks/security-best-practices-for-django-applications/>

Gajendra Deshpande

<https://observatory.mozilla.org/>

DJ Checkup

A01 Broken access control (injection, etc)

discussion of best practices (invalidating sessions, making jwt's short lived, etc)

<https://pypi.org/project/django-user-management/>

A02 cyrptographic failures

stealing keeys, mitm attacks, etc
TLS failures
poor db hashes

SSL/TLS Settings or Django (some good settings, didn't catch them all)

<https://pypi.org/project/django-encrypted-model-fields/>

A03 Injections

SQL Injection

A04 Insecure Design

New category for 2021

A secure design can have implemention, defects, an insecure design can cannot be fixed by perfect implementation

A05 Security Misconfigurations


Dude is going way too fast, too much info too little time to absorb

<https://shadowd.zecure.org/overview/introduction/>

A06 Vulnerable and outdated components

A09 security logging and monitoring failures

A10 Server side request forgery (SSRF)

A11 Beyond OWASP Top 10

Security Features in Django (see djanog docs)

djangohunter (find on github)
pygoat ([herokuapp](http://pygoat.herokuapp.com/) ?)

--

## Why "Hello World" is a Massive Operation - From Python code to Stack Virtual Machine

Richard Rowland

<https://2023.pycascades.com/program/talks/why-hello-world-is-a-massive-operation-from-python-code-to-stack-virtual-machine/>

Walk through the architecture of Cpython, walking through byecode generation, etc

```shell
python -m tokenize hello.py
```

<https://docs.python.org/3/library/tokenize.html?highlight=tokenize#module-tokenize>

```shell
python -m ast hello.py
```

Crafting Interpreters book Nystrom, Robert


```shell
python -m py_compile hello.py
```

devguilde.python.org/internals

inside the python virtual machine book obi ike-nwosu
cpython internals Annthony Shaw

--

## Tightening Your Feedback Loop with Live Coding

Don Kirkby

<https://2023.pycascades.com/program/talks/tightening-your-feedback-loop-with-live-coding/>

Fun turtle graphics example of iterative development

<https://gist.github.com/donkirkby>

Live coding = running as you type/instant feedback

Neat example of matplotlib teaching tool in browser

Visual testing

Folk dancing visualizing sorting algorithms
<https://www.youtube.com/watch?v=lyZQPjUT5B4>

Example of using it for

--

## SBOMs Are Coming. How will Python help?

Anthony Harrison

Pre-recorded talk

SBOMs = Software Bill Of Materials

We no longer undersand how our software is constructed or works
Iceberg analogy

SBOM - formal set of machine readable metadata describing your software application
SBOMs are designed to be shared within and across organizations
Important part ofa  software risk strategy

OpenSSF SBOM
Timeline slide, really accentuates how fast this is developing (log4j was only 1.5 years ago)

TWo standards and formats:

* <https://spdx.org>
* <https://cylconedx.org>

SBOMs used throughout the software lifecycle

Tooling

* sbom4files
* sbom4python
* distro2sbom

Discussion of shorcomings of the tools.

Not entirely clear how SBOMs are used

Challenges with consistency in package metadata (license example)

SBOM mgmt tools:

* sbom-manager
* sbomdiff
* sbomaudit

Typical Use cases

* does my project use version x of component y
* others...

SBOM Governance

* cve-bin-tool
* sbom2doc

CTA to improve the data used for SBOMs

<https://github.com/anthonyharrison>

--

## Eternal Sunshine of the Spotless Development Environment

Sarah Kaiser

<https://2023.pycascades.com/program/talks/eternal-sunshine-of-the-spotless-development-environment/>

Nearal networks for babies
ABC of Engineering
Robotics for Babies

books

Love letters to be remembered

Dev containers

<https://containers.dev>

Remote ddev extension, can pick from templates

Example use case of using devcontainer.json for reproducing a bug

Example use case of education (helping with setup in teaching envs)

Case study with numpy

<https://aka.ms/pycascades_devcontainers>

--

## Metaprogramming in Python using Metaclasses

Adarsh Divakaran & Aby M Joseph

<https://2023.pycascades.com/program/talks/metaprogramming-in-python-using-metaclasses/>

"Code that can modify code"

metaprogramming for classes is called metaclasses

decorator examples

* method decorators
* class decorators
  * singleton example

Descriptors

* readonly attribute example

Dunder methods

Class Creation Steps in Python

"type is the default metaclass in Python"

* type(obj)
* type(name, bases, attrs)

2nd is useful for creating classes dynamically :mindblown:

since classes are just objects, metaclasses are the way to customize their creation
the base metaclass is type
type's type is type

A metaclass is a class whose instance is another class.

Steps to write a metaclass

1. write a subclass of type
2. insert hw new metaclass into the class creation process


Modify class heirarchies - use metaclasses

Proposals for new things to avoid metclasses

`__init_subclass__` - called when a subclass is created

ABC as an example of metclasses
Enums as an example of metaclasses
Django models as an example of metclasses (Model uses ModelBase as it's metaclass)

--

## Demystifying SQLite with Python

Ria Bhatia

<https://2023.pycascades.com/program/talks/demystifying-sqlite-with-python/>

Pre-recorded talk

Uses of SQLite
INtroductory SQLite talk

Some high level details of the sqlite file structure

SQL command types

* DDL
* DQL
* DML
* DCL

Some slides of using the built-in sqlite3 module.

Some discussion of querying mechanics, how indexes can help.

--

## Practicality Beats Purity: The Zen of Python’s Escape Hatch?

Christopher Neugebauer

<https://2023.pycascades.com/program/talks/practicality-beats-purity-the-zen-of-pythons-escape-hatch/>

Discussion of zen of python

"Not prescriptive and a terrible way to settle arguments"

Decorators as an example that's contradictory to Zen of Python (explicit is better than implicit)

type hints as example of contradicting the "Simple is better than complex"

Python is not prescriptive, it is opinionated

One use cas'es simplicity is anothyer use case's complexity

chrisjrn.com




















------------

Udemy python deep dive course
