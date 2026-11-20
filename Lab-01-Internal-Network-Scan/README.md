# Internal network inventory

**Question:** Which devices and services are expected on the lab network, and what evidence links each observation to the correct device?

The original scan output, command line, host count and screenshots are unavailable. The workflow below can be used for a fresh capture.

1. Record the date, observation point and expected devices using aliases such as lab-laptop and lab-receiver.
2. Save the discovery output from the authorized lab. For each observation, compare the address and time with a DHCP lease or the device's own network settings.
3. Record the port, protocol and reported state. Verify the service on its host where possible. Mark uncertain identifications as unresolved.
4. Report one finding with its evidence and a follow-up action. A device missing from one observation may be asleep or on a different segment.

## Repeat the loopback check

This separate example uses Linux, Python 3, ss and curl. Use a free local port. In terminal A, start the temporary service in an empty directory:

~~~bash
cd "$(mktemp -d)"
python3 -m http.server 48173 --bind 127.0.0.1
~~~

In terminal B, record the listener and the local HTTP response:

~~~bash
ss -lntH 'sport = :48173'
curl --noproxy '*' --connect-timeout 2 -sS -o /dev/null -w '%{http_code}\n' http://127.0.0.1:48173/
~~~

Stop the server with Ctrl+C in terminal A. Repeat both checks. The documentation run observed a listener and HTTP 200 while the server ran. After shutdown the listener disappeared and curl exited with status 7. These measurements are local to the host and do not establish LAN reachability.
