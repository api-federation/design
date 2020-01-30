# Meeting Notes
## Date: 2nd January 2020

### Participants
Ram Grandhi - NN Insurance
Cajetan Rodrigues - TrustYou
Dimuthu Leelarathne - Apigate
Isabelle Mauny - 42Crunch
Nuwan Dias - WSO2
Vimukthi Mayadunne - WSO2
Dakshitha Ratnayake - WSO2

This was Ram’s and Isabelle’s first meeting. Gave a quick overview of what we think API Federation is all about. 

Next, we discussed Cajetan’s use cases of lifecycle reflection and seamless access of APIs deployed in gateways belonging to different owners and distributed across different networks. 

Security concepts, rate limiting, monetizing apis are common but there is no single spec which defines how these should be done. Ram has done something similar with respect to use case 6. Get all possible scenarios from folks in the industry. 

Ram mentioned that RAML has introduced a standard called superface.ai and it seems to have an overlap of what we are trying to do. In that, API client and producers don’t want to have anything in between like a gateway in between and communicate directly. Get some thoughts from that perspective as well since that’s where the industry is heading. 

Ram has one public API entry point in their company - not diff gateways from vendors. Where small parts of the company want to test their stuff with a subset of users for stable APIs or stable user bases which divides them with a production customer base - pure paying customers and a user pool of pilot customers. Gives them an opp to have multiple user pools - AWS cognito, Azure AD, Salesforce Active Directory. Today their company is using SAML2 as the only opp between API M and the userpool for this but it will be good to have a vendor-neutral spec to embrace these user pools. Will think more and get back to us. 

SEND MORE PULL CASES!

Narrow it down and create a scope document and create the architecture. 
We have already come up with a spec based on Open API spec
By looking at what we have done we need to reuse what we done. So identify a scope. Now that we have about 6 use we can start designing the architecture. 

Nuwan: Come up with user stories and then create a level 0 architecture. 


Seamless API federation aspect: Discussion - 
What we had in mind was to have  separate gateways but a unified portal to see all info of APIs even though they reside in different gateways. Keep the APIs in their respective gateways without having a proxy or a duplication. 
Nuwan: Let’s see what we can introduce into the spec. How a single lifecycle change should be reflected. So introduce a state in the spec. SImilarly we need to come up with stuff to the spec to use in the spec. 

Ram's suggestion. It would make a lot of sense if we can use a whiteboarding.

Unified catalog component and the independent vendor components. There can be 2 types of events that would be coming in and out. One is an announcement - state change event. There is also the info specific to API info e.g. - throughputs and other info that cannot be changes. Not sure if Swagger 3.0 is the only option. Are we open to other standards? Because it also restricts creativity. Let’s start with the block diagram and see what interactions happen during design time and what happens during run time. 

Isabelle: Have we already reached out to the Open API guys? 

Cajetan: Before the architecture is presented we would present the scope first and figure out what is in scope and out of scope and have a clear seggregation. How long are we planning on keeping the use case discovery phase alive? Is there a plan to enforce a cut off time for the use cases? Nuwan: Keep it open for the time being, so that everyone gets a chance to present their ideas. 

Conclusion: Come up with a scope based on what we have so far. Once we are done with a few iterations we can close the call for use cases. 

TODO - Scoping Exercise
Identify the flows and metrics. 
Once a flow is idenitified, determine the impact of a use case and the feasibiity of use cases should also be documented. e.g., even though one use case is desirable, the implementation could be difficult. 

Side note: 
Isabelle: have you guys looked at this ? http://apisjson.org - This was started by Kin Lane - I am sure he would be happy to collaborate to the API federation effort.

### Participants:

------------------------------
## Date: 19th December 2019

### Participants:

Alex de Groot - Xpirit<br>
Cajetan Rodrigues - TrustYou<br>
Nuwan Dias<br>
Vimukthi Mayadunne<br>
Dakshitha Ratnayake

Gave an update to Cajetan and Alex about use cases and discussed the use cases contributed by the members. 

Alex pointed out that the Federated Publisher use case (UC-2) is a centralization approach which could hinder agile processes adopted by separate teams if a single process is introduced to publish APIs to gateways. While teams need to use their own tools and technologies, UC-2 was conceptualized based on customers who wanted tools to create a good API publishing experience. So, the idea is to let teams use their own tools but if they want to use the publisher tool, they can do that too. 

API consumer shouldn't have to worry about who the provider of the API is and what the functionality behind the scenes is. They should just be allowed to access APIs via a single interface. For example, in the API discovery user case that provides a catalog, if the user has to access the APIs via a different gateway, the experience will not be seamless from the perspective of the user. However, what is needed at the end of the day is an API portal through which users access APIs and the underlying access mechanisms are abstracted and a unified experience should be provided to the user irrespective of where the API resides. This inherently falls under the purview of API Federation. 

We also discussed the possibility of tenants bringing in their own user pools and authenticating them against their IDPs. It could be both user stores and IDPs. We also can think of it as identity federation where a central IDP can federate with IDPs associated with other gateways. The central IDP can send an authentication request for a user to the relevant IDP and once the user is authenticated, the central IDP can issue tokens to the user. More brainstorming required for this use case. 

Furthermore, authorization requirements were also discussed. We can use scopes for this purpose and bind scopes to a resource/token. A scope is an abstraction and the underlying implementation could vary based on various factors: scopes can be bound to user roles, XACML policies etc. Should authorization be a part of federation initiative? 

What about lifecycles? How can lifecycle stages be preserved across gateways? 

What should be federated: API meta data concerning basic API info, policies, key management, analytics.
 

### TODO
Work on a scope document. 

------------------------------------------------
## Date: 12th December 2019

### Participants:

Flavio Geraldes - Lufthansa<br>
Dimuthu Leelarathne - Apigate<br>
Paul Fremantle - WSO2<br>
Vimukthi Mayadunne - WSO2<br>
Dakshitha Ratnayake - WSO2<br>

Flavio has met Paul and Nuwan at APIdays Paris. 
Isabelle from 42 Crunch will also be invited to the group as she has also expressed interest. 
A couple of other folks have also expressed interest in joining the group and Paul will have a chat with them.

We then discussed logistics. 

The Google group is public and anyone can send a request to subscribe to the group api-federation@googlegroups.com.
The Github organization is  https://github.com/api-federation.
There are two repositories for the moment: design and spec.
The design repo will have design documents, minutes (call notes) of the bi-weekly meetings and user stories. The initial version of the spec will also be contained in the design repo and will be moved to the spec repo after review iterations. 
With respect to meeting notes, <b>participants should mention if certain discussion items should be off the record e.g. customer names,  as most of it will be recorded in the meeting notes</b>. 

We then collectively agreed upon a definition of what we mean by API Federation. We can always iterate on this. This is what we have at the moment:<br> <b>'API Federation' involves creating systems where API consumers and API producers are not directly connected and do not need to directly trust each other.’</b><br>

We also agreed on the Group Charter:<br> 
<b>‘The aim of this group is to create vendor-neutral open specifications that enable API federation.’</b><br>

### Next Steps:
We will have to dig deeper and identify a set of different areas that need specifications. We don’t have to work on all of these areas at the same time but prioritize these areas. 

Even though we discussed covering various aspects like listing or publishing APIs in a common marketplace, on-boarding process and federated identity model to connect to gateways and key managers, and more complex scenarios such as monetization and policy enforcement, Dimuthu suggested that we start off with the business use cases and see how API Federation can solve business problems. 
Everyone agreed that it would be easier to make these connections if we address the business problems. 

So, we decided that the group members should contribute user stories/business use cases. They can be emailed to the group or submitted through pull requests to the design repo under user stories as separate markdowns. They will be reviewed separately. 

An example user story Paul elaborated is as follows: 
Assume a government and its various departments. Each government department runs its own API management infrastructure. However, the central government has decided to have one single API marketplace to make those APIs visible and subscribable. So each department will continue to have its own API management solutions but now also have to publish to the central hub.  The subscribers of the central hub should be able to subscribe to them (find their gateways and get the keys). 

The next meeting will be held on Thursday the 19th December at 3PM GMT. We will be primarily going over the user stories and prioritizing them. 

------------------------------------------------

## Date: 22nd November 2019

### Participants:

Alex de Groot - Xpirit<br>
Flavio Geraldes - Lufthansa<br>
(Alex and Flavio attended Paul’s talk at Nordic APIs.)<br>
Dimuthu Leelarathne - Apigate<br>
Paul Fremantle - WSO2<br>
Nuwan Dias - WSO2<br>
Vimukthi Mayadunne - WSO2 <br>
Dakshitha Ratnayake - WSO2<br>

This was the kickoff meeting.
The agenda was as follows:<br>
- Introductions
- High level thinking and requirements 
- Work done so far
- Working approach (meetings, mailing list, github project, output)
- Demonstration

This is all about creating federating APIs across different systems and creating an ecosystem of APIs.  

This kickoff  meeting was to introduce ourselves and figure out our working plan. We will conduct a future session to talk about requirements in detail, create an ontology of all the different components in place, how they should work and what is in and out of scope.
 
Please find some key areas discussed in the Appendix section. 

Vimukthi showed a demo which shows how a swagger file created via the WSO2 API Manager can be pushed to different API management solutions. We have also used the Open API Specification to capture information pertaining to several scenarios. 

### Next Steps:

- Create an open group. Invite anyone to join and create a Google groups mailing list for communication.
- Use either Github or Google docs  for meeting minutes and specs. 
- Bi-weekly meetings (via Zoom) - Thursdays 4PM EU time/ 3 PM UK time
- Come up with an agenda for the next meeting

### Appendix: 
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


