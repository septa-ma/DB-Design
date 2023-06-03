# Understanding User Needs:

**Designing any custom product, whether it’s a database, beach house or so on, is largely a translation process.**
> The first step in the translation process is understanding the user’s requirements.

## Make a Plan:
- **0- Bring a List of Questions:**
    > thinking of questions to ask the customers to get a better idea of the project’s goals and scope.
    - `Functionality`: ***what the system is supposed to accomplish***
        - What should the system do?
        - Why are you building this system? What do you hope it will accomplish?
        - What should it look like? Sketch out the user interface.
        - What response times do you need for different parts of the system? (Typically, interactive response times should be under five seconds, whereas reports and other offline activities may take longer.)
        - What reports are needed?
        - Do the end users need to be able to define new reports?
        - Who are the players? (ties to previous section)
        - Do power users and administrators need to be able to desine new reports?

    - `Data Needs`: ***Knowing what data is needed will help you start defining the database’s tables.***
        - What data is needed for the user interface?
        - Where should that data come from?
        - How are those pieces of data related?
        - How are these tasks handled today? Where does the data come from?

    - `Data Integrity`: ***They help you define some of the integrity constraints that you will build into the database.***
        - What values are allowed in which fields?
        - Which fields are required? (For example, does a customer record need a phone number? A fax number? An email address? One of those but not all of them?)
        - What are the valid domains (allowed values) for various fields? What phone number formats are allowed? How long can customer names be? Addresses? Do addresses need extra lines for suite or apartment number? Do addresses need to handle U.S. ZIP Codes such as 12345? ZIP+4 Codes such as 12345-6789? Canadian postal codes such as T1A 6G9? Or other countries’ postal codes?
        - Which fields should refer to foreign keys? (For example, an address’s State field might need to be in the States table and a CustomerID field might need to be in the Customers table. I’ve seen customers with a big list of standard comments and a Comments field can only take those values.)
        - Should the system validate cities against postal codes? (For example, should it verify that the 10005 ZIP Code is in New York City, New York? That’s cool but a bit trick and can involve a lot of data.)
        - Do you need a customer record before you can place orders?
        - If a customer cancels an account, do you want to delete the corresponding records or just flag
        them as inactive?
        - What level of system reliability is needed?
            - Does the system need 24/7 access?
            - How volatile is the data? How often does it need to be backed up?
            - How disastrous will it be if the system crashes?
            - How quickly do you need to be back up and running?
            - How painful will it be if you lose some data during a crash?

    - `Security`: ***The answers to these questions will help you decide which database product will work best and what architecture to use.***
        - Does each user need a separate password? (Generally a good idea.)
        - Do different users need access to different pieces of data? (For example, sales clerks might need to access customer credit card numbers but order fulfillment technicians probably don’t.)
        - Does the data need to be encrypted within the database?
        - Do you need to provide audit trails recording every action taken and by whom? (For example, you can see which clerk increased the priority of a customer who was ordering the latest iPod and then ask that clerk why that happened.)
        - What different classes of users will there be?
            - ***I often use three classes of users. First, clerks do most of the regular work. They enter orders, print invoices, discuss the latest Oprah around the water cooler, and so forth. Second, supervisors can do anything that clerks can and they also perform managerial tasks. They can view reports, logs, and audittrails; assign clerks to tasks; grant bonuses; and so forth. Third, super users or key users can do everything. They can reset user passwords, go directly into database tables to fix problems, change system parameters such as the states that users can pick from dropdowns, and so forth. There should only be a couple of super users and they should usually log in as supervisors, not as super users, to prevent accidental catastrophes.***
        - How many of each class of user will there be? Will only one person need access to the data at a time? Will there be hundreds or even thousands (as is the case with some Web applications)?
        - Is there existing documentation describing the users’ tasks and responsibilities?

    - `Environment` -> ***Gather information about other systems and processes that the project will replace or with which it will interact.***
        - Does this system enhance or replace an existing system?
            - Is there documentation describing the existing system?
            - Does the existing system have paper forms that you can study?
            - What features in the existing system are required? Which are not?
            - What kinds of data does the existing system use? How is it stored? How are different pieces
            of data related?
            - Is there documentation for the existing system’s data?
        - Are there other systems with which this one must interact?
            - Exactly how will it interact with them?
            - Will the new project send data to existing systems? How?
            - Will the new project receive data from existing systems? How?
            - Is there documentation for those systems?
        - How does your business work? (Try to understand how this project fits into the bigger picture.)

- **1- What the customers' roles are:**
    > The best way to understand the system you need to design and build is to interrogate the customers. I use the rather unfriendly word ‘‘interrogate’’ because, to do the job right, you need much more than a simple chat over tea and crumpets.
    - Learning about the customers’ requirements can be a long and grueling process. It can take days or even weeks of cross-examination, studying existing practices, poring over dusty scrolls and other corporate documentation, and spying on the customers while they do their daily jobs.
    - So when you first start a project, meet the customers. Get to know them and what they do. Even if the problem you are trying to solve is only a small part of their business, get a feel for the overall picture.
    - Sometimes you’ll find unexpected connections that may make your job easier or that may lead to surprising benefits in a completely unrelated area.
    - When you first meet the customers, it usually doesn’t hurt to warn them that you’re going to be a major pest for a while. This can also help you figure out who’s who. Those who are committed to the project and are eager to succeed will take your warning well. Those who are less than dedicated may tip their hands at this point. This idea leads naturally to the next section.


    > ***The following list describes some of the roles that customers (and developers) often play in a project.***
    
    - `Executive Champion`: This is the highest ranking customer driving the project. Often this person
    doesn’t participate in the project’s day-to-day trials and tribulations. The Executive Champion
    will fight for truth, justice, and getting you that extra laptop you need. In the end, the Executive
    Champion must be able to take on any bored super villains or you might be in trouble.
    - `Customer Champion`: This person has a thorough understanding of the customers’ needs. Lesser
    champions may help define pieces of the project but this is the person you run to when the oth-
    ers are unclear. For the purposes of this chapter (‘‘Understanding User Needs’’), this is the most
    important person on the project. This person must have enough time and resources (also known
    as ‘‘people’’) to help you define the project and answer your questions. Ideally this person also
    has enough clout to make decisions when the heroes start bickering over who has to fight Mag-
    neto and who gets to fly the invisible plane.
    - `Customer Representative`: A Customer Representative is someone assigned to answer your
    questions and help define the project. Often these are people who do the day-to-day work of
    your customers’ business. Sometimes they are experts in only parts of the business so you need
    more than one to cover all of the issues.
    - `Stakeholder`: This is anyone who has an interest in the project. Some of these fall into other cat-
    egories such as Customer Champion or Customer Representative. Others are affected by the
    outcome but have no direct say in the design of the system. For example, front-line clerks rarely
    get to toss in their two cents when you design a point-of-sales system. They are like the civil-
    ians whose fate is determined by the battling superheroes and who are easily crushed by falling
    debris and pieces of robot monsters. Though many of them have no direct power over the out-
    come, you should keep them in mind and try to minimize collateral damage. (In a really well-run
    company, these people have their own representatives to watch out for them.)
    - `Sidekick/Gopher`: This is someone who can help you get the more mundane resources you need
    such as conference rooms, airline tickets, donuts, and kryptonite. Though this isn’t a glamorous
    job, an effective Sidekick can make everything run more smoothly. (Sometimes they also pro-
    vide comic relief. On one project, the Sidekick invited everyone out to a huge celebratory lunch
    on him, only to find that the restaurant didn’t take credit cards, so we all had to pitch in. In all
    fairness, though, it could have happened to any of us.)
    - `Short-Timer`: This is someone who is only going to be around for a short while. This may be
    someone who is about to be promoted to a new division, who will retire soon, or who is just
    plain fed up and about to walk. A dedicated short-timer can be a huge asset, particularly those
    who are about to retire and take a lifetime’s worth of experience with them. Others don’t care all
    that much whether the project succeeds or fails after they’re gone. (These are like the red-shirts
    71Part II: Database Design Process and Techniques
    on Star Trek who don’t contribute much. When Kirk says, ‘‘Spock, Bones, and Smith, meet me in
    the transporter room,’’ guess who isn’t coming back?)
    - `Devil’s Advocate`: This is an important role for avoiding groupthink. Left unchecked, some
    groups become irrationally optimistic and can make extremely poor decisions. A Devil’s
    Advocate can help bring the hopeless dreamers back to earth and keep the project realistic...
    as long as the Devil’s Advocate doesn’t get out of hand. The purpose of the Devil’s Advocate
    is to maintain a reality check, not to defeat the entire project. If this person shoots down every
    idea anyone comes up with, you might gently mention that eventually you need to decide on an
    approach and get something done.
    - `Convert`: This is someone who originally is against the project but who you convert to your
    cause. Strangely, both nding and converting this person are usually surprisingly easy, at least
    for bigger projects. If you talk to the disenfranchised stakeholders (the front-line users who have
    no say in the matter), you can usually find some who are dead-set against the project, if for no
    other reason than it represents a change from the way they have always worked. Take one of
    these people who has a fair amount of experience and make him a Stakeholder Representative.
    Get him involved early in the process and take his suggestions very seriously. If you act on
    some of those suggestions, you’ll show that you have the Stakeholders’ interests in mind and
    you’ll win his loyalty. He’ll tell the rest of the Stakeholders and, if all goes well, you’ll have
    more support than you can imagine. And who knows, you may build a better product with this
    person’s input.
    - `Generic Bad Guy`: These range from simple defeatists and layabouts to Arch Super Villains
    actively trying to sabotage the project. Try to identify these people early so you know what
    you’re up against. (On one project, we had a super villain at the Vice Presidential level. We
    also had an Executive Champion at the same level, so we were able to hold our own, but it was
    pretty tough going. It’s easy to get squashed when such heavy-hitters collide.)

- **2- Pick the Customers’ Brains:**
    > Sit down with the Customer Champion and find out what the customers think they need.
    - 

- **3- Walk a Mile in the User’s Shoes:**
    - 
    - 

- **4- Study Current Operations:**
    - 
    - 

- **5- Brainstorm:**
    - 
    - 

- **6- Look to the Future:**
    - 
    - 

- **7- Understand the Customers’ Reasoning:**
    - 
    - 

## Learn What the Customers Really Need:

- 1- Prioritize
    - 
- 2- Verify Your Understanding
    - 
- 3- Write the Requirements Document
    - 
- 4- Make Use Cases
    - 
- 5- Decide Feasibility
    - 
