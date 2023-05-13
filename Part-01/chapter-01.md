# Goals of Effective Database Design

# 1- what are Goals of Effective Database Design?

- Building an application is often compared to building a house or skyscraper. You probably wouldn’t
start building a multibillion dollar skyscraper without a comprehensive design that is based on
well-established architectural principles. Unfortunately software developers often rush off to start coding as soon as they possibly can. Coding is more fun and interesting than design is. Coding also lets developers tell management and customers how many lines of code they have written so it seems like they are making progress even if the lines of code are corrupted by false assumptions. Only later do they realize that the underlying design is awed, the code they wrote is worthless, and the project is in serious trouble.

- Few parts of an application’s design are as critical as the database’s design. The database is the repository of the information that the rest of the application manages and displays to the users. If the database doesn’t store the right data, doesn’t keep the data safe, or doesn’t let the application and the data it needs, then the application has little chance for success. Here the GIGO (GarbageIn, Garbage Out) principle is in full effect. If the underlying data is unsound, it doesn’t matter what the application that uses it does; the results will be suspect at best.

- For example, imagine that you’ve built an order tracking system that can quickly fetch information about a customer’s past orders. Unfortunately every time you ask the program to fetch a certain customer’s records it returns a slightly different result. Though the program can nd data quickly, the results are not trustworthy enough to be usable.

- Or imagine that you have built an amazing program that can track the thousands of tasks that make
up a single complex job such as building a cruise liner or passenger jet. It can track each task’s state
of completion, determine when you need to order new parts for them to be ready for future phases of
construction, and can even determine the present value of future purchases so you can decide whether
it is better to buy parts now or wait until they are needed. Unfortunately the program takes hours to
recalculate the complex task schedule and pricing details. Though the calculations are correct, they are so slow that users cannot reasonably make any changes. Changing the color of the fabric of a plane’s seats or the tile used in a cruise liner’s hallways could delay the whole project.

- Or suppose you have built an efficient subscription application that lets customers subscribe to your
company’s quarterly newsletters and data services. It lets you quickly and and update any customer’s
subscriptions and it always shows the same values for a particular customer consistently. Unfortunately, when you change the price of one of your publications you and that not all of the customers’
records show the updated price. Some customers’ subscriptions are at the new rate, some are at the old
rate, and some seem to be at a rate you’ve never seen before. (This example isn’t as far-fetched as it
may seem. Some systems allow you to offer sale prices or special incentives to groups of customers, or
they allow sales reps to offer special prices to particular customers. That kind of system requires careful
design if you want to be able to do things like change standard prices without messing up customized
pricing.)

- Poor database design can lead to these and other annoying and potentially expensive scenarios. A good design creates a solid foundation on which you can build the rest of the application.

- Experienced developers know that the longer a bug remains in a system the harder it is to find and
fix. From that it logically follows that it is extremely important to get the design right before you start
building on top of it.

- Database design is no exception. A flawed database design can doom a project to failure before it has
begun as surely as ill-conceived software architecture, poor implementation, or incompetent programming can.

# 2- What is a database?

A database is a tool that stores data, and lets you create, read, update, and delete the
data in some manner.