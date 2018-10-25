# WT-Hackathon-Emergency-Shelter
WindingTree Hackathon in Prague Oct 24th-25th, 2018. 

Team Name: Emergency Shelter
------


Team Members: 
------
Dennison Bertram - dennison@dennisonbertram.com (github: crazyrabbitLTC) 
Skylar Weaver - weaver.skylar@gmail.com (github: skylarweaver)

Project Description: 
------

Across the world, the increasing frequency and intensity of natural and human made disasters in the form of SuperStorms, Earthquakes and war means an increasing number of people are left homeless and in urgent need of emergency shelter. 

Problem:
------

While emergency organizations try to address the most dire of circumstances, they are frequently resource stretched and unable to meet every emergency housing crises on the globe. 

By leveraging the Winding Tree Hotel index, Emergency Shelter seeks to tap into a global pool of volunteers willing to open their doors to assist those in need and solve the problem of emergency housing in emergency situations. 

Solution: 
------

Emergency Shelter is a meta-contract building on-top of the WindingTree Hotel Index. Currently the WindingTree hotel index deploys new instances of Hotel Contracts, complete with a manager address and URI for the data feed. The Emergency shelter Contract takes a novel approach by calling the WindingTree Hotel index to create a new hotel contract instance which is managed, rather than by a "manager" by the Emergency Shelter contract itself. 

By doing so, Emergency Shelter creates "Hotel Instances" to represent emergencies, abtrascting the scope of an entire emergency under one "Hotel Instance" to be indexed and returned by the WindingTree API. Volunteers then submit "Shelters" directly to the Emergency Shelter contract which registeres and associates each "shelter" by "emergency". 

This nature of this abstraction keeps the WindingTree Hotel Index uncluttered while centralizing Emergency offerings and solving several unique challanges:

Emergency "Shelter" accomodations will rarely, if ever, be submitted with metadata that meets the standards of the WindingTree Hotel Index: Shelters will rarely include more than a simple contact info and basic description- no photos, amenities, or swimming pool offerings. 

WindingTree Hotel Index assumes that the hotel manager (the ETH responsible for managing the deployed Hotel Contract) will be an interested and motivated manager. With Emergency Shelter, this job is delegated to the manager of the "Emergency" which will most likely be an interested and motivated individual or Aid organization. In the Hotel Contract URI the "Emergency Manager" can keep relevant information up-to-date in a centrazlied format regarding emergency. 

Following on that, when associating shelters by emergency, the emergency manager can remove from the WindingTree Hotel Index ALL of the availible shelters at the end of an emergency by simply deleting the associated Hotel Contract. As it is the nature of emergencies that individauls feel highly motivated at the outset but then lose interest as time goes on, if individuals were to directly register their shelter with the WindingTree Hotel index, the majority would most likely fail to delete their listing at the end of an emergency which would result in polution of the Hotel Index by zombie listings which would be impossible to delete,alter or manage. 

Difficulties:
------

In the process of developing the Emergency Shelter smart contract, we discovered an problem and suggested a solution to the WindingTree Team. As currently written, the WT-Index contract does not return the address of a Hotel Contract once createn, meaning there is not a secure way to programatically be sure at creation time, the address of the hotel created. This is important to fully implement the functionality of deleting a Hotel Instance contract from the WindingTree Database, in this case, when an emergency has passed, as the smart contract is not aware of the address of the Hotel Contract that it directly manages. 

What we Learned:
------
To create Emergency-Shelter required diving into the WindingTree contracts to understand the shape and format of WindingTree's database. We learned the way in which WindingTree is organized and have some suggestions as to how the system usability and security can be improved. In particualar it would be very helpful in our opinion if WindingTree expands support for 3rd party solidity contracts that can interact with the core WindingTree contract base. This would open up many possiblites for a richer more dynamic smart-contract controlled travel ecosystem. 

Notes:
------
Ropsten Deployment of WindingTree Contracts: 0x933198455e38925bccb4bfe9fb59bac31d00b4d3 (For deployment of EmergencyShelter Contract)

Presentation Slides:
------
https://github.com/crazyrabbitLTC/WT-Hackathon-Emergency-Shelter/blob/master/WT-HACKATHON.pdf
