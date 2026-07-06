---
title: "COSE Algorithms for KangarooTwelve, TurboSHAKE and KMAC"
abbrev: "COSE: KangarooTwelve, TurboSHAKE, KMAC"
category: std

docname: draft-bormann-cose-turbo-kanga-kmac-latest
stream: IETF
number:
date:
consensus: true
v: 3
area: "Security"
workgroup: "CBOR Object Signing and Encryption"
keyword:
venue:
  group: "CBOR Object Signing and Encryption"
  type: "Working Group"
  mail: "cose@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/cose/"
  github: "cabo/turbo-kanga"
  latest: "https://cabo.github.io/turbo-kanga/draft-bormann-cose-turbo-kanga-kmac.html"

author:
 -
    name: Quynh Dang
    role: editor
    org: National Institute of Standards and Technology
    orgabbrev: NIST
    email: quynh.dang@nist.gov
 -
    name: "Your | Name Here"
    role: editor
    organization: org
    email: "Your@example.com"
 -
    name: Carsten Bormann
    role: editor
    org: Universität Bremen TZI
    street: Postfach 330440
    city: Bremen
    code: D-28359
    country: Germany
    phone: +49-421-218-63921
    email: cabo@tzi.org

normative:
  NIST.SP.800-185:
  RFC9861:
  IANA.cose: IANA.cose

informative:

...

--- abstract

RFC 9861 defined and registered four eXtendable-Output Functions
(XOFs), hash functions with output of arbitrary length, named
TurboSHAKE128, TurboSHAKE256, KT128, and KT256; the present document
is intended as the IETF consensus document that is now needed to give
these algorithms Recommended status in the COSE registry.

This document specifies concrete instances of those four functions above to be used as MACs in COSE.

This document also specifies concrete instances of KMAC128 and KMAC256 in {{NIST.SP.800-185}} to be used as MACs in COSE and registers code points for them.

And, this document provides "Recommended" status for those algorithms for COSE.



[^replace-xxxx]: RFC Ed.: throughout this section, please replace
    RFC-XXXX with the RFC number of this specification and remove this
    note.

--- middle

# Introduction

TurboSHAKE128, TurboSHAKE256, KT128, and KT256 specified in {{RFC9861}} have great performance improvement over Keccak-based functions specified in FIPS 202 and SP 800-185. This document specifies concrete instances of those four functions for being used as MACs in COSE and moves their status to "Recommended".

In addition, this document also specifies concrete instances of KMAC128 and KMAC256 specified in SP 800-185 for being used as MACs in COSE and registers code points for them.

## Conventions and Terminology

{::boilerplate bcp14-tagged}

<!-- Some examples in this specification are truncated using "..." for readability. -->

[^question]: Question for the group:

# MAC Algorithms Based on TurboSHAKE128, TurboSHAKE256, KT128, and KT256 for COSE

(Add specifications for the HopMACs and for a simple KT based MAC.)

## TurboSHAKE128-MAC
As specified in {{RFC9861, Section 2}}, TurboSHAKE128 has 2 required input parameters: the message M and the output length in bytes L, and one optional input parameter D.
TurboSHAKE128-MAC is a MAC using TurboSHAKE128 where M is the concatenation of the original input message, called M', and a 128-bit secret key, called K, denoted as M'|| K.
[^question] Does the group want to have a D value? If the answer is yes, what would it be?
[^question] L being 16 bytes (128 bits) is fine?

## TurboSHAKE256-MAC
As specified in {{RFC9861, Section 2}}, TurboSHAKE256 has 2 required input parameters: the message M and the output length in bytes L, and one optional input parameter D.
TurboSHAKE256-MAC is a MAC using TurboSHAKE256 where M is the concatenation of the original input message, called M', and a 256-bit secret key, called K, denoted as M'|| K.
[^question] Does the group want to have a D value? If the answer is yes, what would it be?
[^question] L being 32 bytes (256 bits) is fine?

## KT128-MAC
As specified in {{RFC9861, Section 3}}, KT128 has 2 required input parameters: the message M and the output length in bytes L, and one optional input parameter C.
KT128-MAC is a MAC using KT128 where M is the concatenation of the original input message, called M', and a 128-bit secret key, called K, denoted as M'|| K.
[^question] Does the group want to have a C value? If the answer is yes, what would it be?
[^question] L being 16 bytes (128 bits) is fine?

KT128 was designed to utilize parallelism in SIMD processors.

## KT256-MAC
As specified in {{RFC9861, Section 3}}, KT256 has 2 required input parameters: the message M and the output length in bytes L, and one optional input parameter C.
KT256-MAC is a MAC using KT256 where M is the concatenation of the original input message, called M', and a 256-bit secret key, called K, denoted as M'|| K.
[^question] Does the group want to have a C value? If the answer is yes, what would it be?
[^question] L being 32 bytes (256 bits) is fine?

KT128 was designed to utilize parallelism in SIMD processors.

# KMAC128 and KMAC256 for COSE

{{NIST.SP.800-185}} specifies two MAC algorithms: KMAC128 and KMAC256 which have 3 required input parameters and an optional customization string input, called S.
The key, K, shall be 128 and 256 bits for KMAC128 and KMAC256 respectively.

[^question] Does the group want to have S to be an empty string? Or, is there a specific string the group would like to use?

# IANA Considerations

[^replace-xxxx]

## Updates to the COSE Algorithms Registry {#sec-regupdate}

IANA is requested to update \[has updated] the registrations in the
COSE Algorithms registry in [IANA.cose] shown in {{tab-upgrade}} by
setting the Recommended status column to Yes, and by adding the present
document to the Reference column.

In {{tab-upgrade}}, the following columns all have the same content and
have been elided:

* Capabilities: `[kty]`
* Change Controller: IETF
* Reference: {{RFC9861}}, RFC-XXXX
* Recommended: Yes

| Name          | Value | Description       |
|---------------|-------|-------------------|
| KT256         |  -264 | KT256 XOF         |
| KT128         |  -263 | KT128 XOF         |
| TurboSHAKE256 |  -262 | TurboSHAKE256 XOF |
| TurboSHAKE128 |  -261 | TurboSHAKE128 XOF |
{: #tab-upgrade align="left" title="Registrations in COSE Algorithms Updated to Recommended: Yes"}

## Additions to Existing Registries {#sec-regadd}


IANA is requested to update \[has updated] the registrations in the
COSE Algorithms registry in [IANA.cose] shown in {{tab-upgrade}} by
setting the Recommended status column to Yes.

In {{tab-add}}, the following columns all have the same content and
have been elided:

* Capabilities: `[kty]`
* Change Controller: IETF


| Name              | Value | Description               | Reference                     | Recommended |
|------------------ |-------|---------------------------|-------------------------------|-------------|
| TurboSHAKE256-MAC | -nnn  | TurboSHAKE256 MAC         | {{RFC9861}}, RFC-XXXX         | Yes         |
| TurboSHAKE128-MAC | -nnn  | TurboSHAKE128 MAC         | {{RFC9861}}, RFC-XXXX         | Yes         |
| KMAC128           | -nnn  | KMAC128                   | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
| KMAC256           | -nnn  | KMAC256                   | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
| KT128-MAC         | -nnn  | KT128 MAC                 |  {{RFC9861}}, RFC-XXXX        | Yes         |
| KT256-MAC         | -nnn  | KT256 MAC                 |  {{RFC9861}}, RFC-XXXX        | Yes         |
{: #tab-add align="left" title="Registrations Added to COSE Algorithms"}

# Security Considerations

--- back

# Examples

TBD

# Acknowledgments
{:unnumbered}

TBD
