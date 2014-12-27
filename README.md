lanbahn
=======

project home pages:    http://www.lanbahn.de  and   http://www.oscale.net/en

Software for controlling Model Railroads via Networks (UDP Multicast commands)

The Lanbahn protocol is actually very simple:

Everyone (smartphone, tablet, decoder, …) is communicating via UDP Multicasts to everyone 
in the network (just like the tradional model railroad “Bus” systems). ASCII transmission 
is choosen because ease of debugging.

The standard “channel” concept is also retained, so each accessory decoder and each locomotive are having a unique “address” (from 1 to 10000(?)).

There are a few commands available:

SET (“S”) and READ (“R”) – set address 911 to state 1 by sending the message: “S 911 1″. Trigger reading of 
channel 911 with “R 911″ – and the decoder with address 911 will respond with it’s current state “S 911 1″.

Feedback messages from the accessory decoders were introduced after the experience of a noisy environment at
the Warley Show (where 1 out of 500 commands did not reach the accessory) – “OK 911 1″ meaning: command understood
and having set decoder 911 to 1.

LOCK (“L”) is the same a set (“L 911 1″ = set channel 911 to 1 and lock the decoder), except that it locks 
the decoder state afterwards (i.e. decoder will not respond to a new “SET” until it is unlocked again).

UNLOCK (“U”) is unlocking a decoder (“U 987″ = unlock channel 987)

commands starting with “F” are used in routing, to announce that a route was set or cleared 

More to come soon ....


