---
title: SERVICE field
categories: [defined]
type: 36
---
Type
: 36

Structure
: u8 known
: u8 flags
: u16 service\_field
: u8 ch\_bw\_in\_non\_ht

Unit(s)
: none

For some frames, the scrambler and SERVICE field bits may be used to encode
further information about the frame. This field exists to report related
information when available.

The `known` field indicates which information is known:

| **flag** | **definition** | **notes** |
| 0x01 | service field known | The service field bits in `service_field` are valid. |
| 0x02 | scrambler init known | The lower bits in `service_field` represent the scrambler initialization value. |
| 0x03 | dynamic BW in non-HT known | In `ch_bw_in_non_ht` part of the field. |

The `flags` field is any combination of the following:

| **flag** | **definition** | **notes** |
| 0x01 | dynamic BW in non-HT | Set if the dynamic BW in non-HT bit was set in the scrambler bits |
| 0x02 | 11bit scrambler init | Set for frames that have 11 bit of scrambler initialization (e.g. EHT) |

The `service_field` may contain both the scrambler initialization and the SERVICE field value
that was received depending on the flags in `known`. The lower bits are used to store the
scrambler initialization as the SERVICE field must be all zero there.
The scrambler initialization may be 7 or 11 bit long depending on the PHY type of the frame.
If it is 11 bit, then the corresponding bit is set in `flags`.

The `ch_bw_in_non_ht` field contains the value of `CH_BANDWIDTH_IN_NON_HT` as defined in
IEEE802.11REVmf-D1.0 Table 17-8 - "TXVECTOR parameter `CH_BANDWIDTH_IN_NON_HT` values".
