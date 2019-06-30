# **Website Design Proposal**

![Skillage I.T](.\logos\logo.png "Skillage I.T &copy;")

**Address:**  
4 Collings Street Melbourne 3000  
**Email:**  
mikeymikemike@Skillageit.su  
**Phone:**  
0412345678  

## **Website Proposal for:**

### *Tiger Paws*

**Address:**  
7 Collings Street Melbourne 3000  
**Email:**  
businessmanager@tigerpaws.com.au  
**Phone:**  
1300IMPAWSIBLE

## Introduction

Tiger Paws a botique stuffed toy retail outlet, has requested a website consisting of a **Home Page**, a **Catalog** page, a **Discussion** page, and a **Communication** page. This proposal is written to Tiger Paws to outline their needs and how we at Skillage I.T can ensure they are met within the guidelines mentioned in this document.

Skillage I.T has a strong background of building websites and offering I.T solutions, including but not limited to:

1. **Online Backups**. We provide server space and Always Online    connections so businesses may backup their important data offsite.

2. **Online Payment Processing**. Skillage I.T provides EFT services, helping to process payments and manage all communications with payment providers and the Banks.

3. **Online Shopping**. We provide a simple shopping service where our clients can list their items for sale on our Web Portal and their customers can browse, purchase and review utilizing our state of the art infrastructure.

4. **Web Site Design & Hosting**. Most importantly in Tiger Paws' case, we offer a complete package of ***Website Design, Development, Testing, and Hosting*** on our cloud infrastructure.

*[Problem Statement](#Problem-Statement)  
[Goals/proposed solutions](#Goals/proposed-Solutions)  
[Standard package breakdown](#Standard-package-breakdown)  
[Extras](#Extras)  
[Testimonials](#Testimonials)  
[Next steps](#Next-steps)  
[Terms and conditions & signature page](#Terms-and-conditions-&-signature-page)*  

## Problem Statement

Lately Tiger Paws has noticed some drastic loss in revenue, and after surveying their customers, they've found that it is due to one main issue *"Time"*. This is due to the commitments of a modern day family and the fact that it is very hard to find time out of a busy family schedule to go stuffed toy shopping.

This loss of revenue is also due to the fact the Tiger Paws does not have an online presence. In our experiences we've found that stores without an online presence go out of business generally very quickly unless we can get them a website designed by specialist I.T professionals.

The user base is found to be parents in their 20s with some grandparents and great grandparents in the mix. It seems the older generation has been with Tiger Paws for a long time, so we will need to ensure catering for the accessability of the older generations.  

## Goals/proposed solutions

As per the conversation with Tiger Paws, to address these concerns we will need to design a website that contains the following:

* **A Home Page** - Where people can see specials that they have along with any announcements they would like the community to know about. This needs to incorporate a new logo designed by Skillage I.T.

* A **Catalog Page**  - Showing the different stuffed toys they have available for purchase. Needs to be an online catalog and not a sales focussed shopping page.

* A **Discussion Page**  - Where Tiger Paws members can post and have discussions with other community members.

* A **Communication Page**  - This page will allow users to get in touch with Tiger Paws via email with any questions, and the page should also host their general contact info.  

Tiger Paws have advised that the site does not need to be responsive in design (mobile friendly), but we will do this at no extra cost for two reasons:

1. Parents in their 20's use mobiles more than they use normal computers.

2. Eventually the site will need to be responsive (as most if not all websites are these days), so instead of having to rewrite the website in the future we will ensure it is responsive now and make it easier to upgrade/update in the future.

As we are expecting elderly/disabled users accessing the site, we will need to ensure that the site is compliant with the **Web Content Accessibility Guidelines Version 2.0** (WCAG) AA standard.

## Standard package breakdown

The site will be designed with scalability in mind, ensuring that during busy times we can keep up with demands, and during quite times we can scale back to ensure low cost to the owners of Tiger Paws.  

Below you will see a network diagram of the proposed website infrastructure.  

![Tiger Paws Infrastructure](.\screens\tiger-paws-infrastructure.png "Tiger Paws Infrastructure")

### Frontend Architecture and Frameworks:

Facing the internet will be a **Firewall** and **Load Balancer** ensuring security and controlling the traffic flow to the **Reverse Proxy**.This will be managed internally by Skillage I.T and will also include a **Web Application Firewall** or **WAF** as part of the package. This is for security and to make sure we divert the traffic depending on the demand at the time.

The **Reverse Proxy** will be controlled by the Load Balancer. Sending traffic to the **Web Server** that is not already under load or a brand new instance of a **Web Server**, if the need be. The **Reverse Proxy** software will be **NGinx**.

Behind the Reverse Proxy, **Web Services** running with the traffic going to each depending on what the **Load Balancer** and **Reverse Proxy** decide at the time.

Skillage I.T's **Web Services** are designed to be quite malleable, with the opportunity to scale either horizontally (adding more machines to process the work load) or vertically (adding more resources like CPU power, or RAM). Depending on the workload and Tiger Paw's budget, we can add either or both, with the ability to scale back as needed.

To begin with we recommend running two **Web Servers** to handle traffic, allowing for concurrent processing and giving a bit of redundancy incase of hardware failure.

The **Web Servers** will be running Nginx in Alpine Linux containers.
Containerizing our applications ensures security and agility as we scale depending on the workload.
Using Alpine Linux helps to make sure the container size stays as small as possible and gives the user the best possible experience.

Using Nginx gives us the ability to easily handle high amounts of workload and integrate seamlessly with other Frameworks.

Nginx also give us the ability to take advantage of **Google's PageSpeed** project. Rewriting & Minifying HTML,CSS,Javascript, among many other things will give the user a great experience and help to keep down costs, when it comes to optimization.

The front end of the site will be run and developed using the following Frameworks:

HTML: Will be written with **Bootstrap** - this will bring a familiar look o the user and will shorten development time as we do will not need to create our own components from scratch.

CSS: Will be written with the HTML using **Bootstrap**, easy to use and familiar to the user. **Bootrap** also helps to ensure a responsive design.

JS: Javascript and other CSS, and HTML elements will be written using a Framework called **Svelte**.

The **Svelte** Framework is light-weight and extremely fast. **Svelte** updates only the needed part of the DOM and does not create a virtual DOM before updating a webpage, unlike frameworks such as React and Vue.

After the site has been written we will then compile and bundle everything into a small package using a static module bundler called **webpack**. Using webpack means that we will be loading less files, giving the user a better experience when they land on the Tiger Paws website.

### Backend Architecture and Frameworks:

**ASP.NET Core 3.0** will be the backend Programming Framework that is used to talk to both the SQL Servers, Document Servers, Redis Server, and Web Application servers. Instead of talking to a Kestral webserver which is default for ASP.NET Core, we will be communicating with Nginx web servers as discussed earlier.

The Web Servers will be talking directly to a **Redis** caching database. Redis is an application with the ability to cache website data. In short, it means that there will be less requests to the database and quicker response time for the user.

Communicating with the **Redis** server will be an SQL Server acting as a "Master". The master will help to identify which of the databases hold the shard that has been requested by the Webserver instance.

To achieve scalability and high performance, we will be using two "Slave" databases (to start with)that will act as Shards.

Once the master gets a request, it will identify which shard has the data and send it back to the Web Servers. The Master will also provide statistics and allow us to scale out if both shards are under heavy load for a long period of time. The Sharding Strategy we use is called the Hash Strategy.

The mast SQL server will also communicate with the Two **Document Databases**. The document databases, will be hosting files such as images, PDFs, tmp files, and any other non SQL data.

### DevOps Tools and Frameworks:

![DevOps Cycle](.\screens\devops-cycle.png "DevOps Cycle")

As with any project, there needs to be a a continuous cycle of Planing, Development, Feedback, and Improvement. Below are some of the Framework and Tools, we will use to make the best possible user experience:

**Planning**: Has been done with Tiger Paws through a meeting and in depth discussion about what they would like to achieve. 

**Development**: We will be using tools such as -

Github - For Version Control
Docker - For container management and ease of development
Docker Compose - To build our containers

**Testing**:


**Professionally designed logo and site theme** - $1000 - We will work with Tiger Paws to design a logo that suits their needs and catches the eye of any would be consumer. Our proof of concept is below:

![Tiger Paws](.\logos\tiger-paws.png "Tiger Paws Logo")

As per our provided logo, the site colours will be Orange #e78200, light Orange #fac175, and black #000000.  

The font to be used on the site will be a mixture of **Emilys Candy** (same as logo), and **Kranky**.

* Please note colours and backgrounds used in the examples, do not represent the finished product as we will work with Tiger Paws to get a complete colour theme, this will take a lot of back and fourth over a course of a few months.
Also because of the potentially elderly customer base, we will need to ensure everything is A11y compliant before release.

### **Home Page** - $600 (2-3 Months)

A responsive homepage with logo designed by Skillage I.T.

![Tiger Paws Homepage](.\screens\homepage.png "Tiger Paws Homepage")

The layout will be a grid layout with a short introduction and title in the middle of the page.  

![Introduction](.\screens\introduction.png "Introduction")

There will be a card on the top left for **Announcements** with an ability to add a picture in the light orange area.  

![Announcements Card](.\screens\announcements.png "Announcements Card")

Underneath the introduction, there will be a grid of specials and community posts to entice users to join the site. This will be a scroll-able page that loads new content as you scroll down further.  

![Specials Grid](.\screens\specialsgrid.png "Specials Grid")

Up the top of the page there will be a navigation bar with the Tiger Paws Logo and links to the three other pages -

* **Catalogue** (will be called EXPLORE)
  
* **Discussion** (will be called FORUM)  
  
* **Communication** (will be called CONTACT)

There are also three other buttons on the top right of all pages -  

* **Magnifying Glass** - For the user to search any content throughout the site.

* **Alerts Button** - For the user to see if they have any post of messages from other users that relate to them.

* **My Profile** - For the user to login and customize their profile to their liking. Also for storing information about the user i.e email, phone number, address etc...

![Navigation Bar](.\screens\navbar.png "Navigation Bar")

Lastly, on the bottom right of each page, to keep up with current trends, there will be a button for the following -

* **Instagram** - Share the page/image/community post/announcement with your Instagram followers.

* **Twitter** - Share the page/image/community post/announcement with your Twitter followers.

* **Facebook** - Share the page/image/community post/announcement with your Facebook friends.

* **World Wide Web** - Share the page/image/community post/announcement by copying the url to the clipboard and posting it to the world.

![Share Buttons](.\screens\share.png "Share Buttons")

### **EXPLORE (Catalogue page)** - $600 (2-3 Months)

A responsive Catalogue page designed by Skillage I.T.  

![Catalogue Page](.\screens\catalogue.png "Catalogue Page")

The layout will take it's style from the home pages' grid layout.

Starting from the top will be the navigation bar (uniform for all pages).

The Tiger Paws logo will be a link be to the home page.
With all other links in the navigation bar exactly the same as the home page.

In the middle under the navigation bar, will be a title asking the user to select their category from the 5 that are provided.  

Below the title will be the 5 catagories with a title and a bit of information in the body.

 ![Category Selection](.\screens\select-category.png "Category Selection")

Under the navigation bar to the left will be a catalogue of items, which will be displayed as a grid, the user is able to scroll down continuously as more content loads just out of the viewport.

![Catalogue Grid](.\screens\catalogue-grid.png "Catalogue Grid")

When a user clicks on an image to get more info, there will be a modal show on the right that has information and pricing.  

![Pricing Modal](.\screens\pricing.png "Pricing Modal")

Here the user can choose to add it to their Kart, or just simply read about the item.

### **FORUM (Community Discussion page)** - $800 (12-24 Months)

A responsive Community Discussion Forum designed by Skillage I.T.

![Forum Page](.\screens\forum.png "Forum Page")

Starting from the top, we have exactly the same format as all other pages. With the **Logo**, **Explore**, **Forum**, and **Contact** buttons all in the same position.

There will be a short introduction to the page up the top in the centre.

![Introduction to the forum](.\screens\intro-forum.png "Introduction to the forum")

In the middle of the page we will show the top discussion happing, with the most popular ones on the top left in a descending order from left to right.

![Discussions](.\screens\top-discussions.png "Discussions")

Each discussion will appear as a card with a picture accompanied by a heading, a body of text, a like button with a count, a comment button with a count, and a share button.

If the user clicks on the card, they will see a pop-up modal that allows them to view comments and/or join in the discussion.

![Comment Modal](.\screens\posts-and-comments.png "Comment Modal")

They can also click on the profile picture to view a larger image of each user.

Over to the right of the forum page, the user will see a **_Trending Posts_** card. This will be an item to show posts that may not have many comments, or post that are in the best interests of the business to show.

![Trending Posts Card](.\screens\trending-posts.png "Trending Posts Card")

Down the bottom right of the Forum page, we will have the buttons that are on each page to share to various platforms.

### **CONTACT (Contact Us page)** - $600 (2-3 Months)

![Contact Us Form](.\screens\contact-form.png "Contact Us Form")

The last page will be the Contact page, allowing users to get in touch with Tiger Paws via email. It also hosts their other contact details so users can get in touch any other way.

On the page, the same template as the other pages still applies. With the Navigation bar having the same buttons, and the share buttons down the button right being exactly the same.

### **Total Time and Costs**

33 Months (Maximum)  
$2600

## Extras

**No extra cost** - Ensure site is compatible with all modern day browsers

**Online Backup** - **$40 per month**  
 Allow Tiger Paws to ensure they always stay online, wth regular backups sent to the cloud occuring nightly.

 **Online Payment Processing** - **$2 per transaction & 3% payment fee**

We are happy to provide Tiger Paws with the payment processing tools to allow them to manage online payments.

**Online Shopping** - $600 an additional page that will allow users to post their products and sell them via Tiger Paws store, ensuring Tiger Paws get paid and get traffic to their website.

## Testimonials

*"The Greatest Company I've ever dealt with. Really helped me get my site up and running"* - **Bill Gates from Microsoft**

*"Fantastic Service, Couldn't be happier"* - **Joseph Stalin from USSR**

*"5 out 7, Comparable service"* - **Dave from the internet**

## Next steps

The next steps are important as we will need to get started as soon as possible to avoid any further losses to the business.

If you choose to proceed, our next steps will be -

1. **Package Customization** - We will work with you to alter the standard web design package to fit your needs, incorporating extras as requested. Once all services are agreed upon, we will finalize our contract with you. This will take 1-2 days.

2. **Website Creation** - We will begin the work on the site and ensure compatibility on all browsers. To be completed in about 33 months.

3. **Website Regression Testing** - Our developers and testers will do continuous testing on all browsers to ensure everything is working well before release. This will take 1-2 hours (possibly less).

Our website testing procedure normally consists of a team of 4 people using web browsers on both desktop, laptops, Android, and IOS devices. They will click on every button and if they find any bugs, this will be sent to the development team who will then put up the fix to a staging build so the testers can test again before we roll the fix out to production.

We will be asking Tiger Paws to also test the staging site so they are happy with the build before we roll out to production.

If all goes well and we are W3C, and A11y compliant, we will roll out the build to the live production site.  

## Terms and conditions & signature page

This Proposal will be sent via email, it is written in Markdown, so it is recommended you view it in a Mark viewer. Something free like Typora is a great option.

We have attached the WireFrames used as XD files, but also as PDF files so you can view them at your leisure.

Please let us know if you have any questions by responding with the contact details at the top of the document.

Or simply sign on the line and send through the completed Document to Skillage I.T.

## *Sign Here* _____________________
