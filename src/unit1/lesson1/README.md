Unit 1, Lesson 1 – Getting Started
==================================

It’s time to start learning RavenDB 4. Even if you know previous versions of
RavenDB, you will probably get good surprises and learn some new tricks in this
bootcamp.

In this lesson, you will learn how to install and start using it on your
computer.

Getting RavenDB up and running
------------------------------

In this bootcamp, we are assuming that you are a developer trying to get an
instance of RavenDB up and running on your computer. We will not discuss how to
deal with production scenarios (at least, for a while). If you need information
about how to setup RavenDB for production, we recommend you to read the online
documentation.

### Exercise: Running on the live demo instance

Don’t want to download bits and bytes? No problem!

Without installing anything, you can point your browser to
<http://live-test.ravendb.net> and access the public demo instance that we have
available.

Using the live demo version is useful for quick checks and verifications, but it
isn’t meant for anything more serious than that. Obviously, all data in the live
instance is public, and there are no guarantees about availability. We use this
instance to try out the latest versions, so you should consider that.

### Exercise: Running on Docker

Using docker is a fast way to start using RavenDB on your computer. If you have
Docker installed, all you need to do is run the following command:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker run -e UNSECURED_ACCESS_ALLOWED=PublicNetwork -p 8080:8080 ravendb/ravendb
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Docker will now get the latest RavenDB version and spin up a new container to
host it. Note that we run it in developer mode, without any authentication.

### Exercise: Running on Windows, Linux or MacOS

To set up RavenDB on Windows, Linux or MacOS, you will need first to download it
from <http://ravendb.net/download> (selecting the right distribution for your
platform). You will get a compressed file that you can extract to a folder of
your preference.

Go ahead and do it, we can wait.

Done?! Now, all you need to do is run the `./Server/Raven.Server.exe` located
in RavenDB folder. This will start a console application in interactive mode,
inside a console application. Also, the script will open your browser and start
the RavenDB Management Studio

-   Put RavenDB image here

By default, RavenDB will try to use `http://localhost:8080` as its endpoint.
But, if something is already using port 8080, RavenDB will fail to start and
give you an “address in use” error (more specifically, EADDRINUSE). In this
case, you will need to configure RavenDB (You can [follow the documentation to
get it
done](https://ravendb.net/docs/article-page/4.0/csharp/server/configuration/configuration-options)).

Running RavenDB for the first time, you will need to do a little setup. You just
need to answer the questions to get it done.

Your first database
-------------------

RavenDB Management Studio was completely re-designed. It’s looking beautiful,
and we did a lot of work to make it simpler and easier than ever.

![](media/d1ff71a639f63e04488b56706a91f423.png)

### Exercise: Creating a Database

To create your first database:

1.  Select the `Database` option in the left panel.

2.  Click on the `New Database` button.

3.  Type a name for the new database (we recommend Northwind, in this lesson)

4.  Click on the `Create` button

Congratulations! You just created your first RavenDB database... but, it is
empty.

![](media/3f7ec9fbf9d626ebbe905e7a589e81ed.png)

### Exercise: Loading sample data

For learning purposes let’s load some sample data into our database.

1.  Select `Databases` on the left panel
2.  In the right panel, click on the name of the database you just created (that
   is empty for a while)
3.  In the left panel, click on `settings`, and then `Create Sample Data`

![](media/26de5d4d9b2cf6a0f8867677aa776b45.png)

4.  Click on the big `Create` button

> The Northwind database is the sample database that came with SQL Server;
it has been used for decades as the sample database in the Microsoft
community. We chose this database as our sample data because it is likely
already familiar to you in its relational format.

Going to the `Documents` session (left panel), you will see that we created a
lot of documents for you.

![](media/3f24692d124b788b08cb11e49d8fb66f.png)

Exploring the database
----------------------

That's great. We just launched RavenDB in interactive mode, created our first
database and loaded some sample data. But, wait! It looks remarkably similar to
what you see in a relational database. Right? The data is shown in a grid format
with the tables on the left.

If you click on any "record", you will start to see the NoSQL magic!

![](media/4bcc55018cd05b354a0d98c3ce7bcfb7.png)

Yes! All RavenDB data is stored as JSON.

Understanding the `Document` concept
------------------------------------

Using the `Go to document` feature (the text box in the Studio toolbar), go to
the document `orders/101-A`.

```json
{
    "Company": "companies/86",
    "Employee": "employees/4",
    "OrderedAt": "1996-11-07T00:00:00.0000000",
    "RequireAt": "1996-12-05T00:00:00.0000000",
    "ShippedAt": "1996-11-15T00:00:00.0000000",
    "ShipTo": {
        "Line1": "Adenauerallee 900",
        "Line2": null,
        "City": "Stuttgart",
        "Region": null,
        "PostalCode": "70563",
        "Country": "Germany"
    },
    "ShipVia": "shippers/2",
    "Freight": 0.78,
    "Lines": [
        {
            "Product": "products/1",
            "ProductName": "Chai",
            "PricePerUnit": 14.4,
            "Quantity": 15,
            "Discount": 0.15
        },
        {
            "Product": "products/23",
            "ProductName": "Tunnbröd",
            "PricePerUnit": 7.2,
            "Quantity": 25,
            "Discount": 0
        }
    ]
}
```

It is very different from what we're used to in relational databases.

>   \> A document is a self-describing, hierarchical tree data structure which
>   can consist of maps, collections, and scalar values.

Being practical, RavenDB database stores documents, which are plain JSON
formatted data. So, we can aggregate related information into a common object,
as in the case of the `ShipTo` property which has all the shipping information.

In a Document Database, documents are organized in collections.

Understanding the `Collection` concept
--------------------------------------

The collections provide a good way to have some level of organization. For
example, documents holding customers data are very different from documents
holding products information, and you want to talk about groups of them. RavenDB
allows for a document to be stamped with a string value that will be evidence of
its type (like "Customers" and "Products").

Note that documents that are in the same collection can have a completely
different structure, which is fine because RavenDB is schema-less.

Exercise: Exploring the Northwind collections
---------------------------------------------

1.  Open the RavenDB Management Studio at <http://localhost:8080>
2.  Open the Northwind Database
3.  In the `Documents` session, explore all the collections.

The user interface is pretty simple. It is important to you to get familiar with
it. We strongly recommend you to try to create your documents, edit and so on.
You can create another database, load the sample data (if you want).

Don’t be afraid. Test your self!

Great job! Onto Lesson 2!   
-------------------------

Awesome! You have just completed your first lesson. It was a big one. 

If you are getting started with document databases and want to learn more about
document modeling, we recommend you to watch this [Ayende’s
talk](https://www.youtube.com/watch?v=FY0BiZaJwL4).


**Let's move onto** [Lesson 2](../lesson2/README.md) **and start querying.**
