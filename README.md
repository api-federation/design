# Overview
Contains requirements and design documents.

Federation of APIs involves creating systems where API consumers and API producers are not directly connected and do not  need to directly trust each other. The aim of this group is to create vendor-neutral open specifications that enable API federation.

![api-federation-design](/media/api-federation-big-picture.png)  <br>
<p align="center">
<i>
Figure 1 - The Big Picture
<br/>
</i>

As shown in Figure 1, the interfaces or their interactions are not yet defined. The different components/players in the API ecosystem are shown in the diagram.

For the federated API system, we need a federated user store. There are systems to onboard users and how to work with them. (A future task is the blockchain aspect - decentralized identity management systems and W3C standards around it). Tenant-based user bases can also be considered where clients of clients can also be onboarded. 

There is a clear distinction between a portal and marketplace. A portal is where one company exposes their APIs whereas a marketplace is where lots of companies together expose those APIs in one place.  For example, each provider creates a portal and takes definitions from that portal and pushes them to a marketplace. It doesn’t have to be that way. We can have a marketplace without those individual portals. Useful to capture both of those aspects. 

Once users subscribe to an API we have to think of ways to get keys issued to those subscribers - to configure the gateway to enable that key and then find the right gateway to add that API. Imagine lots of different gateways where each of those will have only some APIs on them. Those gateways have to take care of aspects such as access control, throttling and monetization policies configured and therefore has to be connected to those policy stores etc. 

There are also aspects such as lifecycles and visibility to be considered; there might be rules about workflows and subscribing to them. We don’t know how to deal with all of that yet. Initially, the way to do it is to put most of it out of scope and start with something simple and move forward. 

There will be instances where the marketplace wants a cut of the revenue, e.g, in cases when the request comes in, the gateway routes the request to the relevant gateway and capture analytics and gets a percentage of the revenue. If the marketplace directs a user to a company’s site and if they buy something, the marketplace gets a share of the revenue. The same can be applied to any billing event in an API marketplace. It will be nice to have a standardized way of sending billing/analytics events to a billing engine and analytics systems from all those gateways so that we can shift that data around. If each API has their own payment strategy we must decide whether we want to capture all those policies or just capture the data and let another system decide what to do. E.g. Zuora - like a broker in between. 

There will be challenges in grouping together APIs into a subscription and so forth. We don't know how we are going down those lines. Must start with minimal pieces. e.g. With CloudEvents, which is just a simple eventing standard, we could try capturing API analytics or billing events and not talk about how they get monetized but just have a standard way of shipping that data and send them to a backend. 

Obviously complexities of portals and marketplaces have to be captured. 
