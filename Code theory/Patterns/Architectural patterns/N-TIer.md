# N-TIer
*or multi-tier architecture*

`This is not so popular anymore but there are a couple of legacy project with this architecture.` 

It splits the application into multiple tiers. A tier is the piece of an application that is responsible for a certain function. 

Tiers can be physically separated. These are not layers. 

A typical example is the **3 tier architecture**.
It consists of three systems:
1. Presentation tier
This contains the user interface and any UI logic. 

2. Business logic tier
Contains the business logic of the problem domain. 

3. Data tier 
Database

These three can be on separate machines or together. 
This allows you to develop and deploy the tiers independently. 
If one thing is modified in one tier, you do not have to touch the other tiers. 
Theoretically the tiers can scale up independently, but the reality is not the same. 

Often one change in one tier requires a change in another tier(s). 
For example a new input filed on the UI requires changes in business logic and database too. 


