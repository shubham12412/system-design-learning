https://learning.oreilly.com/library/view/cassandra-the-definitive/9781491933657/ch05.html

### Defining Application Queries
Let’s try the query-first approach to start designing the data model for our hotel application. The user interface design for the application is often a great artifact to use to begin identifying queries. Let’s assume that we’ve talked with the project stakeholders and our UX designers have produced user interface designs or wireframes for the key use cases. 

#### We’ll likely have a list of shopping queries like the following:

Q1. Find hotels near a given point of interest. \
Q2. Find information about a given hotel, such as its name and location. \
Q3. Find points of interest near a given hotel. \
Q4. Find an available room in a given date range. \
Q5. Find the rate and amenities for a room. \


#### TIP:
NUMBER YOUR QUERIES \
It is often helpful to be able to refer to queries by a shorthand number rather that explaining them in full. The queries listed here are numbered Q1, Q2, and so on, which is how we will reference them in diagrams as we move throughout our example.

Now if our application is to be a success, we’ll certainly want our customers to be able to book reservations at our hotels. This includes steps such as selecting an available room and entering their guest information. So clearly we will also need some queries that address the reservation and guest entities from our conceptual data model. Even here, however, we’ll want to think not only from the customer perspective in terms of how the data is written, but also in terms of how the data will be queried by downstream use cases.

Our natural tendency as data modelers would be to focus first on designing the tables to store reservation and guest records, and only then start thinking about the queries that would access them. You may have felt a similar tension already when we began discussing the shopping queries before, thinking “but where did the hotel and point of interest data come from?” Don’t worry, we will get to this soon enough. 

### Here are some queries that describe how our users will access reservations:

Q6. Lookup a reservation by confirmation number. \
Q7. Lookup a reservation by hotel, date, and guest name. \
Q8. Lookup all reservations by guest name. \
Q9. View guest details. \


We show all of our queries in the context of the workflow of our application in Figure 5-3. Each box on the diagram represents a step in the application workflow, with arrows indicating the flows between steps and the associated query. If we’ve modeled our application well, each step of the workflow accomplishes a task that “unlocks” subsequent steps. For example, the “View hotels near POI” task helps the application learn about several hotels, including their unique keys. The key for a selected hotel may be used as part of Q2, in order to obtain detailed description of the hotel. The act of booking a room creates a reservation record that may be accessed by the guest and hotel staff at a later time through various additional queries.

![Hotel-application-queries.png](./img/Hotel-application-queries.png)
