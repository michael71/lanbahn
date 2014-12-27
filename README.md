lanbahn
=======

project home pages:    http://www.lanbahn.net  and   http://www.oscale.net/en

Software for controlling Model Railroads via Networks (UDP Multicast commands)

The Lanbahn protocol is actually very simple:

Every device (smartphone, tablet, decoder, …) is communicating via UDP Multicasts to everyone 
in the network (just like the tradional model railroad “Bus” systems). ASCII transmission 
is choosen because ease of debugging.

The standard “channel” concept is also retained, so each accessory decoder and each locomotive are having a unique “address” (from 1 to 10000(?)).

There are a few commands available:

<pre>
S = SET 
R = READ 
    set address 911 to state 1 by sending the message: “S 911 1″. Trigger reading of 
    channel 911 with “R 911″ – and the decoder with address 911 will respond with it’s current state “S 911 1″.

OK = FEEDBACK 
    messages from the accessory decoders were introduced after the experience of a noisy environment at
    the Warley Show (where 1 out of 500 commands did not reach the accessory) – “OK 911 1″ meaning: command 
    understood and having set decoder 911 to 1.

L = LOCK
    is the same a set (“L 911 1″ = set channel 911 to 1 and lock the decoder), except that it locks 
    the decoder state afterwards (i.e. decoder will not respond to a new “SET” until it is unlocked again or
    a new "Start of Day" message is received).

U = UNLOCK 
    is unlocking a decoder (“U 987″ = unlock channel 987)
    
D = START OF DAY
    "D 0" means: all decoders back to start position (i.e. red for signal, closed for turnouts)
    
A = Announce
    regularly decoder capabilities can be announce, exact format still unclear

F = Routing
    commands starting with “F” are used in routing, to announce that a route was set or cleared.
</pre>

More to come soon ....


