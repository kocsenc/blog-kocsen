---
layout: post
title:  "Building a $600 Router for $300"
date:   2015-11-26 10:42:15 -0500
---


If you have ever built your own PC, it's very similar. You get **great bang for buck** and **awesome flexibility**.

# Let's build it
You mainly need three things to make any router work.

* Hardware
* Wireless Hardware
* Software

**Hardware**
I got my board from [PC Engines][pc-home]. It's a super **sketchy** site, in a good way though. Kind of like a mom & pop store of the internet; with amazing craftsmanship. They're located @ Sweden.
I personally got the [APU][pc-apu] model. (Detailed list below)

![APU](/assets/apu.jpg)

**Wireless Hardware**
I went a little overboard and got an Enterprise AP. Ubiquity UniFi makes awesome products
I got the [UniFi AP AC Lite][ac-lite]. You get: `802.11ac`, up to 867 Mbps, [PoE](https://en.wikipedia.org/wiki/Power_over_Ethernet), and the fastest connection I've ever seen.

> Honestly, you can just get this, plug it into your existing router, turn off your wireless on the old router and you'll see amazing performance boosts.

In fact if you're just tired of your router, get this first and give it a try. You'll probably be super satisfied. This is one of those companies that is showing companies like Cisco that you can have enterprise grade hardware for reasonable prices. What they do is admirable, kudos to Ubiquiti.

![UniFi AP AC Lite](/assets/lite.jpg)

**Software**
Easy. [PF Sense][pfsense-home]. It's basically the defacto for routing and even excellent firewalls and security. Based off of `FreeBSD`.

![PF Sense Logo](/assets/pfsense.jpg)

# Mandatory detailed list of items I used
1. PC Engines - [APU board][pc-apu] (I got the 4GB DRAM one called `apu1d4`)
1. `APU`: [Case](http://www.pcengines.ch/case1d2blku.htm) (required for cooling)
1. `APU`: [A/C adapter](http://www.pcengines.ch/ac12vus.htm)
1. `APU`: Memory. [mSATA SSD](http://www.pcengines.ch/msata16d.htm) or [SD Card](http://www.pcengines.ch/sd4b.htm)
1. `APU`: [Null Modem Cable](http://www.pcengines.ch/db9cab1.htm) AND [USB to Serial](http://amzn.com/B00IDSM6BW) to interface with the `APU`.
1. [If not using an AP] [miniPCI express wireless](http://www.pcengines.ch/wle200nx.htm) with appropriate antennaes and stuff. Not for me, I want my AP.
1. `AP`: UniFi [UAP AC LITE][ac-lite]. I got it on [amazon]().
1. `Software`: PF Sense -> Free, <3 open source.

> Note: A lot of these items link to PC Engines site, but you can get them wherever since they are *not* proprietary!

**Total**: $290


# Putting it together

![PC Engines Box](/assets/materials.jpg)

I don't want to get to deep into this because PC Engines and PF Sense documentation is great, so I'm listing a very general steps and resources.


1. Assemble the APU board + case.
1. Connect your Serial connection and set up correct frequencies.
1. Boot up the APU board and set up BIOS settings.
1. Setup a bootable USB PFSense. You want `AMD 64`, `NanoBSD` OR `USB Memstick Live`, and `Serial` console. Then [burn it][pf-burn].
1. Install BSD on APU board.

Read at least:

* This [guide][pf-guide]
* [APU Documentation][pc-apu] -> Find it with your model, it's a `.pdf`.

Other more detailed guides found [here][G1] and [here][G2].

I now have the full power of PFSense with capabilities for VPN server, Epic Firewall, Dyanmic DNS, and [more](https://www.pfsense.org/about-pfsense/features.html). Meanwhile I have an enterprise level AP dealing with IP assignation. Fun fact, that little guy also runs Linux - or some flavor, probably `BusyBox`.

# Here's the finished product

## TBP IMAGE HERE


# Why did I do this?

The main reason I did this was because at least once a week I had to restart my router, because it would just stop performing right. Dropping some connections, or slowing down speeds.
I was tired at the lack of performance.

`<rant>`

> "Kocsen, **why** would you ever build your own router? You can get a cheap Linksys Router for $30 bucks".

And that's the problem. Consumer grade routers are literally *toys*. Even ones that are [over $200](http://www.linksys.com/us/p/P-WRT1900ACS/) have proprietary (and potentially *unsafe*) software along with sub-par hardware.

`</rant>`

[pc-home]: http://www.pcengines.ch/about.htm
[pc-apu]: http://www.pcengines.ch/apu.htm
[pfsense-home]: https://www.pfsense.org
[pf-guide]: https://doc.pfsense.org/index.php/Installing_pfSense
[ac-lite]: https://www.ubnt.com/unifi/unifi-ap-ac-lite/
[pf-burn]: https://doc.pfsense.org/index.php/Writing_ISO_Images
[G1]: https://mateh.id.au/2014/09/build-awesome-apu-based-pfsense-router/
[G2]: http://www.get-virtual.net/2014/09/16/build-firewall-appliance/
