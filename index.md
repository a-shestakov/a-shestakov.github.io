<img style='float:left; width: 148px; margin-right: 20px;' src='file:///Users/andrey/Desktop/ashest.github.io/ebach.jpg'>

Hi, my name is Andy. 
In real life I'm a lover of music, art and beautiful explanations.
In my work I want to create something that brings people joy.

### Works from 2008 to 2015


On the rise of Russian Facebook clone vk.com I've single-handedly created an app that was installed by *500 000 people*, by virtue of having “viral” properties. I've done the **Flash** programming and all the graphics myself.

The app was called “The fridge door”. Users could go to their friends’ fridges and leave post-it notes or magnets there. These magnets featured memes like the Rage Guy. Apparently in 2008 I invented Facebook-like stickers.

Users could leave a note to a friend who was yet to install the app. This motivated friends to install the app to see what was in the note. Probably because of this, my app went viral. ***I received up to 200 messages from users daily.*** Sadly I was unable to monetize this thing, because at the time I didn't understand how social networks work.

--------------

Then I went to work for a company that provided table linens for events. I fell in love with them because they were perfectionists and didn't allow the tiniest detail to go unnoticed. I've built an **Adobe Flash** app to showcase their products:

![alt text](studio-screen.png  "Logo Title Text 1")

This thing consists of 27 different layers. It even supports varying shadow intensity that depends on item color. In total, this editor requires *about 1000 image files, all of them generated from a 2GB PSB source*. I wrote a suite of **Photoshop scripts** that created images for the main view, the previews and the opacity masks.

![alt text](editor.png  "Editor")

That's when I experienced what it takes to build something beautiful. We painstakingly hunted for pixels that were of slightly wrong color, we fixed opacity masks until everything fit together nicely, and we repeated this process once more when the boss decided to hire another 3D-modeler and start from scratch.

![alt text](matrix.png  "One of the many supporting files")

-----------------------

That's when I should have stopped, but we decided to make a shopping cart for my client's business in **Flash**. They wanted the user to be able to order products right from the “design view” I showed you above, and also create all sorts of other synergies between the site's sections. Doing only the design view in Flash and the other sections in HTML+JS was not an option for them.

So we decided to create *a whole ecommerce solution in Flash*. Now, of course Adobe has created a UI components and layout system specifically for this purpose, called **Flex**, but it was too clumsy and unresponsive for our purposes, so we decided to program everything from scratch.

I implemented, among other things

* a SELECT element
* an IMG element with preloader
* scrolling
* content management tools
* *async command queue system*

Basically for some tasks I needed to recreate parts of HTML, because Flash's HTML and CSS support is really rudimentary. I wrote a whole page of hacks to process **Markdown** into something that looks like **HTML**+**CSS**. It's really absurd what I had to do to make this:

![alt text](unprocessed-markdown.png  "Editor")

look like this:

![alt text](processed-markdown.png  "Editor")

***As a result of this unreasonable perfectionism we had pixel-perfect cross-platform UI, every font we needed, smooth transitions and basically a single-page async app, in 2011.***

On the server side we implemented a custom booking system in **PHP**, because the usual ecommerce solutions don't work for rentals. Most of the backend was done by another developer, but I inherited all of his code later.

***This system allowed my client to process orders in 15 seconds, instead of the industry standard—1 day.***

<video src="file:///Users/andrey/Desktop/ashest.github.io/order.mp4" controls></video>

This thing is used by approximately 1000 returning customers. I imagine they are very happy.

-----------------------

Business was growing rapidly, achieving tens of orders on the same day in summer. All these orders required setup and teardown, so we needed systems for managing workers.

I created, using **Ruby on Rails** and **Angular**, a highly responsive worker management solution. Using it, the manager can assign orders to setup and teardown workers, record and view their performance metrics.

Because it's an internal tool, I can't show it here, but it allows a single manager to manage about 50 simultaneous events, which means:

* receiving customer's order
* making sure the payment is made in time
* manage shipping
* assign orders to workers
* making sure they arrive on time
* record customer feedback and relay it to workers and laundry
* answer any customer question regarding their order in less than 15 seconds

I can't take credit for all of the above, because the interaction design was mostly done by my boss. I just made sure that every feature was implemented as fully as physically possible.

We wanted to eventually make the worker-order assignment not demand our manager's attention. To achieve this, I created an interactive system for workers, where they could pick the most convenient orders for themselves. Of course, there was often a fight over the most convenient and profitable orders. As a solution I created a realtime queueing system that allowed workers to not step on each others' toes. Everyone in the queue knew when their turn is and who is selecting orders now. I tried to create this system using **React**/**Clojurescript**, just for fun, but it turned out to be difficult to debug, so I started from scratch in **Angular**.

![alt text](unused-clojurescript.png  "Unused Clojurescript code")

-----------------------

The table linen rental business was doing fine, but we had all these technologies and a vast amount of know-how in the industry, which we didn't feel we were using to the fullest.

So we decided to sell our byproducts and create our own SaaS solution for event rental companies.

*For the first 5 months we didn't write any code at all, only creating specs and dreaming up database structure.* My boss was not a developer, but he wanted to know all the details of the system, so we created a spec format that could be reasonably easily understood by a non-programmer, yet was highly specific. Our specs were written in Russian, basically 1 test per **Ruby** code line. This way, boss could understand most details of the system without being a programmer.

![alt text](spec.png  "Our specs before being turned into Rspec tests")

In total, our SaaS system has about 1000 tests.

We designed this system completely from scratch. I remember having long discussions about the order of menu items, about names of different things (Phil Karlton was cited frequently), about all kinds of little fiddly things you really don't think about when you are using the app.

> There are only two hard things in Computer Science: cache invalidation and naming things.
> — Phil Karlton

We used Ruby on Rails for backend, and **Angular** + **Coffeescript** + **SASS** for frontend. For storage we used **Postgres**, because Postgres schemas allow to create multitenant applications.

![alt text](db.png  "Some tables are public, other reside inside Postgres schemas")

It was quite a challenge to make the UI elements we designed work everywhere consistently. Every day I felt miserable and stupid, banging my head against some issue with **Angular**-**jQuery** integration or strange JS execution bugs. I felt the need to be a part of a larger team where I could at least hope for some inspiration or advice.

What I did:

* designed  database structure
* programmed controllers and models in **Ruby on Rails**
* set up a web server (**nginx** + **Phusion Passenger**)
* implemented delayed processing of uploaded photos with **delayed_job**
* interfaced our system with third-party APIs for payments, geolocation and Russian morphology
* implemented internationalization
* programmed the UI in **Angular** + **jQuery**
* managed a remote team of CSS wizards
* programmed export of user data to beautiful Excel documents with **AXLSX**

What my boss did:

* graphic design in **Sketch** and interaction design
* functional specifications
* quality assurance

We scored 11 of 12 on the Joel Test (no schedule 😀). We used **Trello** as a planning tool and a bug database. 

In the end we achieved everything we planned regarding this project, albeit at the cost of health and personal relationships. I feel that maybe I can overcome this tendency if I know best industry practices, that's why I'm seeking some sort of team where programmers are a bit more specialized. I still believe that developers should understand the whole stack.

<video src="article.mp4" controls></video>

I am proud of the work I've done for PIFA, it's the most beautiful thing I've ever produced. We received some very kind words such as “this feels like iOS”. I'd say iOS beta.
This system is only 3 months old and it's already used by about 50 companies. You can browse them here: [pifakit.ru](http://pifakit.ru). 

A good example of the site made with PIFA's system is [blomerius.pifakit.ru](http://blomerius.pifakit.ru).

-------------
Other works I did in the meantime (without links):

* a map of tram stops I made for my city using **D3**. It was supposed to allow the authorities to efficiently spend the tram stop renovation budget.
* software for classification of geophysical signals with **Hierarchical Temporal Memory (NuPIC)**

-------------
Stuff I'm interested in personally:

* rational decision making
* generative art (especially recent developments using deep learning, such as StyleNet)
* swing dancing
* optimizing all areas of life


------------
At the moment I'm seeking the next company to fall in love with. It's important for me to feel that my work is helping people.

If you like my style, please contact me via email: [andreyshestakov@icloud.com](mailto:andreyshestakov@icloud.com)