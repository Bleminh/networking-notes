TCP VS UDP:
TCP:
- Connection Oriented. Official "start" and "end".
- Reliable:
+ Confirmation of data delivery.
+ Sender is aware of errors.
+ Data is delivered in order.
- Flow Control: TCP adjusts transmission rate to safely use maximum available bandwidth without exceeding it.
- More Overhead (TCP at L4 is larger (in terms of bits (20-60 bits) and structure?)).
UDP:
- Not Connection Oriented. No official "start" and "end". Connection defined by timeout (Source IP, destination IP, source port, destination port, protocol: UDP).
- No Confirmation of Delivery.
+ Fire and Forget.
+ No error awareness at L4.
+ No intrinsic data ordering.
- No Flow Control: UDP transmits as fast as it can.
- Less Overhead (only 8 bits).
- Important takeaways:
- Speed is identical. Latency (which affects speed) is unaffected by TCP or UDP.
- Security is identical. No security is provided by TCP or UDP.
- UDP doesn't provide reliability at L4. Protocols implement their own reliability.
- TCP provides confirmation of delivery. It doesn't guarantee delivery.