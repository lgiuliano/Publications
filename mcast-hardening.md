<p dir="auto">Internet multicast introduces a range of new security threats to a network. These threats are not necessarily any more or less destructive than those found in unicast-only networks, but they represent a new class of vulnerability that may be unfamiliar to those with minimal multicast experience. The following is a detailed set of recommended best practices for securing a multicast infrastructure of Juniper routers. These recommendations include the most comprehensive set of features in the industry and are forged by lessons learned after many years of deployment experience in the world’s largest Internet backbones.</p>
<h2 dir="auto"><a id="user-content---w-a-r-n-i-n-g--" class="anchor" aria-hidden="true" href="#--w-a-r-n-i-n-g--"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>! ! W A R N I N G ! !</h2>
<hr>
<p dir="auto">As with all such templates, this one must be modified to fit the specific requirements of the local network(s) and hosts. It is not wise to simply cut and paste without a thorough understanding of each command.</p>
<hr>
<h3 dir="auto"><a id="user-content-questions-comments-suggestions" class="anchor" aria-hidden="true" href="#questions-comments-suggestions"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Questions, Comments, Suggestions</h3>
<p dir="auto">Feedback is both welcome and encouraged! Please send any correspondence to
<a href="mailto:outreach@cymru.com">outreach@cymru.com</a> or
<a href="/team-cymru/network-security-templates/blob/master/Secure-Multicast-Templates/lenny@juniper.net">lenny@juniper.net</a>.</p>
<h3 dir="auto"><a id="user-content-credits" class="anchor" aria-hidden="true" href="#credits"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Credits</h3>
<p dir="auto">Our thanks to Lenny Giuliano @ Juniper Networks for authoring this document and making it available to us for publication!</p>
<h2 dir="auto"><a id="user-content-calm-during-the-storm-best-practices-in-multicast-security-for-junos" class="anchor" aria-hidden="true" href="#calm-during-the-storm-best-practices-in-multicast-security-for-junos"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Calm During the Storm: Best Practices in Multicast Security for JUNOS</h2>
<h4 dir="auto"><a id="user-content-by-lenny-giuliano-lennyjunipernet" class="anchor" aria-hidden="true" href="#by-lenny-giuliano-lennyjunipernet"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>By Lenny Giuliano &lt;<a href="mailto:lenny@juniper.net">lenny@juniper.net</a>&gt;</h4>
<p dir="auto">Originally, multicast deployment recommendations focused on filtering certain groups that should not be leaked into or out of a network. Some of these groups are protocol related, some are from legacy applications, and some are administratively scoped. Examples of these groups include:</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="224.0.1.2/32 SGI-Dogfight
224.0.1.3/32 RWHOD
224.0.1.8/32 SUN-NIS
224.0.1.22/32 SRVLOC 
224.0.1.24/32 MICROSOFT-DS
224.0.1.25/32 NBC-PRO
224.0.1.35/32 SVRLOC-DA
224.0.1.39/32 AUTORP-Announce
224.0.1.40/32 AUTORP-Discovery
224.0.1.60/32 HP-Device-Discovery
224.0.2.1/32 RWHO
224.0.2.2/32 SUN-RPC
224.77.0.0/16 Norton-Ghost
226.77.0.0/16 Norton-Ghost
225.1.2.3/32 Altiris
229.55.150.208/32 Norton-Ghost
234.42.42.40/30 Phoenix/StorageSoft ImageCast
239.0.0.0/8 Administratively Scoped"><pre class="notranslate"><code>224.0.1.2/32 SGI-Dogfight
224.0.1.3/32 RWHOD
224.0.1.8/32 SUN-NIS
224.0.1.22/32 SRVLOC 
224.0.1.24/32 MICROSOFT-DS
224.0.1.25/32 NBC-PRO
224.0.1.35/32 SVRLOC-DA
224.0.1.39/32 AUTORP-Announce
224.0.1.40/32 AUTORP-Discovery
224.0.1.60/32 HP-Device-Discovery
224.0.2.1/32 RWHO
224.0.2.2/32 SUN-RPC
224.77.0.0/16 Norton-Ghost
226.77.0.0/16 Norton-Ghost
225.1.2.3/32 Altiris
229.55.150.208/32 Norton-Ghost
234.42.42.40/30 Phoenix/StorageSoft ImageCast
239.0.0.0/8 Administratively Scoped
</code></pre></div>
<p dir="auto">In the past, a list of these unwanted groups was tracked and documented in draft-ietf-mboned-ipv4-mcast-bcp as providers discovered traffic that should not have been on the Internet, but that document has long since expired.</p>
<p dir="auto">Historically, the primary threat seen on multicast networks has been Multicast Source Discovery Protocol (MSDP) storms. Internet worms, such as Ramen, Slammer, and Sasser, have most often caused these storms. Typically, these worms infect a host and propagate by using these infected hosts to discover and attack other vulnerable hosts. To discover other vulnerable hosts, they usually select a large block of addresses (such as a /16) at random and port scan all hosts in that block. In just a few minutes, these infected hosts can scan up to tens or even hundreds of thousands of other hosts.</p>
<p dir="auto">The coders of these worms often randomly select any IP address range, inadvertently including IP multicast addresses (224/4) in the possible range. When packets are transmitted with a destination address in 224/4 on a multicast-enabled network, multicast protocols use this data to drive the creation of multicast state. For example, when a Protocol Independent Multicast – Sparse Mode (PIM-SM) router detects that one of its locally connected hosts is transmitting multicast packets, it encapsulates these packets in PIM register messages and sends these messages to the PIM-SM Rendezvous Point (RP), which keeps the state of these local sources. The RP then creates an MSDP Source Active (SA) message for each source-group pair and floods it to all its MSDP peers, which cache these messages and flood them to all their respective peers, until MSDP speakers across the Internet have populated their SA caches. In this way, a single infected host that port scans only a single /16 of multicast addresses will generate more than 65,000 MSDP SAs that are flooded and cached by all MSDP speaking routers on the Internet. As more hosts attack and scan larger blocks of multicast addresses, this state explosion quickly causes MSDP-speaking routers to run out of memory and crash. This type of attack, which is not even launched to intentionally affect the multicast infrastructure, is known as an MSDP SA storm. These storms are quite easy to launch and have been by far the most common type of attack seen on multicast networks to date. Juniper has introduced a number of features in its implementation of MSDP to mitigate and even eliminate the damage caused by MSDP storms. These features are described extensively in the following sections. Additionally, it should be noted that the damage done by MSDP storms is primarily accidental. That is, attackers damage critical components of the network infrastructure without even targeting these components.</p>
<p dir="auto">This document recommends a two-fold approach to hardening a multicast deployment: first, by enabling features that will reduce or eliminate the damage caused by attacks, and second, by reducing the size of the target for accidental attacks by using the concept of whitelisting. The most common use of filtering in network security involves blacklists. Blacklists simply contain a list of hosts or services that need to be denied, while all other hosts or services are permitted. Whitelists, on the other hand, contain a list of hosts or services that are permitted, while all other hosts or services are denied. So blacklists allow everything except what is on the list, while whitelists block everything except what is on the list.</p>
<p dir="auto">According to RFCs 5771 and 6308, the Internet Assigned Numbers Authority (IANA) has allocated addresses for global use only from the 224/8, 232/8, 233/8 and 234/8 address ranges. Multicast groups outside these ranges can be considered reserved from global use, and there is no legitimate reason to see this traffic on the Internet. Accordingly, this document recommends allowing forwarding and control traffic only for groups in these whitelisted ranges. By permitting only 1/4 of the possible multicast address range to be routed, 75 percent of the accidental attacks should be prevented.</p>
<h3 dir="auto"><a id="user-content-design-considerations" class="anchor" aria-hidden="true" href="#design-considerations"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Design Considerations</h3>
<p dir="auto">The recommendations listed in this document are supported on all routers that run JUNOS software. All features and commands mentioned have been available since JUNOS version 7.6 or earlier.</p>
<h3 dir="auto"><a id="user-content-scope" class="anchor" aria-hidden="true" href="#scope"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Scope</h3>
<p dir="auto">This dAocument assumes a multicast deployment that uses static anycast RP as the RP-mapping mechanism. An in-depth discussion of the operation of PIM-SM and MSDP is outside of the scope of this document. Additionally, for full documentation on the JUNOS software commands listed, consult the JUNOS Configuration Guide for “Multicast Protocols”.</p>
<h3 dir="auto"><a id="user-content-throttling-multicast-source-discovery-protocol" class="anchor" aria-hidden="true" href="#throttling-multicast-source-discovery-protocol"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Throttling Multicast Source Discovery Protocol</h3>
<p dir="auto">The most obvious method to prevent damage caused by MSDP storms is to rate limit. However, whenever you rate limit control traffic, you inadvertently introduce new vulnerability since it is usually impossible to tell the difference between a good control message and a bad one. For example, if you blindly rate limit all MSDP (TCP port 639) traffic to 1 Mbps, you simply lower the bar for attack. An attacker must send only 1 Mbps of MSDP traffic to engage the rate limiter, and all legitimate MSDP traffic is also blocked. Therefore, it is crucial that rate limiting be as intelligent as possible to deny the malicious, but permit the legitimate.</p>
<h3 dir="auto"><a id="user-content-per-source-limits" class="anchor" aria-hidden="true" href="#per-source-limits"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Per-Source Limits</h3>
<p dir="auto">The most important feature used to achieve intelligent rate limiting is per-source SA limits. Per-source limits prevent an MSDP speaker from allowing any single host to generate more than a configured maximum number of SAs. For example, a per-source limit of 1000 will not allow any individual host to generate more than 1000 SAs. A worm-infected host that port scanned a /16 of multicast addresses would then generate only 1000 SAs instead of more than 65,000. The configuration includes both a maximum and a threshold. SAs are randomly dropped using the random early detection (RED) algorithm after they exceed the threshold value. MSDP per- peer and per-instance rate limits use the same threshold and maximum syntax and behavior. It is difficult to imagine a host that legitimately sources more than 1000 multicast streams. In the event that there are known hosts that legitimately transmit more than 1000 multicast streams, these sources can be given larger limits. The following configuration allows the host 10.1.1.1 to generate up to 5000 MSDP SAs, while all other hosts on the Internet are rate limited to 1000 SAs.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="msdp {
    source 0.0.0.0/0 {
        active-source-limit {
            maximum 1000;
            threshold 900;
        }
    }
    source 10.1.1.1/32 {
        active-source-limit {
            maximum 5000;
            threshold 4500;
        }
    }
}"><pre class="notranslate"><code>msdp {
    source 0.0.0.0/0 {
        active-source-limit {
            maximum 1000;
            threshold 900;
        }
    }
    source 10.1.1.1/32 {
        active-source-limit {
            maximum 5000;
            threshold 4500;
        }
    }
}
</code></pre></div>
<p dir="auto">To see the per-source limits as they apply to all known multicast sources, use the show msdp source command:</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="lenny@paix&gt; show msdp source
Source address /Len Type Maximum Threshold Exceeded
0.0.0.0/0 Configured 1000 900 0
10.10.32.32 /32 Dynamic 1000 900 0
10.14.59.51 /32 Dynamic 1000 900 0
10.14.59.57 /32 Dynamic 1000 900 1243
10.39.0.144 /32 Dynamic 1000 900 0
10.89.2.245 /32 Dynamic 1000 900 13"><pre class="notranslate"><code>lenny@paix&gt; show msdp source
Source address /Len Type Maximum Threshold Exceeded
0.0.0.0/0 Configured 1000 900 0
10.10.32.32 /32 Dynamic 1000 900 0
10.14.59.51 /32 Dynamic 1000 900 0
10.14.59.57 /32 Dynamic 1000 900 1243
10.39.0.144 /32 Dynamic 1000 900 0
10.89.2.245 /32 Dynamic 1000 900 13
</code></pre></div>
<p dir="auto">To see only the hosts that exceed the per-source limits, use the “show msdp source | except “\ 0” regular expression:</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="lenny@paix&gt; show msdp source | except &quot;\ 0&quot;
Source address /Len Type Maximum Threshold Exceeded
10.14.68.99 /32 Dynamic 1000 900 81099693
10.51.171.149 /32 Dynamic 1000 900 540763
10.88.60.37 /32 Dynamic 1000 900 9080
10.88.176.175 /32 Dynamic 1000 900 1144711
10.58.5.249 /32 Dynamic 1000 900 425"><pre class="notranslate"><code>lenny@paix&gt; show msdp source | except "\ 0"
Source address /Len Type Maximum Threshold Exceeded
10.14.68.99 /32 Dynamic 1000 900 81099693
10.51.171.149 /32 Dynamic 1000 900 540763
10.88.60.37 /32 Dynamic 1000 900 9080
10.88.176.175 /32 Dynamic 1000 900 1144711
10.58.5.249 /32 Dynamic 1000 900 425
</code></pre></div>
<h3 dir="auto"><a id="user-content-per-peer-limits" class="anchor" aria-hidden="true" href="#per-peer-limits"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Per-Peer Limits</h3>
<p dir="auto">Per-peer SA limits rate limit the number of SAs received from an MSDP peer. These limits are functionally analogous to BGP maximum-prefix limits. The following configuration prevents the router from accepting more than 100,000 SAs from peer 1.1.1.1.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="msdp {
    group eMSDP-peer {
        local-address 2.2.2.2;
        peer 1.1.1.1 {
            active-source-limit {
                maximum 100000;
                threshold 90000;
            }
        }
    }
}"><pre class="notranslate"><code>msdp {
    group eMSDP-peer {
        local-address 2.2.2.2;
        peer 1.1.1.1 {
            active-source-limit {
                maximum 100000;
                threshold 90000;
            }
        }
    }
}
</code></pre></div>
<p dir="auto">To apply the same per-peer limit to all MSDP peers, use apply-groups.</p>
<h3 dir="auto"><a id="user-content-per-instance-limits" class="anchor" aria-hidden="true" href="#per-instance-limits"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Per-Instance Limits</h3>
<p dir="auto">Per-instance SA limits rate limit the maximum number of SAs that a router allows in the entire routing instance. The following configuration prevents the router from installing more than 200,000 SAs in its default routing instance.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="msdp {
	    active-source-limit {
            maximum 200000;
            threshold 190000;
	    }
}"><pre class="notranslate"><code>msdp {
	    active-source-limit {
            maximum 200000;
            threshold 190000;
	    }
}
</code></pre></div>
<h3 dir="auto"><a id="user-content-disabling-multicast-source-discovery-protocol-data-encapsulation" class="anchor" aria-hidden="true" href="#disabling-multicast-source-discovery-protocol-data-encapsulation"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Disabling Multicast Source Discovery Protocol Data Encapsulation</h3>
<p dir="auto">To support bursty sources, MSDP SAs may also contain actual multicast data packets. Typically, the first packet in a multicast stream is added to the SA. MSDP SAs are placed in inet.4, the routing table that contains the MSDP SA cache. Additionally, SAs that include encapsulated data are placed in the forwarding table. The forwarding table generally has less capacity than the routing table. Therefore, it is recommended to prevent the creation of unnecessary forwarding table entries, as the forwarding table is a finite resource that also contains all the unicast forwarding entries. The following configuration prevents originating RPs from placing encapsulated data in SAs and ignores the encapsulated data in SAs received by peers. This sample configuration prevents MSDP from creating forwarding table entries. Note, however, that the configuration may have an impact on bursty source applications. For instance, when the source transmits one multicast packet is every 20 minutes. If support for bursty source applications is critical, leave MSDP data encapsulation enabled.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="msdp {
    data-encapsulation disable;
} "><pre class="notranslate"><code>msdp {
    data-encapsulation disable;
} 
</code></pre></div>
<h3 dir="auto"><a id="user-content-multicast-source-discovery-protocol-filters" class="anchor" aria-hidden="true" href="#multicast-source-discovery-protocol-filters"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Multicast Source Discovery Protocol Filters</h3>
<p dir="auto">It is important to apply MSDP SA filters on all external MSDP sessions, inbound and outbound. MSDP SA filters prevent SAs for groups and sources that should remain inside a network from leaking in or out. At a minimum, these filters should be applied to all external MSDP peerings. The following configuration will prevent SAs (for sources and groups that do not belong on the Internet) from being transmitted or received by all MSDP peers.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="protocols {
    msdp {
        export sa-filter;
        import sa-filter;
    }
}
policy-options {
  policy-statement sa-filter {
      term bad-groups {
          from {
              route-filter 224.0.1.2/32 exact;
              route-filter 224.0.1.3/32 exact;
              route-filter 224.0.1.8/32 exact;
              route-filter 224.0.1.22/32 exact;
              route-filter 224.0.1.24/32 exact;
              route-filter 224.0.1.25/32 exact;
              route-filter 224.0.1.35/32 exact;
              route-filter 224.0.1.39/32 exact;
              route-filter 224.0.1.40/32 exact;
              route-filter 224.0.1.60/32 exact;
              route-filter 224.0.2.1/32 exact;
              route-filter 224.0.2.2/32 exact;
              route-filter 224.77.0.0/16 orlonger;
              route-filter 226.77.0.0/16 orlonger;
              route-filter 225.1.2.3/32 exact;
              route-filter 229.55.150.208/32 exact;
              route-filter 232.0.0.0/8 orlonger;
              route-filter 234.42.42.40/30 orlonger;
              route-filter 239.0.0.0/8 orlonger;
          }
          then reject;
      }
      term bad-sources {
          from {
              source-address-filter 10.0.0.0/8 orlonger;
              source-address-filter 127.0.0.0/8 orlonger;
              source-address-filter 172.16.0.0/12 orlonger;
              source-address-filter 192.168.0.0/16 orlonger;
          }
          then reject;
      }
      term accept-everything-else {
          then accept;
      }
   }
}"><pre class="notranslate"><code>protocols {
    msdp {
        export sa-filter;
        import sa-filter;
    }
}
policy-options {
  policy-statement sa-filter {
      term bad-groups {
          from {
              route-filter 224.0.1.2/32 exact;
              route-filter 224.0.1.3/32 exact;
              route-filter 224.0.1.8/32 exact;
              route-filter 224.0.1.22/32 exact;
              route-filter 224.0.1.24/32 exact;
              route-filter 224.0.1.25/32 exact;
              route-filter 224.0.1.35/32 exact;
              route-filter 224.0.1.39/32 exact;
              route-filter 224.0.1.40/32 exact;
              route-filter 224.0.1.60/32 exact;
              route-filter 224.0.2.1/32 exact;
              route-filter 224.0.2.2/32 exact;
              route-filter 224.77.0.0/16 orlonger;
              route-filter 226.77.0.0/16 orlonger;
              route-filter 225.1.2.3/32 exact;
              route-filter 229.55.150.208/32 exact;
              route-filter 232.0.0.0/8 orlonger;
              route-filter 234.42.42.40/30 orlonger;
              route-filter 239.0.0.0/8 orlonger;
          }
          then reject;
      }
      term bad-sources {
          from {
              source-address-filter 10.0.0.0/8 orlonger;
              source-address-filter 127.0.0.0/8 orlonger;
              source-address-filter 172.16.0.0/12 orlonger;
              source-address-filter 192.168.0.0/16 orlonger;
          }
          then reject;
      }
      term accept-everything-else {
          then accept;
      }
   }
}
</code></pre></div>
<h3 dir="auto"><a id="user-content-multicast-boundaries" class="anchor" aria-hidden="true" href="#multicast-boundaries"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Multicast Boundaries</h3>
<p dir="auto">Apply multicast boundary filters on all customer-facing interfaces by using multicast scoping. Multicast scoping prevents multicast packets from flowing into or out of an interface. Apply these scopes on all interfaces and on all routers in your network, since there is usually no good reason for these groups to flow on backbone links. The following configuration prevents multicast data packets from flowing into or out of all interfaces on the router for groups that do not belong on the Internet. This configuration also permits data packets in 239/8 to flow over backbone links, which is necessary on networks that allow 239/8 traffic for internal purposes.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="routing-options {
    multicast {
        scope-policy boundary-filter;
    }
}
policy-options {
    policy-statement boundary-filter {
        term permit-239-on-backbone {
            from {
                interface [ so-0/0/0.0 so-1/0/0.0 ];
                route-filter 239.0.0.0/8 orlonger;
            }
            then accept;
        }
        term bad-groups {
            from {
                route-filter 224.0.1.2/32 exact;
                route-filter 224.0.1.3/32 exact;
                route-filter 224.0.1.8/32 exact;
                route-filter 224.0.1.22/32 exact;
                route-filter 224.0.1.24/32 exact;
                route-filter 224.0.1.25/32 exact;
                route-filter 224.0.1.35/32 exact;
                route-filter 224.0.1.39/32 exact;
                route-filter 224.0.1.40/32 exact;
                route-filter 224.0.1.60/32 exact;
                route-filter 224.0.2.1/32 exact;
                route-filter 224.0.2.2/32 exact;
                route-filter 224.77.0.0/16 orlonger;
                route-filter 226.77.0.0/16 orlonger;
                route-filter 225.1.2.3/32 exact;
                route-filter 229.55.150.208/32 exact;
                route-filter 234.42.42.40/30 orlonger;
                route-filter 239.0.0.0/8 orlonger;
            }
            then reject;
        }
        term accept-everything-else {
            then accept;
        }
    }
}"><pre class="notranslate"><code>routing-options {
    multicast {
        scope-policy boundary-filter;
    }
}
policy-options {
    policy-statement boundary-filter {
        term permit-239-on-backbone {
            from {
                interface [ so-0/0/0.0 so-1/0/0.0 ];
                route-filter 239.0.0.0/8 orlonger;
            }
            then accept;
        }
        term bad-groups {
            from {
                route-filter 224.0.1.2/32 exact;
                route-filter 224.0.1.3/32 exact;
                route-filter 224.0.1.8/32 exact;
                route-filter 224.0.1.22/32 exact;
                route-filter 224.0.1.24/32 exact;
                route-filter 224.0.1.25/32 exact;
                route-filter 224.0.1.35/32 exact;
                route-filter 224.0.1.39/32 exact;
                route-filter 224.0.1.40/32 exact;
                route-filter 224.0.1.60/32 exact;
                route-filter 224.0.2.1/32 exact;
                route-filter 224.0.2.2/32 exact;
                route-filter 224.77.0.0/16 orlonger;
                route-filter 226.77.0.0/16 orlonger;
                route-filter 225.1.2.3/32 exact;
                route-filter 229.55.150.208/32 exact;
                route-filter 234.42.42.40/30 orlonger;
                route-filter 239.0.0.0/8 orlonger;
            }
            then reject;
        }
        term accept-everything-else {
            then accept;
        }
    }
}
</code></pre></div>
<h3 dir="auto"><a id="user-content-protocol-independent-multicast-bootstrap-router-filters" class="anchor" aria-hidden="true" href="#protocol-independent-multicast-bootstrap-router-filters"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Protocol Independent Multicast Bootstrap Router Filters</h3>
<p dir="auto">It is extremely important to make sure bootstrap router filter (BSR) messages do not leak into or out of your network. The following configuration prevents BSR messages from getting into or out of a router. Use this configuration on all routers.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="protocols {
    pim {
        rp {
            bootstrap-import no-bsr;
            bootstrap-export no-bsr;
        }
    }
}
policy-options {
    policy-statement no-bsr {
        then reject;
    }
}"><pre class="notranslate"><code>protocols {
    pim {
        rp {
            bootstrap-import no-bsr;
            bootstrap-export no-bsr;
        }
    }
}
policy-options {
    policy-statement no-bsr {
        then reject;
    }
}
</code></pre></div>
<h3 dir="auto"><a id="user-content-protocol-independent-multicast-join-filters" class="anchor" aria-hidden="true" href="#protocol-independent-multicast-join-filters"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Protocol Independent Multicast Join Filters</h3>
<p dir="auto">Multicast scopes prevent multicast data packets from flowing into or out of an interface. PIM join filters prevent the creation of PIM-SM state, so multicast traffic is not transmitted across your network and dropped at a scope at the edge. Also, PIM join filters reduce the potential for denial-of-service (DOS) attacks and PIM state explosion. PIM join filters apply only to PIM-SM state. If you use them, apply them to all routers in your network. The following configuration will reject PIM joins sent by neighbors for groups that do not belong on the Internet. This configuration also permits PIM joins to flow over backbone links, which is necessary on networks that allow 239/8 traffic for internal purposes.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="protocols {
    pim {
        import pim-join-filter;
    }
}
policy-options {
    policy-statement pim-join-filter {
        term permit-239-on-backbone {
            from {
                interface [ so-0/0/0.0 so-1/0/0.0 ];
                route-filter 239.0.0.0/8 orlonger;
            }
            then accept;
        }
        term bad-groups {
            from {
                route-filter 224.0.1.2/32 exact;
                route-filter 224.0.1.3/32 exact;
                route-filter 224.0.1.8/32 exact;
                route-filter 224.0.1.22/32 exact;
                route-filter 224.0.1.24/32 exact;
                route-filter 224.0.1.25/32 exact;
                route-filter 224.0.1.35/32 exact;
                route-filter 224.0.1.39/32 exact;
                route-filter 224.0.1.40/32 exact;
                route-filter 224.0.1.60/32 exact;
                route-filter 224.0.2.1/32 exact;
                route-filter 224.0.2.2/32 exact;
                route-filter 224.77.0.0/16 orlonger;
                route-filter 226.77.0.0/16 orlonger;
                route-filter 225.1.2.3/32 exact;
                route-filter 229.55.150.208/32 exact;
                route-filter 234.42.42.40/30 orlonger;
                route-filter 239.0.0.0/8 orlonger;
            }
            then reject;
        }
        term bad-sources {
            from {
                source-address-filter 10.0.0.0/8 orlonger;
                source-address-filter 127.0.0.0/8 orlonger;
                source-address-filter 172.16.0.0/12 orlonger;
                source-address-filter 192.168.0.0/16 orlonger;
            }
            then reject;
        }
        term accept-everything-else {
            then accept;
        }
    }
}"><pre class="notranslate"><code>protocols {
    pim {
        import pim-join-filter;
    }
}
policy-options {
    policy-statement pim-join-filter {
        term permit-239-on-backbone {
            from {
                interface [ so-0/0/0.0 so-1/0/0.0 ];
                route-filter 239.0.0.0/8 orlonger;
            }
            then accept;
        }
        term bad-groups {
            from {
                route-filter 224.0.1.2/32 exact;
                route-filter 224.0.1.3/32 exact;
                route-filter 224.0.1.8/32 exact;
                route-filter 224.0.1.22/32 exact;
                route-filter 224.0.1.24/32 exact;
                route-filter 224.0.1.25/32 exact;
                route-filter 224.0.1.35/32 exact;
                route-filter 224.0.1.39/32 exact;
                route-filter 224.0.1.40/32 exact;
                route-filter 224.0.1.60/32 exact;
                route-filter 224.0.2.1/32 exact;
                route-filter 224.0.2.2/32 exact;
                route-filter 224.77.0.0/16 orlonger;
                route-filter 226.77.0.0/16 orlonger;
                route-filter 225.1.2.3/32 exact;
                route-filter 229.55.150.208/32 exact;
                route-filter 234.42.42.40/30 orlonger;
                route-filter 239.0.0.0/8 orlonger;
            }
            then reject;
        }
        term bad-sources {
            from {
                source-address-filter 10.0.0.0/8 orlonger;
                source-address-filter 127.0.0.0/8 orlonger;
                source-address-filter 172.16.0.0/12 orlonger;
                source-address-filter 192.168.0.0/16 orlonger;
            }
            then reject;
        }
        term accept-everything-else {
            then accept;
        }
    }
}
</code></pre></div>
<h3 dir="auto"><a id="user-content-pim-register-filters" class="anchor" aria-hidden="true" href="#pim-register-filters"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>PIM Register Filters</h3>
<p dir="auto">PIM register filters can be used to prevent unwanted traffic from creating PIM register state on the RP. These filters can be applied on the RP as well as on the source’s designated router (DR). By filtering at the DR, the register messages are never sent to the RP. By filtering at the RP, unwanted register messages sent from any DR will be discarded.</p>
<p dir="auto">PIM registers can be filtered based on the source address or group address. The following example shows a DR filter that allows local sources in 10.1.1.0/24 to register for groups in 224.1.0.0/16. All PIM registers for traffic outside these sources and groups will be prevented from sending registers to the RP.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="protocols {
    pim {
        rp {
            dr-register-policy dr-filter;
        }
    }
}
policy-options {
    policy-statement dr-filter {
        term permitted-sources-groups {
            from {
                route-filter 224.1.0.0/16 orlonger;
                source-address-filter 10.1.1.0/24 orlonger;
            }
            then accept;
        }
        term deny-everything-else {
            then reject;
        }
    }
}    "><pre class="notranslate"><code>protocols {
    pim {
        rp {
            dr-register-policy dr-filter;
        }
    }
}
policy-options {
    policy-statement dr-filter {
        term permitted-sources-groups {
            from {
                route-filter 224.1.0.0/16 orlonger;
                source-address-filter 10.1.1.0/24 orlonger;
            }
            then accept;
        }
        term deny-everything-else {
            then reject;
        }
    }
}    
</code></pre></div>
<p dir="auto">The following example shows an RP filter that also allows sources in 10.1.1.0/24 to create register state on the RP for groups in 224.1.0.0/16. All PIM registers for traffic outside these sources and groups from all DRs will be filtered on this RP.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="protocols {
    pim {
        rp {
            rp-register-policy rp-filter;
        }
    }
}
policy-options {
    policy-statement rp-filter {
        term permitted-sources-groups {
            from {
                route-filter 224.1.0.0/16 orlonger;
                source-address-filter 10.1.1.0/24 orlonger;
            }
            then accept;
        }
        term deny-everything-else {
            then reject;
        }
    }
}  "><pre class="notranslate"><code>protocols {
    pim {
        rp {
            rp-register-policy rp-filter;
        }
    }
}
policy-options {
    policy-statement rp-filter {
        term permitted-sources-groups {
            from {
                route-filter 224.1.0.0/16 orlonger;
                source-address-filter 10.1.1.0/24 orlonger;
            }
            then accept;
        }
        term deny-everything-else {
            then reject;
        }
    }
}  
</code></pre></div>
<h3 dir="auto"><a id="user-content-pim-passive-interfaces" class="anchor" aria-hidden="true" href="#pim-passive-interfaces"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>PIM Passive Interfaces</h3>
<p dir="auto">When more than one router on a LAN is running PIM, DR election is performed. The router with the highest DR priority is elected as the DR. If the priorities are the same, the router with the highest IP address is usually elected as the DR. On a stub network with only one router, it may be desirable to ensure that the router is always elected as the DR. This approach prevents a malicious host or misconfigured router from hijacking the DR assignment, which can prevent all hosts on the LAN from sourcing or joining multicast traffic outside the LAN.</p>
<p dir="auto">To ensure that the stub router becomes the DR and ignores all other PIM neighbors on the LAN, you can set the hello-interval value to 0. This setting will simulate a passive interface, where the protocol is enabled on the interface, but no hellos are transmitted or received on this interface. Passive interfaces are commonly used with interior gateway protocols (IGPs), such as OSPF and IS-IS, to accomplish a similar result.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="protocols {
    pim {
        interface ge-0/0/0.0 {
            hello-interval 0;
        }
    }
}   "><pre class="notranslate"><code>protocols {
    pim {
        interface ge-0/0/0.0 {
            hello-interval 0;
        }
    }
}   
</code></pre></div>
<h3 dir="auto"><a id="user-content-forwarding-cache-limit" class="anchor" aria-hidden="true" href="#forwarding-cache-limit"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Forwarding Cache Limit</h3>
<p dir="auto">Inet.1 is the table that contains the multicast forwarding cache, which includes all PIM entries as well as MSDP SAs with encapsulated data. You can limit the number of inet.1 entries on the router by configuring a forwarding cache limit. The multicast forwarding cache is added to the forwarding table, which the packet forwarding engine (PFE) uses for unicast and multicast forwarding lookups. The following configuration limits the number of entries in the forwarding-cache to 150,000. After this limit is reached, the router cannot add entries until the forwarding cache drops to 149,000.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="routing-options {
    multicast {
        forwarding-cache {
            threshold {
                suppress 150000;
                reuse 149000;
            }
        }
    }
}"><pre class="notranslate"><code>routing-options {
    multicast {
        forwarding-cache {
            threshold {
                suppress 150000;
                reuse 149000;
            }
        }
    }
}
</code></pre></div>
<h3 dir="auto"><a id="user-content-packet-filtering" class="anchor" aria-hidden="true" href="#packet-filtering"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Packet Filtering</h3>
<p dir="auto">You can use packet filters to deny certain multicast traffic based on values in the IP header. While scoping blocks multicast data packets based on group address, firewall filters block data packets based on values such as source address or protocol. For example, many worms use TCP packets when they probe. There is no legitimate reason for multicast TCP packets, so you can deny them on all routers. Filtering illegitimate multicast traffic such as TCP packets with firewall filters prevents data forwarding as well as state creation of unwanted traffic.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="interfaces {
    fe-0/0/0 {
        unit 0 {
            family inet {
                filter {
                    input mcast-packet-filter;
                }
            }
        }
    }
}
firewall {
    filter mcast-packet-filter {
        term deny-tcp {
            from {
                destination-address {
                    224.0.0.0/4;
                }
                protocol tcp;
            }
            then {
                count mcast-tcp;
                discard;             }
        }
        term allow-everything-else {
            then accept;
        }
    }
} "><pre class="notranslate"><code>interfaces {
    fe-0/0/0 {
        unit 0 {
            family inet {
                filter {
                    input mcast-packet-filter;
                }
            }
        }
    }
}
firewall {
    filter mcast-packet-filter {
        term deny-tcp {
            from {
                destination-address {
                    224.0.0.0/4;
                }
                protocol tcp;
            }
            then {
                count mcast-tcp;
                discard;             }
        }
        term allow-everything-else {
            then accept;
        }
    }
} 
</code></pre></div>
<h3 dir="auto"><a id="user-content-routing-engine-filtering" class="anchor" aria-hidden="true" href="#routing-engine-filtering"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Routing Engine Filtering</h3>
<p dir="auto">Filtering of control traffic to the routing engine (RE) is a critical step in securing routers. Firewall filters on loopback interfaces provide this function. In the case of MSDP, only configured peers should be allowed to send MSDP packets to a router. The following configuration allows only MSDP packets (TCP port 639) to be sent to the RE if the source address is one of its configured MSDP peers. Note that the apply-path command enables this filter to be applied automatically to all peers configured under MSDP, so this filter does not need to be edited when MSDP peers are added or removed.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="interfaces {
    lo0 {
        unit 0 {
            family inet {
                filter {
                    input Protect-RE;
                }
            }
        }
    }
}
policy-options {
    prefix-list MSDP-Peers {
        apply-path &quot;protocols msdp group  peer &quot;;
    }
}
firewall {
    filter Protect-RE {
        term MSDP-Allow {
            from {
                source-prefix-list {
                    MSDP-Peers;
                }
                protocol tcp;
                port msdp;
            }
            then accept;
        }
    }
}"><pre class="notranslate"><code>interfaces {
    lo0 {
        unit 0 {
            family inet {
                filter {
                    input Protect-RE;
                }
            }
        }
    }
}
policy-options {
    prefix-list MSDP-Peers {
        apply-path "protocols msdp group  peer ";
    }
}
firewall {
    filter Protect-RE {
        term MSDP-Allow {
            from {
                source-prefix-list {
                    MSDP-Peers;
                }
                protocol tcp;
                port msdp;
            }
            then accept;
        }
    }
}
</code></pre></div>
<p dir="auto">Use the apply-path command for BGP peers as well. The loopback filter should include all other protocols required to reach the router’s control plane such as PIM, OSPF, Internet Group Management Protocol (IGMP), SSH, Domain Name System (DNS), Internet Control Message Protocol (ICMP), and SNMP.</p>
<h3 dir="auto"><a id="user-content-session-announcement-protocol-storms" class="anchor" aria-hidden="true" href="#session-announcement-protocol-storms"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Session Announcement Protocol Storms</h3>
<p dir="auto">Another common source of trouble on multicast networks has been the Session Announcement Protocol (SAP). SAP is an advertisement protocol used by sources to inform receivers of an available multicast session. Session Description Protocol (SDP) messages are sent over the well-known SAP group, 224.2.127.254, and contain the pertinent information describing a multicast session. Receiving hosts can join this SAP group and learn of available multicast sessions, in a manner similar to viewing a program guide.</p>
<p dir="auto">In the past, it was a common practice on many networks to enable routers to join and listen to the SAP group and cache these SDP messages, instead of merely forwarding this group to interested receivers. With SAP listening enabled, you can view the SAP/SDP cache as seen by the router with the show multicast sessions command. This functionality has been used by operators as a quick and easy way to see whether multicast is working properly on a network. If the router sees a large number of sessions, then multicast is probably working properly on the network; if not, something is amiss and further investigation is needed.</p>
<p dir="auto">Unfortunately, SAP has been a source of many problems. Misbehaving sources have been known to originate malformed SDP packets that have crashed routers and receiving hosts. Additionally, misconfigured SAP servers have been known to multicast the actual data session accidentally over the SAP group, also crashing routers, firewalls, and receiving hosts, which were not expecting high-data-rate flows on this well-known announcement group.</p>
<p dir="auto">These SAP storms are another example of successful attacks upon the multicast infrastructure without even trying. Whatever limited, vague benefits may be gained from enabling routers to cache these messages have proven in practice to not be worth the risk. Thus, it is recommended that routers should not listen to the SAP group or cache these messages. By default, SAP listening is not enabled (set protocols sap) in JUNOS software, so removing this configuration (delete protocols sap) or not configuring it in the first place will ensure that routers will not be affected by SAP storms.</p>
<p dir="auto">Disabling SAP caching on the routers will have no effect on hosts interested in receiving SAP announcements. Routers will continue to happily forward SAP packets blindly to interested receivers. Some have suggested policing 224.2.127.254 to some low value such as 1 Mbps to protect firewalls and hosts as well as downstream routers that still listen to SAP. As mentioned earlier, simply policing control traffic actually makes DoS easier. With a 1-Mpbs policer on all traffic to 224.2.127.254, only one malicious host is needed to send 1 Mbps of bad traffic to the SAP group to engage this policer and block all legitimate SAP traffic, effectively killing the SAP service for all hosts.</p>
<p dir="auto">Note that seeing unwanted traffic on a given multicast group is an inherent weakness of the any-source multicast (ASM) service model. The only real way to prevent traffic from unwanted sources is to use the source-specific multicast (SSM) service model, in which traffic is forwarded only from explicitly requested sources. The SAP group is a particularly attractive target for attack since it can be reliably assumed to have many persistent receivers. In fact, of all the well-known ASM groups, it is probably the best known and most commonly joined group. If you still want to protect receivers and firewalls from unwanted traffic on the SAP group without making it easier to cripple the SAP service, you can monitor the traffic statistics for each source for the SAP group to see whether any particular source is sending too much traffic via the show multicast route group 224.2.127.254 detail command. This monitoring can be automated using a JUNOS software event script. If one source is found to be sending excess traffic, a simple policer can be applied to that source to protect the rest of the SAP service.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="firewall {
    policer sap-policer {
        if-exceeding {
            bandwidth-limit 1m;
            burst-size-limit 10k;
        }
        then discard;
    }
    filter bad-sap-source {
        term one {
            from {
                source-address {
                    10.1.1.1/32;
                }
                destination-address {
                    224.2.127.254/32;
                }
            }
            then policer sap-policer;
        }
    }
}"><pre class="notranslate"><code>firewall {
    policer sap-policer {
        if-exceeding {
            bandwidth-limit 1m;
            burst-size-limit 10k;
        }
        then discard;
    }
    filter bad-sap-source {
        term one {
            from {
                source-address {
                    10.1.1.1/32;
                }
                destination-address {
                    224.2.127.254/32;
                }
            }
            then policer sap-policer;
        }
    }
}
</code></pre></div>
<p dir="auto">More information on event scripts can be found in the JUNOS API and Scripting Documentation for the “Configuration and Diagnostic Automation Guide”.</p>
<h3 dir="auto"><a id="user-content-putting-it-all-together" class="anchor" aria-hidden="true" href="#putting-it-all-together"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Putting It All Together</h3>
<p dir="auto">The following configuration includes all the aforementioned features along with a number of optimizations to maximize reuse of policies among all protocols. It uses the whitelist approach so that only multicast traffic from assigned address space is forwarded (224/8, 232/8, 233/8 and 234/8), and all other multicast traffic is denied.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto" data-snippet-clipboard-copy-content="groups {
    MSDP-Per-Peer-Limit {
        protocols {
            msdp {
                group  {
                    peer  {
                        active-source-limit {
                            maximum 100000;
                            threshold 90000;
                        }
                    }
                }
            }
        }
    }
}
interfaces {
    lo0 {
        unit 0 {
            family inet {
                filter {
                    input Protect-RE;
                }
            }
        }
    }
}
routing-options {
    multicast {
        scope-policy [ SSM-Allow ASM-Allow ];
        forwarding-cache {
            threshold {
                suppress 150000;
                reuse 149000;
            }
        }
    }
}
protocols {
    msdp {
        apply-groups MSDP-Per-Peer-Limit;
        data-encapsulation disable;
        active-source-limit {
            maximum 200000;
            threshold 190000;
        }
        export [ Bogon-Sources ASM-Allow ];
        import [ Bogon-Sources ASM-Allow ];
        source 0.0.0.0/0 {
            active-source-limit {
                maximum 1000;
                threshold 900;
            }
        }
        group EMSDP-Peer1 {
            local-address 1.1.1.1;
            peer 2.2.2.2;
        }           
    }
    pim {
        import [ Bogon-Sources SSM-Allow ASM-Allow ];
        rp {
            bootstrap-import BSR-Deny;
            bootstrap-export BSR-Deny;
            rp-register-policy [ Bogon-Sources ASM-Allow ];
            local {
                address 1.1.1.1;
            }
        }
        interface all {
            mode sparse;
        }
    }
}
policy-options {
    prefix-list MSDP-Peers {
        apply-path &quot;protocols msdp group  peer &quot;;
    }
    prefix-list BGP-Peers {
        apply-path &quot;protocols bgp group  neighbor &quot;;
    }
    policy-statement ASM-Allow {
        term Bogon-Groups {
            from {
                route-filter 224.0.1.2/32 exact;
                route-filter 224.0.1.3/32 exact;
                route-filter 224.0.1.8/32 exact;
                route-filter 224.0.1.22/32 exact;
                route-filter 224.0.1.24/32 exact;
                route-filter 224.0.1.25/32 exact;
                route-filter 224.0.1.35/32 exact;
                route-filter 224.0.1.39/32 exact;
                route-filter 224.0.1.40/32 exact;
                route-filter 224.0.1.60/32 exact;
                route-filter 224.0.2.1/32 exact;
                route-filter 224.0.2.2/32 exact;
                route-filter 224.77.0.0/16 orlonger;
            }
            then reject;
        }
        term ASM-Whitelist {
            from {
                route-filter 224.0.0.0/8 orlonger;
                route-filter 233.0.0.0/8 orlonger;
                route-filter 234.0.0.0/8 orlonger;
            }
            then accept;
        }
        term Deny-Everything-Else {
            then reject;
        }
    }
    policy-statement BSR-Deny {
        then reject;
    }
    policy-statement Bogon-Sources {
        term RFC-1918-Addresses {
            from {
                source-address-filter 10.0.0.0/8 orlonger;
                source-address-filter 127.0.0.0/8 orlonger;
                source-address-filter 172.16.0.0/12 orlonger;
                source-address-filter 192.168.0.0/16 orlonger;
            }
            then reject;
        }
    }
    policy-statement SSM-Allow {
        term SSM-Whitelist {
            from {
                route-filter 232.0.0.0/8 orlonger;
            }
            then accept;
        }
    }
}
firewall {
    filter Protect-RE {
        term MSDP-Allow {
            from {
                source-prefix-list {
                    MSDP-Peers;
                }
                protocol tcp;
                port msdp;
            }
            then accept;
        }
        term BGP-Allow {
            from {
                source-prefix-list {
                    BGP-Peers;
                }
                protocol tcp;
                port bgp;
            }
            then accept;
        }
        term PIM-Allow {
            from {
                protocol pim;
            }
            then accept;
        }
        term IGMP-Allow {
            from {
                protocol igmp;
            }
            then accept;
        }
        term Other-Protocols-Allow {
            from {
                /* Add all other required unicast protocols */
            }
            then accept;
        }
        term Deny-Everything-Else {
            then {
                discard;
            }
        }
    }
}"><pre class="notranslate"><code>groups {
    MSDP-Per-Peer-Limit {
        protocols {
            msdp {
                group  {
                    peer  {
                        active-source-limit {
                            maximum 100000;
                            threshold 90000;
                        }
                    }
                }
            }
        }
    }
}
interfaces {
    lo0 {
        unit 0 {
            family inet {
                filter {
                    input Protect-RE;
                }
            }
        }
    }
}
routing-options {
    multicast {
        scope-policy [ SSM-Allow ASM-Allow ];
        forwarding-cache {
            threshold {
                suppress 150000;
                reuse 149000;
            }
        }
    }
}
protocols {
    msdp {
        apply-groups MSDP-Per-Peer-Limit;
        data-encapsulation disable;
        active-source-limit {
            maximum 200000;
            threshold 190000;
        }
        export [ Bogon-Sources ASM-Allow ];
        import [ Bogon-Sources ASM-Allow ];
        source 0.0.0.0/0 {
            active-source-limit {
                maximum 1000;
                threshold 900;
            }
        }
        group EMSDP-Peer1 {
            local-address 1.1.1.1;
            peer 2.2.2.2;
        }           
    }
    pim {
        import [ Bogon-Sources SSM-Allow ASM-Allow ];
        rp {
            bootstrap-import BSR-Deny;
            bootstrap-export BSR-Deny;
            rp-register-policy [ Bogon-Sources ASM-Allow ];
            local {
                address 1.1.1.1;
            }
        }
        interface all {
            mode sparse;
        }
    }
}
policy-options {
    prefix-list MSDP-Peers {
        apply-path "protocols msdp group  peer ";
    }
    prefix-list BGP-Peers {
        apply-path "protocols bgp group  neighbor ";
    }
    policy-statement ASM-Allow {
        term Bogon-Groups {
            from {
                route-filter 224.0.1.2/32 exact;
                route-filter 224.0.1.3/32 exact;
                route-filter 224.0.1.8/32 exact;
                route-filter 224.0.1.22/32 exact;
                route-filter 224.0.1.24/32 exact;
                route-filter 224.0.1.25/32 exact;
                route-filter 224.0.1.35/32 exact;
                route-filter 224.0.1.39/32 exact;
                route-filter 224.0.1.40/32 exact;
                route-filter 224.0.1.60/32 exact;
                route-filter 224.0.2.1/32 exact;
                route-filter 224.0.2.2/32 exact;
                route-filter 224.77.0.0/16 orlonger;
            }
            then reject;
        }
        term ASM-Whitelist {
            from {
                route-filter 224.0.0.0/8 orlonger;
                route-filter 233.0.0.0/8 orlonger;
                route-filter 234.0.0.0/8 orlonger;
            }
            then accept;
        }
        term Deny-Everything-Else {
            then reject;
        }
    }
    policy-statement BSR-Deny {
        then reject;
    }
    policy-statement Bogon-Sources {
        term RFC-1918-Addresses {
            from {
                source-address-filter 10.0.0.0/8 orlonger;
                source-address-filter 127.0.0.0/8 orlonger;
                source-address-filter 172.16.0.0/12 orlonger;
                source-address-filter 192.168.0.0/16 orlonger;
            }
            then reject;
        }
    }
    policy-statement SSM-Allow {
        term SSM-Whitelist {
            from {
                route-filter 232.0.0.0/8 orlonger;
            }
            then accept;
        }
    }
}
firewall {
    filter Protect-RE {
        term MSDP-Allow {
            from {
                source-prefix-list {
                    MSDP-Peers;
                }
                protocol tcp;
                port msdp;
            }
            then accept;
        }
        term BGP-Allow {
            from {
                source-prefix-list {
                    BGP-Peers;
                }
                protocol tcp;
                port bgp;
            }
            then accept;
        }
        term PIM-Allow {
            from {
                protocol pim;
            }
            then accept;
        }
        term IGMP-Allow {
            from {
                protocol igmp;
            }
            then accept;
        }
        term Other-Protocols-Allow {
            from {
                /* Add all other required unicast protocols */
            }
            then accept;
        }
        term Deny-Everything-Else {
            then {
                discard;
            }
        }
    }
}
</code></pre></div>
<h3 dir="auto"><a id="user-content-summary" class="anchor" aria-hidden="true" href="#summary"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Summary</h3>
<p dir="auto">Multicast enables a broad new set of exciting content and capabilities on the Internet. Along with these new capabilities come new risks. This document describes the most comprehensive set of multicast security features in the industry. By deploying these features with the recommendations described in this document, providers can confidently offer Internet multicast over a hardened, secure infrastructure.</p>
<h3 dir="auto"><a id="user-content-references" class="anchor" aria-hidden="true" href="#references"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>References</h3>
<ul dir="auto">
<li>RFC 6308, Overview of the Internet Multicast Addressing Architecture</li>
<li>RFC 5771, IANA Guidelines for IPv4 Multicast Address Assignments</li>
<li>RFC 4609, Protocol Independent Multicast – Sparse Mode (PIM-SM) Multicast Routing Security Issues and Enhancements</li>
<li>Internet draft draft-ietf-mboned-ipv4-mcast-bcp-02.txt, IPv4 Multicast Best Current Practice</li>
<li><a href="http://www.juniper.net/techpubs/software/junos/" rel="nofollow">JUNOS Software Documentation</a></li>
<li>Interdomain Multicast Routing: Practical Juniper Networks and Cisco Systems Solutions (Addison-Wesley 2002)</li>
</ul>
</article>
  </div>

    </div>

  </readme-toc>

 
