# Flavors of Software Transparency Artifacts

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

I deliberately used 'artifact' as a catch-all.
I will attempt to use 'writeup' to mean the text you are reading -
so as not to confuse with "documents" that the artifacts we
are trying to describe.
I will attempt to avoid the use of the word document
since artifacts may be documents (english text, xml, etc)
but they may not be, by at least some definitions of the word 'document'
(e.g. JSON data structures in a Machine-to-Machine protocol).
I will attempt to use 'component' to mean 'the thing that
we are being transparent about' and hopefully be able to
avoid whether it is 'mid-stream' (i.e. downstream of its component parts
yet upstream of some component that used it) or 'finished good'
(i.e has no downstream components of which it is a component).

I believe that we will talk past each other less
if we understand 'which flavor' is under discussion
and what use case it is being used in.

Flavor examples where clarification would be beneficial:
- ingredients only
- assembly instructions
- component to license relationships
- known-unknowns / incomplete / "one-hop" / "complete"
- component to vulnerability relationships
- component "affected/not-affected" relationship to vulnerability
- has ingredients but not 'sufficient' for SBOM baseline as defined by framing
- has insufficient data for a particular use case (many examples which will need to be un-confounded)

I believe this is one source of our talking past each other,
and that having 'document names' will allow us to better reach consensus on many other topics.

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
the producer of the document,
and the consumer of the document.
They may be the same
(i.e. document is for internal consumption).
The component producer
(i.e. the thing the document is about)
is a different role from
this writeup's perspective.
The document producer may or may not be the
component producer.
This writeup allows for other-than-component-producer
creating relevant documents.
"Authority" to produce a document,
and 'trust' of that document are out of scope for this writeup.

Everything in this writeup assumes
the document producer
and the document consumer
have a sufficient trust relationship
for the use cases.
How that is achieved is outside the scope of this writeup.

Everything in this writeup assumes
the document producer
has sufficient data to produce the document accurately.
Incompleteness is addressed but inaccuracy and integrity
are outside the scope of this writeup.

This writeup assumes parties in the use case,
and only the parties in the use case,
have access to the document.
How confidentiality is achieved,
(and what level of confidentiality
is appropriate) is out-of-scope.

TL;DR confidentiality, integrity, availability are beyond scope of naming
which documents we are talking about in this writeup -
albeit they will introduce more
flavors once they are addressed.

## Big Picture
In Allan's previous life, he championed vulnerability coordination
and FIRST has the following pic on it's website (
https://www.first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.1):

![Big Picture](./VulnMultipartyFigure-1.jpeg)

When necessary to define roles, I will use the roles on this pic
