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
workgroup: "COSE (CBOR Object Signing and Encryption)"
keyword:
venue:
  group: "CBOR Object Signing and Encryption (COSE)"
  type: "Working Group"
  mail: "cose@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/cose/"
  github: "cabo/turbo-kanga"
  latest: "https://cabo.github.io/turbo-kanga/draft-bormann-cose-turbo-kanga-latest.html"

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

This document specifies or updates registrations for a number of
Keccak-based algorithms in the COSE Algorithms Registry.

RFC 9861 defined and registered four eXtendable-Output Functions
(XOFs), hash functions with output of arbitrary length, named
TurboSHAKE128, TurboSHAKE256, KT128, and KT256; the present document
is intended as the IETF consensus document that is now needed to give
these algorithms Recommended status in the COSE registry.

RFC 9861 only hints at MACs that could make use of the TurboSHAKE and
KT algorithms.
This document completes the specification of HopMAC128 and HopMAC256
from RFC 9861 and also specifies simpler MACs directly based on KT128
and KT256.
Finally, this document registers COSE Algorithm identifiers for the
KMAC set of algorithms (NIST.SP.800-185).

--- middle

[^replace-xxxx]: RFC Ed.: throughout this section, please replace
    RFC-XXXX with the RFC number of this specification and remove this
    note.

# Introduction

(Please see abstract.)

## Conventions and Terminology

{::boilerplate bcp14-tagged}

<!-- Some examples in this specification are truncated using "..." for readability. -->

# Status Recommended for TurboSHAKE128, TurboSHAKE256, KT128, and KT256

(Add text with rationale.)

{{sec-regupdate}} describes the updates needed in the COSE Algorithms registry.

# MAC Algorithms Based on TurboSHAKE128, TurboSHAKE256, KT128, and KT256

(Add specifications for the HopMACs and for a simple KT based MAC.)

# SHA-3 based Algorithms (KMAC etc.)

{{NIST.SP.800-185}}

[^kmac]: What algorithms do we want to register?
    Maybe directly include cSHAKE?

[^kmac]

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


| Name             | Value | Description               | Reference                   | Recommended |
|------------------|-------|---------------------------|-----------------------------|-------------|
| HopMAC256        | -nnn  | HopMAC based on KT256 XOF | {{RFC9861}}, RFC-XXXX         | Yes         |
| HopMAC128        | -nnn  | HopMAC based on KT128 XOF | {{RFC9861}}, RFC-XXXX         | Yes         |
| xxxTurboSHAKE256 | -nnn  | TurboSHAKE256 XOF         | {{RFC9861}}, RFC-XXXX         | Yes         |
| xxxTurboSHAKE128 | -nnn  | TurboSHAKE128 XOF         | {{RFC9861}}, RFC-XXXX         | Yes         |
| cSHAKE128        | -nnn  | cSHAKE128                 | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
| cSHAKE256        | -nnn  | cSHAKE256                 | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
| KMAC128          | -nnn  | KMAC128                   | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
| KMAC256          | -nnn  | KMAC256                   | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
| KMACXOF128       | -nnn  | KMACXOF128                | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
| KMACXOF256       | -nnn  | KMACXOF256                | {{NIST.SP.800-185}}, RFC-XXXX | Yes         |
{: #tab-add align="left" title="Registrations Added to COSE Algorithms"}

# Security Considerations

--- back

# Examples

TBD

# Acknowledgments
{:numbered="false"}

TBD
