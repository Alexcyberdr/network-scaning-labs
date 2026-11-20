# Network discovery and service validation

This portfolio explores how to compare a network observation with evidence from the device that owns the service. The two original practice folders survive, but their scan outputs and screenshots were not preserved in this repository.

| Case | Question | Evidence available |
| --- | --- | --- |
| [Internal network inventory](Lab-01-Internal-Network-Scan/) | Which expected devices and services can be accounted for? | Collection guide plus a separate, verified Linux loopback example below. |
| [Apple AirPlay service validation](Lab-02-Full-Port-Scan-Apple-AirPlay/) | Does a network observation correspond to the receiver setting on the device? | Before-and-after validation plan. Original device findings are unavailable. |

## Worked example: verifying when a listener is reachable

A separate documentation check used a temporary HTTP service bound to the Linux loopback interface. This example illustrates the inventory method on one host; the original home network and Apple device were outside its scope.

| Condition | Local observation on TCP 48173 | Client observation |
| --- | --- | --- |
| Service running | Listening on 127.0.0.1 | HTTP 200 from the local client |
| Service stopped | No matching listener | Connection failed (curl exit 7) |

The change in both observations ties the endpoint to the temporary service. A loopback result establishes reachability only from that same host. [Repeat the check](Lab-01-Internal-Network-Scan/#repeat-the-loopback-check).
