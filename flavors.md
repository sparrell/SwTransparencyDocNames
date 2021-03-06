# Flavors of Software Transparency Artifacts

TL;DR
- can we agree that we can call something an SBOM if (iff?)
   + it is in one of SWID, SPDX, CycloneDx formats AND
   + has all the baseline elements, and nothing more than the baseline elements?
- what do we call something that many would call an SBOM but does not contain all the baseline elements?
- what do we call something that contain all the baseline elements but also contains some 'beyond baseline' elements?


“There are only two hard things in Computer Science:
cache invalidation and naming things.”

Attributed to Phil Karlton circa 1996

This writeup is my attempt at clarifying
the flavors of "stuff" under discussion
in the NTIA Software Transparency
Multistakeholder Working Group.
I am purposely not using the word "SBOM" yet
because it is clear to me that different stakeholders
have different assumptions on the which 'flavor' is meant by that term.
I will use Some-Word-Other-Than-SBOM (SWOTS) in place of SBOM
until we agreed on when to use SBOM,
when to use SBOM with particular qualifiers,
and what words to use for those artifacts we aren't calling SBOMs.
All the 'names' I've chosen are horrible and I hope
someone comes up with better words for each.
This document is to make the point we need to be able to distinguish
the 'flavors' - I don't really care what each flavor is called.

I deliberately used 'artifact' as a catch-all.
I will attempt to use 'writeup' to mean the text you are reading -
so as not to confuse with "documents" that are the artifacts we
are trying to describe.
I will attempt to avoid the use of the word document entirely,
since artifacts may be documents (english text, xml, etc)
but they may not be,
by at least some definitions of the word 'document'
(e.g. JSON data structures in a Machine-to-Machine protocol).
I will attempt to use 'component' to mean 'the thing that
we are being transparent about' and hopefully be able to
avoid whether it is 'mid-stream'
(i.e. downstream of its component parts
yet upstream of some component that used it)
or 'finished good'
(i.e has no downstream components of which it is a component).
I will attempt to use 'transparency artifact' to describe
the 'thingies' coming out of this work.
Yes it's awkward and somebody should come up with better wording.

I believe that we will talk past each other less
if we understand 'which flavor' is under discussion
and what use case it is being used in.

Flavor examples where clarification would be beneficial to
distinguish between:
- ingredients only
- component relationships
- assembly instructions
- component to license relationships
- known-unknowns / incomplete / "one-hop" / "complete"
- component to vulnerability relationships
- component "affected/not-affected" relationship to vulnerability
- has ingredients but not 'sufficient' for SBOM baseline as defined by framing
- has insufficient data for a particular use case (many examples which will need to be un-confounded)

I believe this is one source of our talking past each other,
and that having 'artifact names' will allow us
to better reach consensus on many other topics.

## First Principles
This is just Duncan's opinion.
Assume "IMHO" on every sentence.
Don't mistake passion for intransigence -
change my opinion by presenting alternatives
and reasoning - particularly with use cases/scenarios.
I recognize my experiences prejudice me
and I recognize
there are use cases
beyond the ones I have considered.
Everyone has to operate in their
own frame of reference.
Broaden my mind by alerting me
to your frame of reference.

This writeup has only two parties involved,
the producer of the transparency artifact,
and the consumer of the transparency artifact.
They may be the same
(i.e. transparency artifact is for internal consumption).
The component producer
(i.e. the thing the transparency artifact is about)
is a different role from
this writeup's perspective.
The transparency artifact producer may or may not be the
component producer.
This writeup allows for other-than-component-producer
creating relevant transparency artifacts.
"Authority" to produce a transparency artifact,
and 'trust' of that transparency artifact are out of scope for this writeup.

Everything in this writeup assumes
the transparency artifact producer
and the transparency artifact consumer
have a sufficient trust relationship
for the use cases.
How that is achieved is outside the scope of this writeup.

Everything in this writeup assumes
the transparency artifact producer
has sufficient data to produce the transparency artifact accurately.
Incompleteness is addressed;
but inaccuracy and integrity
are outside the scope of this writeup.

This writeup assumes parties in the use case,
and only the parties in the use case,
have access to the transparency artifact.
How confidentiality is achieved,
(and what level of confidentiality
is appropriate) is out-of-scope.

TL;DR confidentiality, integrity, availability are beyond scope of naming
which transparency artifacts we are talking about in this writeup -
albeit they will introduce more
flavors once they are addressed.

## Big Picture
In Allan's previous life, he championed vulnerability coordination
and FIRST has the following pic on it's website (
https://www.first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.1):

![Big Picture](./VulnMultipartyFigure-1.jpeg)

When necessary to define roles,
I will use the roles on this pic
except I will use producer and consumer instead of vendor and user.

## SBOM
I assume there is consensus that the artifact is an SBOM if it
- has the 'baseline'(as defined by the framing group) information, and
- is one of SWID/CycloneDx/SPDX formats, and
- has no 'beyond baseline' information

For lack of a better term, I am going to call this the
'ingredients-only baseline SBOM';
and it will be the only artifact I call an SBOM
since we apparently do not have consensus on whether
these other artifacts should be called SBOMs (maybe with some qualifier)
or we should have different names for some/all of them.

## Complete SBOM
A 'complete' (or full?) SBOM would contain all components,
including going upstream until all components had no further upstream components.
An SBOM that has 'known-unknowns'
(e.g. had a component that it was unknown whether it contained any upstream
components) would be an 'incomplete' SBOM.

## "less than baseline" SWOTS
There are transparency artifacts that do not contain enough information
to be considered SBOMs by the definition above.
For example some vendors list components without sufficient identification
to know the version.
- Should such artifacts be able to be called SBOMs?
- Or should they have a qualifier (eg 'not quite' SBOMs)?
- Or should then have a different name entirely.

## Component Relationship Artifacts
Consider two artifacts for the same compound component:
- artifact one contains the components and their relationships eg A includes B & C; B includes D; ...
- artifact two is a 'parts list' is artifact one minus all the relationships. Ie it is a 'parts list' without the 'assembly diagram' eg A,B,C,D,...

Both could be argued to be compliant with baseline framing definition of an SBOM.
Should they have different names?

## Artifacts created by post-processing of SBOMs
I am a proponent of the IACD (Integrated Adaptive Cyber Defense,
https://www.iacdautomate.org/) framework
for vendor-agnostic interoperability and automation.
IACD separates functionality as:
- sensing (gathering information)
- sense making (data augmentation, analytics, ... )
- decision making
- acting

In such an automated system, the decison making module may send a command
(e.g. an OpenC2 command)
to a sensing function (which may reside on the device itself)
to obtain the device's SBOM.
Following a CACAO playbook, it may then send the SBOM to a sense-making function
to correlate the SBOM with vulnerabilities (eg vs the NVD) and licensing issues.
Depending on the answers, it would follow different paths in the CACAO playbook
(connect, patch, sandbox, send to detonation chamber, send to deception engine, ...).

This is a case when an
'ingredients-only baseline SBOM'
is augmented with'beyond baseline' information?
Is it still an SBOM?

What is the artifact called when the
'ingredients-only baseline SBOM'
is augmented with'beyond baseline' information?
For some stakeholders, it would be advantageous
if these 'beyond baseline' artifacts
went by names other than SBOMs.

### Component to license relationships
If the 'ingredients-only baseline SBOM' is augmented
with the relationship of each component to licensing information:
- Should such artifacts be able to be called SBOMs?
- Or should it have a qualifier (eg 'Licensing' SBOMs)?
- Or should they have a different name entirely?

### Component to CVE relationships
If the 'ingredients-only baseline SBOM' is augmented
with the relationship of each component to CVE information:
- Should such artifacts be able to be called SBOMs?
- Or should it have a qualifier (eg 'CVE' SBOMs)?
- Or should they have a different name entirely?

### Component 'affected'
The VEX contains component "affected/not-affected" relationship to vulnerability
... from VEX docs.
Is it agreed that is called a VEX, not an SBOM?
What if an SPDX or CycloneDx artifact:
- starts ingredients only (called an SBOM)
- has CVE relationship information added (does 'type' or 'name' of document change?)
- has "affected/not-affected relationship to vulnerability" added (while still containing the other info)

### Component Assembly
If the 'ingredients-only baseline SBOM' is augmented
with the information on an 'as-built' instantiation was created
(eg which version of compiler with which configuration options):
- Should such artifacts be able to be called SBOMs?
- Or should it have a qualifier (eg 'build' SBOMs)?
- Or should they have a different name entirely?

### Component Provenance & Pedigree relationships
what if provenance and pedigree information is included?
What is the artifact called in this case?

## Totally different (but confounded) Topic
What is the SWOTS of?
- a source package on github (eg https://github.com/sFractal-Podii/quizquadaminos)
   + note this is amorphous without a specific date/time, package, ...
   + not useful for many usecases, but still use better than nothing
- a source-only github release (eg https://github.com/sFractal-Podii/quizquadaminos/releases/tag/v0.7.2)
   + this is a dated release. It is (sort of, more later) the actual code that ran the game at RSAC
   + note it does not contain the compiled binaries
- the binary of the previous bullet (with it's own subflavors)
- as would come from a package manager. This case probably should be language dependent since different languages put different combinations in their packages of:
   + source,
   + machine-independent virtual machine bytecode (eg pyc in python, beam in erlang, ..),  
   + machine-dependent executables
- 'as built' ie including config files and instantiation-specific details
   + in the game example above, the host url is the only difference between two
instantiations (eg test.qqb.sfractal.com for test and quadblockquiz.org for production). But that change ripples into different compiled binaries (BEAM bytecode in this case)
