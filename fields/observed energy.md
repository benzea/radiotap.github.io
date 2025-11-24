---
title: Observed energy
categories: [defined]
type: 35
---
Type
: 35

Structure
: u16 known
: u16 bw

Unit(s)
: none

This field contains information related to the energy that was observed and
likely belong to the same transmission. This may be larger than the required
signal bandwidth if the transmission was duplicated over multiple channels.

The `known` field indicates which information is known:

| **flag** | **definition** | **notes** |
| 0x0001 | observed energy bandwidth known | In `bw` part of the field |

The `bw` field encodes the observed bandwidth in MHz. The reported bandwidth is
sufficient to contain all subchannels where energy likely belonging to the
same transmission was observed.
