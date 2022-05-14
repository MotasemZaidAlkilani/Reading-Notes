# OO Design
Object-oriented design is the process of planning a system of interacting objects for the purpose of solving a software problem.
It is one approach to software design.

## Priciple 
-DRY principle stand for (Dont repeat Yourself) is a principle of software development aimed at reducing repetition of software patterns,
replacing it with abstractions or using data normalization to avoid redundancy.example for that in code , dont write the same code alot 
,try to reduce of unessary code .

-WET principle stand for (write everything twice) are common in multi-tiered architectures where a developer may be tasked with, for example,
adding a comment field on a form in a web application. The text string "comment" might be repeated in the label, the HTML tag, in a read function name,
a private variable, database DDL, queries, and so on. A DRY approach eliminates that redundancy by using frameworks that reduce or eliminate all those
editing tasks except the most important ones, leaving the extensibility of adding new knowledge variables in one place.
Kevin Greer named and described this programming principle.

-AHA principle stand for (avoid hasty abstractions)is rooted in the understanding that the deeper the investment we've made into abstracting a piece of 
software, the more we perceive that the cost of that investment can never be recovered (Sunk cost fallacy). Thus, engineers tend to continue to iterate on 
the same abstraction each time the requirement changes. AHA programming assumes that both WET and DRY solutions inevitably create software that is rigid
and difficult to maintain. Instead of starting with an abstraction, or abstracting at a specific number of duplications, software can be more flexible and
robust if abstraction is done when it is needed, or,when the duplication itself has become the barrier and it is known how the abstraction needs to 
function.

## Rule of three 
("Three strikes and you refactor") if u have same code written twice , no problem to reduce it ,but if it 3 or more , u need to make new procedure to 
reduce the same codes .the problem with the same code ,in the future it's will be hard to maintain ,so change it when u see it ,to make easier program to
understand from others.

## U are not gonna need it 
this principle telling u to not add new feature to your program if it's not nessary ,because new functions mean more errors and complex program,so just make
what is nessary .

## minimum viable product (MVP)
is a version of a product with just enough features to be usable by early customers who can then provide feedback for future product development.
A focus on releasing an MVP means that developers potentially avoid lengthy and (ultimately) unnecessary work.Instead, they iterate on working versions and
respond to feedback, challenging and validating assumptions about a product's requirements.can be part of a strategy and process directed toward making
and selling a product to customers.[17] It is a core artifact in an iterative process of idea generation, prototyping, presentation, data collection,
analysis and learning. One seeks to minimize the total time spent on an iteration.The process is iterated until a desirable product/market fit is 
obtained, or until the product is deemed non-viable

> "You’re selling the vision and delivering the minimum feature set to visionaries, not everyone."

**Purposes**

-Be able to test a product hypothesis with minimal resources
-Accelerate learning
-Reduce wasted engineering hours
-Get the product to early customers as soon as possible
-Base for other products
-To establish a builder's abilities in crafting the product required
-Brand building very quickly



