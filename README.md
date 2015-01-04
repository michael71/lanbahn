lanbahn
=======

<p>project home pages:    http://www.lanbahn.net  and   http://www.oscale.net/en</p>

<p>Software (and Hardware) for controlling Model Railroads via Networks (UDP Multicast commands) </p>
<p>LAN-Bahn (german) = local area network - model railroad (english)</p>

<table border="0"><tr><td>
<a href="http://www.lanbahn.net" target="_blank"><img src="http://www.lanbahn.net/wp-content/uploads/2014/12/lanbahn-sigplus-rev.0.21-292x300.png" alt="lanbahn-sigplus-rev.0.2" width="292" height="300" /></a></td><td>
<a href="http://www.lanbahn.net" target="_blank"><img src="http://www.lanbahn.net/wp-content/uploads/2014/12/lonstoke_west_signal-227x300.png" alt="lonstoke_west_signal" width="227" height="300" /></a></td></tr></table>

The Lanbahn <b>protocol</b> is actually very simple:

Every device (smartphone, tablet, decoder, …) is communicating via UDP Multicasts to everyone 
in the network (just like the tradional model railroad “Bus” systems). ASCII transmission 
is choosen because ease of debugging.

The standard “channel” concept is also retained, so each accessory decoder and each locomotive
are having a unique “address” (from 1 to 10000(?)).

<h3>PROTOCOL Rev. 2.0:</h3>

<pre>
SET &lt;addr&gt; &lt;data&gt;  and  READ &lt;addr&gt;
    set address 911 to state 1 by sending the message: “S 911 1″. Trigger reading of 
    channel 911 with “R 911″ – and the decoder with address 911 will respond with it’s 
    current state “S 911 1″.

FB &lt;addr&gt; &lt;data&gt; (FEEDBACK) 
    messages from the accessory decoders were introduced after the experience of a 
    noisy     environment at the Warley Show (where 1 out of 500 commands did not
    reach the accessory) – “FB 911 1″ meaning: command understood and having set 
    decoder 911 to 1.
    
LOCO &lt;addr&gt; &lt;speed&gt; &lt;functions&gt;
    set speed and functions of a locomotive. Locos have a separate command to allow
    address overlaps between accessory decoders and locomotives to allow use of loco-
    numbers (like 7411) as addresses.
    
FL &lt;addr&gt; &lt;speed&gt; &lt;functions&gt; (= FEEBACK from Loco)
    tbd.

LOCK &lt;addr&gt;
    is the same a set (“L 911 1″ = set channel 911 to 1 and lock the decoder), except
    that it locks the decoder state afterwards (i.e. decoder will not respond to a
    new “SET” until it is unlocked again or a new "Start of Day" message is received).

UNLOCK &lt;addr&gt;
    is unlocking a decoder (“U 987″ = unlock channel 987)
    
SOD = START OF DAY
    "SOD" means: all decoders back to start position (i.e. red for signal, closed for
    turnouts)
    
A = Announce
    regularly decoder capabilities can be announce, exact format still unclear

RT &lt;n&gt; (= Routing)
    commands starting with “R” are used in routing, to announce that a route was set 
    or cleared.
    
</pre>
