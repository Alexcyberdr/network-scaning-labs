# Apple AirPlay receiver validation

**Investigation question:** Which observations change when the AirPlay receiver is enabled on the lab device?

The original folder identifies the topic, but the saved command file contains no historical command. No original output, port list, device version or screenshot was recovered. The steps below describe a repeatable comparison for a future run.

| Stage | What to record |
| --- | --- |
| Baseline | Record the date, receiver model and OS, receiver setting, and observer network. Assign aliases to the devices. |
| Receiver enabled | From the same network, record whether the receiver appears in the AirPlay picker. On the receiver, record the relevant listening sockets and processes where available. |
| Receiver disabled | Refresh discovery from the same observer after allowing for cached entries. Repeat the listener observation and compare. |
| Restore and verify | Restore the original setting, repeat discovery, and document any differences that persist. |

A port number alone does not establish that AirPlay owns the listener. Pair the setting change with a discovery observation and, when available, the owning process. If a result stays the same in both states, label it inconclusive.

**Evidence for the next run:** a short before/after table, a redacted screenshot from each state and the exact observation times. Until that capture exists, the receiver's exposed ports and service behavior remain unverified.
