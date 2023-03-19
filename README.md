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

--

## Day 2

## Lightning Talks

### Global domain names and email addresses are here!

no longer limited to latin script

Jim DeLaHunt

Indigenous languages

idna - does it wrong

Technical info <https://uasg.tech>

<https://universalacceptance.day>

<http://go.jdlh.com/pycascades2023>

### Git Reset

Wes Lord

<https://github.com/weslord/git-demos>
<https://git-man-page-generator.lokaltog.net/>

```shell
git log --online --graph --all

```

Merging branches
rebasing

### Do Everything with Pydantic

Sam Edwardes

github.com/SamEdwardes

Pydantic with SQL?

* sqlmodel example

### A Crash Course in Digital Accessibility

Tony Fast

wcag guidelines
wuh-cag guidelines

<https://tonyfast.github.io/tonyfast/xxiii/2023-03-18-pycascades-ally-talk.html>

### Pycon US 2023

Mariatta

Pycon US chair!

Online only option - $100USD

Pycon US Stories Slideshow

<https://bit.ly/3ZSG6t1>

### Yellowsto0ne Codera

Robin

<https://robinrh.github.io>

Puzzles for teaching Python

### Pooch A Friend to fetch your data files

Santiago Soler

<https://fatiando.org/pooch>

Download data files

Used by a bunch of the scientific libraries (scipy, etc)

### Lets Spice this up

Andres

August Python Conference in Latin America

Pycion Latam 2023

Mexico

<https://pylatam.org/en>


## Writing an I2C Sensor Driver

Colin Dietrich

<https://2023.pycascades.com/program/talks/writing-an-i2c-sensor-driver/>

I2C

Crash course in hardware

<https://github.com/crdietrich/meerkat>

--

## Cloud Infrastructure From Python Code: How Far Could We Go?

Asher Sterkin

<https://2023.pycascades.com/program/talks/cloud-infrastructure-from-python-code-how-far-could-we-go/>

Virtual presentation

Slides - <https://www.slideshare.net/AsherSterkin/pycascades23pdf>

is ifc same as iac?  No

CDKs - don't solve the core prooblem anew but rather wrap the same low level
abstractions in a programming language

Solution: Raise the level, bridge the gap

PyIFC - seems to be this idea of generating CDK type stuff from python code?

Example that took a python app, and seemed to produce a cloudformation template

caios

--

## Sharing is Caring - Sharing pytest Fixtures

Brian Okken

<https://2023.pycascades.com/program/talks/sharing-is-caring-sharing-pytest-fixtures/>

<https://pythontest.com/pycascades-2023>

Fixture crash course

Sharing via conftest.py

What about sharing between projects?

Make a pytest plugin

Walked through example using tox & flit.

What is pytester?

Private classifier for internal only projects, to avoid publishing to pypi

Nice practical example talk

--

## Untangle Python Spaghettis - Deep Dive Into Environments and Dependencies Management

Cheuk Ting Ho

<https://2023.pycascades.com/program/talks/untangle-python-spaghettis-deep-dive-into-environments-and-dependencies-management/>

<https://cheuk.dev>

Deep dive into environments and dependencies management

Why venvs?

* avoid conflicts
* preserve versions
* discard when not needed

Where are your packages stored?

How Python finds your packages?

* import statement
* searches for both python code and extension modules
* search along `sys.path`

Example creating a venv using `-m venv`

looking into the contents of a venv directory

```python
import sys
print(sys.path)
```

Discussion of how the scripts in bin modify sys.path

`pip list` to show all packages installed.  Look into `site-packages`

Conda

Data scientists are often different as they often use conda rather than pip &
such.  Lets look at what's different.

* comes with Anaconda
* environment manager that
* doubles as a package manager

Using Conda

* Similar mechanics but
* live by default in the envs folder of your conda directory
* independent from venv
* work on system level
* works with other languages as well

--

## Vulnerability Scanning For Free (as in Puppies)

Terri Oda

<https://2023.pycascades.com/program/talks/vulnerability-scanning-for-free-as-in-puppies/>








------------

Udemy python deep dive course
