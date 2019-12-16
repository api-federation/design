# Meeting Notes
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

Next step- 
We will have to dig deeper and identify a set of different areas that need specifications. We don’t have to work on all of these areas at the same time but prioritize the areas. 

Even though we discussed covering various aspects like listing or publishing APIs in a common marketplace, on-boarding process and federated identity model to connect to gateways and key managers, and more complex scenarios such as monetization and policy enforcement, Dimuthu suggested that we start off with the business use cases and see how API Federation can solve business problems. 
Everyone agreed that it would be easier to make these connections we need to think about if we address the business problems. 

So we decided that group members should contribute user stories/business use cases. They can be emailed to the group or through pull requests to the design repo under user stories as separate markdowns. They will be reviewed separately. 

An example user story Paul elaborated is as follows: 
Assume a government and its various departments. Each government department runs its own API management infrastructure. However, the central government has decided to have one single API marketplace to make those APIs visible and subscribable. So each department will continue to have its own API management solutions but now also have to publish to the central hub.  The subscribers of the central hub should be able  to subscribe to them (find their gateways and get the keys) . 

The next meeting will be held on Thursday the 19th December at 3PM GMT. We will be primarily going over the user stories and prioritizing them. 


## Date: 22nd November 2019

### Participants:

Alex de Groot - Xpirit
Flavio Geraldes - Lufthansa
(Alex and Flavio attended Paul’s talk at Nordic APIs.)
Dimuthu Leelarathne - Apigate
Paul Fremantle - WSO2
Nuwan Dias - WSO2
Vimukthi Mayadunne - WSO2 
Dakshitha Ratnayake - WSO2

This was the kickoff meeting. 
The agenda was as follows:
Introductions
High level thinking and requirements 
Work done so far
Working approach (meetings, mailing list, github project, output)
Demonstration

This is all about creating federating APIs across different systems and creating an ecosystem of APIs.  

This kickoff  meeting was to introduce ourselves and figure out our working plan. We will conduct a future session to talk about requirements in detail, create an ontology of all the different components in place, how they should work and what is in and out of scope.
 
Please find some key areas discussed in the Appendix section. 

Vimukthi showed a demo which shows how a swagger file created via the WSO2 API Manager can be pushed to different API management solutions. We have also used the Open API Specification to capture information pertaining to several scenarios. 

Next Steps:

Create an open group. Invite anyone to join and create a Google groups mailing list for communication.
Use either Github or Google docs  for meeting minutes and specs. 
Bi-weekly meetings (via Zoom) - Thursdays 4PM EU time/ 3 PM UK time
Come up with an agenda for the next meeting

Appendix: 



Paul’s big picture - Not trying to say what the connections or interfaces are. Hasn’t gotten all the interactions here either. It’s about what the different components/players in the API ecosystem are and then we can talk about what sort of connections have to be drawn. 

For the federated API system, we need a federated user store. It’s a given. There are systems to do that to onboard users and how to work with them. (A future task is the blockchain aspect - decentralized identity management systems and W3C standards around it.) 

Alex - Federated user bases and also tenant based user base should be considered where their clients can also be onboarded. 

Paul distinguishes between a portal and marketplaces. A portal is where one company exposes their APIs whereas a marketplace is where lots of companies together expose those APIs in one place.  For example, each provider creates a portal and takes definitions from that portal and pushes them to a marketplace. It doesn’t have to be that way. We can have a marketplace without those individual portals. Useful to capture both of those aspects. 

Obviously there are also complexities like lifecycles, visibility, there might be rules about workflows and subscribing to them. We don’t know how to deal with all of that yet. Maybe at fIrst, the way to do it is to put most of it out of scope and start with something simple and move forward. 
And then once users subscribe to an API we have to think of ways to get keys issued to those subscribers - to configure the gateway to enable that key and then find the right gateway to add that API. Imagine lots of different gateways where each of those will have only some APIs on them. Those gateways have to take care of aspects such as access control, throttling and monetization policies configured and therefore has to be connected to those policy stores etc. 

Suppose the marketplace wants a cut of the revenue. If the marketplace directs a user to a company’s site and if they buy something, the marketplace gets a share of the revenue. Same goes to the  billing event in an API marketplace. It will be nice to send a standardized way of sending billing/analytics events to a billing engine and analytics systems from all those gateways so that we can shift that data around.


Alex - What about autonomous business capabilities?Every API has their own payment strategy. Sometimes by users or customers. We must decide whether we want to capture all those policies or just capture the data and let another system decide what to do. E.g. Zuora - like a broker in between. 


Dimuthu -  Apigate bundles together APIs and share the revenue. Apigate exposes an API from the marketplace. When the request comes in the Apigate gateway routes the request to the relevant gateway and capture analytics and gets a percentage of the revenue. 

Paul- 
There will be challenges in grouping together APis into a subscription and so forth. We don't know how we are going down those lines. Must start with minimal pieces. e.g. there is a standard called cloud events which is just a simple eventing standard; we could try capturing API analytics or billing events in cloud events and not talk about how they get monetized but just have a standard way of shipping that data and send them to a backend. 

Paul - 
Obviously complexities of portals and marketplaces have to be captured. WSO2 has various tools and backends. For example we have a portal, we have a traffic management component etc. we have some components not in the picture. 

We have customers using not just us but Apigee, Mule etc. because they are big and there are 3 or 4 different groups with different API management solutions. They want to produce a single marketplace because they want to see everything in one place. 


