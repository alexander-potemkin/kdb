# Marty Cagan - Inspired How To


In the mid 1980s, I was a young software developer working for HP on a high-profile product. It was when Artificial Intelligence was all the rage, and I was fortunate enough to be working at one of the industry's best companies, as part of a very strong software engineering team

  

How Do We Succeed With Remote Developers?

If you find yourself with a remote development team, there are three key things you can do to dramatically improve the odds of your success:

1. The farther away the team is from you—and the more the communication challenges of language, culture and time zones—the more pressure there is to ensure that you have done a very thorough job on the product spec. The nightmare project is where the product manager isn't sure what he wants built (or keeps changing his mind) and the remote engineering team is thrashing. It's like being on the wrong end of a whip—and a recipe for failure.

In the chapter Reinventing the Product Spec, I write about the importance of a high-fidelity prototype as the basis of the product spec. I won't repeat all the reasons for that here, but suffice it to say that if your team is remote, you absolutely want to make sure you use the high-fidelity prototype as your main communication mechanism—both for communicating the actual spec and for communicating changes. Written documents are hard enough to get people to read, but if it's written in a language that isn't native, and if the author isn't in the cube down the hall to clarify questions, you're asking for big trouble.

1. When a development team is local, resource conflicts (for example, two different managers give conflicting instructions) are typically caught and resolved quickly. With remote teams, you can expect lots of unpleasant surprises, and literally months can pass before the disconnects are identified. This is usually because the remote developers are forced to make assumptions about

--- Page 40 ---

Highlight (orange):

who wanted what and how to interpret the various instructions (and, of course, the assumptions are not always correct). It is critical to have someone local manage all coordination with the remote team. This doesn't mean that all communication must be funneled through this person, but there should be no question to whom the engineering team is accountable. Sometimes this is a project manager and sometimes this is a director or VP of engineering who is based locally (near the product manager).

1. There are many good communication mechanisms available within most businesses today. In addition to e-mail and instant messaging, video conferencing technology is much improved, and VoIP has brought the costs way down for international calls. That said, there still is no substitute for establishing personal face-to-face relationships. At least once a quarter, the product manager should get out and spend some quality face time with the engineering team, meeting with the key architects and managers. These face-to-face visits will improve relationships and communication. Another great communication-building technique is to have an exchange program where key developers come stay with the product manager for a while.

With a talented remote team, and managing the relationship as I've described, you can actually come to enjoy this arrangement. Especially with engineers based in India, the time difference can make it such that every morning when you come in to work, you see progress waiting for you, and you can spend your day (and their night) reviewing, testing, and providing feedback. The result can be extremely fast cycle times.

Note that you can also have your prototyping resources in a remote location, but you'll have to work a little harder on the communication and be more flexible on your hours because of the very quick cycle times (several iterations a day).

Yet another solution to the problems of dealing with a remote development team involves locating the entire product team together in the remote location. I see this trend just starting, and I think it will grow. That said, you don't have to worry about this just yet. It has taken 10 years to develop the engineering and QA capabilities in these remote locations, and it'll likely take another 10 before these locations have skilled product managers and designers as well.

--- Page 41 ---

Highlight (orange):

What About Outsourcing?

Just about every company I talk to now is outsourcing to one degree or another. Yet the results are decidedly mixed. I think there are several reasons for the problems that companies are having. Often the problems stem from issues with the product development process, or from language or cultural issues, but more often than not I think the core issue stems from using outsourcing for the wrong reasons.

If you're trying to create inspiring products, for most professional positions, outsourcing should not be about cost savings—it should be about assembling the right people for the product. Very often, you'll have to look beyond your immediate geographic vicinity for the best people. This might mean hiring someone that's based in another state, or in another country.

The sad truth about Silicon Valley is that it has become so expensive that many of the people you would like to hire can't afford to live here at the salary you can afford to pay them. Commuting only works to a degree. Eventually the talent supply runs out and you have to look elsewhere for the right team.

Fortunately, there are some terrific sources of outstanding product talent in places such as India, Eastern Europe (especially the Czech Republic, Hungary, Poland, and Slovakia), Northern Europe (especially the Netherlands, Sweden, and Germany), Israel, China, Singapore, Australia, and New Zealand. I know some amazing people in every one of these locations. One of the best teams I ever had the privilege to lead had members spread across Sweden, Silicon Valley, Boston, and India. We were building infrastructure that needed to support more than 20 million users and it's not at all clear we could have succeeded without the talents of the specific individuals involved.

One of my favorite companies is MySQL, which is a company that has embodied this philosophy for years. They are nominally based in Silicon Valley and Sweden, but their product team and even their executives are scattered all over the globe. They are a true virtual organization, and they are able to benefit from some of the very best database and system software talent to be found anywhere. It is not easy for them to manage a completely distributed product team, but I'd argue that very likely they would not have been able to accomplish

--- Page 42 ---

Highlight (orange):

what they have if they had picked a single location on the globe, and tried to be a typical centralized company.

Just as manufacturing jobs were forced out of Silicon Valley in the ‘80s, several other types of jobs are moving out today—especially customer service, QA, and to a somewhat lesser extent, engineering. It's becoming common to have the architects and QA managers located at the company's headquarters, along with product management and design, and then to have the rest of the team at locations either together or dispersed around the globe.

The key is to realize that it's all about the team and the caliber of the individuals it consists of. Many managers don't quite get this, and they are stunned to learn that there can be as much as a 20X difference in productivity among their staff in the same job class.

Which will do better—the team that has five very strong people chosen for their proven skills, or the team of 15 that was hired or assembled based on their location? This productivity factor can easily dwarf perceived financial savings. Similarly, it can turn a top engineer living in the very expensive city of Stockholm into a bargain.

There are additional factors that come into play, but it's my firm belief that everything begins with the right product team, and if your product team decides you need to outsource, I hope you do it for the right reasons—to get the right people for your product team and not just because you think you'll save a few bucks.

--- Page 43 ---

Highlight (orange):

Engineering Wants To Rewrite!?!

Few words are more dreaded by product managers than being told by engineering: “No more new features! We need to stop and rewrite! Our code base is a mess, it can't keep up with the number of users, it's a house of cards, we can no longer maintain it or keep it running!”

This situation has happened to many companies in the past, and continues to happen today. It happened to eBay in 1999, and the company came far closer to collapsing than most people ever realized. It happened to Friendster a few years ago, opening the door for MySpace to take over social networking. It happened to Netscape during the browser wars with Microsoft, and everyone knows who won. The truth is that most companies never recover.

When a company does get into this situation, the company typically blames engineering. But in my experience, the harsh truth is that it's usually the fault of product management. The reason is that when this comes up, it's usually because for several years, product managers have been pounding the engineering organization to deliver as many features as the engineering team possibly can produce. The result is that at some point, if you neglect the infrastructure, all software will reach the point where it can no longer support the functionality it needs to.

During this rewrite, you're forced to stop forward progress for what the customers see. You might think that the rewrite will take only a few months (more about that below), but invariably it takes far longer, and you are forced to stand by and watch your customers leave you for your competitors, who in the meantime, are continuing to improve their product.

If you haven't yet reached this situation, here's what you need to do to make sure you never do—you need to allocate a percentage of your engineering capacity to what at eBay we called “headroom.” Since many of the issues you run into with rapid growth have to do with scale, the idea behind headroom is to avoid slamming into ceilings. You do this by creating room for growth in the user base, growth in transactions, and growth in functionality; essentially, keep the product's infrastructure able to meet the organization's needs.

--- Page 44 ---

Highlight (orange):

The deal with engineering goes like this: Product management takes 20% of the team's capacity right off the top and gives this to engineering to spend as they see fit. They might use it to rewrite, re-architect, or re-factor problematic parts of the code base, or to swap out database management systems, improve system performance—whatever they believe is necessary to avoid ever having to come to the team and say, “we need to stop and rewrite.”

If you're in really bad shape today, you might need to make this 30% or even more of the resources. However, I get nervous when

I find teams that think they can get away with much less than 20%.

If you are currently in this situation, the truth is that your company may not survive. But if you are to have a chance of pulling through, here's what you'll need to do:

Step 1: Do a realistic schedule and timeline for making the necessary changes that engineering identifies. Most of the time in a normal development project, an experienced engineering team will come up with fairly accurate estimates. The exception to this rule is this case of rewrites—here the estimates are often wildly optimistic—largely because few teams have any real experience with true rewrites. You must make informed decisions in this situation, so you'll have to go through every line item on the schedule to make sure that the dates are realistic.

Step 2: If there's any way humanly possible to break up the rewrite into chunks to be done incrementally with user-visible product development continuing on the site, you should absolutely do so. Even though the rewrite might now stretch over two years instead of nine months, if you can find a way to continue to make forward progress on user-visible functionality—even if it's only with 25% to 50% of the capacity—this is incredibly important for the product to stay relevant in the marketplace, particularly in the fast-paced Internet space.

Step 3: Since you'll only have very limited ability to deliver user-visible functionality, you will need to pick the right features, and make sure you define them right.

After eBay's near-death experience, the team made sure they wouldn't put the company at risk again. This meant immediately beginning another rewrite, this time well in advance of issues. In fact, due to their very rapid growth, eBay

--- Page 45 ---

Highlight (orange):

ended up rewriting a third time, this time translating the entire site into a different programming language and architecture. And they did this massive, multi-million-line rewrite over several years while at the same time managing to deliver record amounts of new functionality and—most importantly—without impacting the user base. It's the most impressive example of rebuilding the engine in mid-flight that I know of.

The best strategy for dealing with this situation is to not get to this point. You need to pay your taxes and remember to dedicate at least 20% to headroom. If you haven't had this discussion with your engineering counterpart, do so today.

--- Page 56 ---

Highlight (orange):

If I ever need a defibrillator one day, I hope there was a product manager on the team that designed it that knew something about cardiac care. But in my experience, this is by far the exception rather than the rule.

I'll go even further. It can be dangerous for a product manager to have too much domain expertise. I say that because people that have spent a long time building their mastery of one domain often fall into another common product management trap: they believe they can speak for the target customer, and that they are more like their target customer than they really are. The product manager needs to constantly revisit assumptions about the domain and the customers. It's not impossible for people with deep domain expertise to do this, but they have to work harder at it to remain open-minded to new developments and options.

--- Page 57 ---

Highlight (orange):

This is not to say that you don't need domain expertise in order to do a good job with your product—in fact I think understanding your product domain is absolutely essential, and I don't mean superficial knowledge either. But I believe that strong product managers can come up to speed on most new product domains very quickly if they approach the education process aggressively. I've learned that it generally takes me one to three months to come up to speed on a domain I haven't worked on before, to the point where I feel confident charting a product strategy. Some people can probably learn faster, and others might take a little longer.

--- Page 61 ---

Highlight (orange):

Building The Team That Will Build Your Company

--- Page 65 ---

Highlight (orange):

How Do We Meaure Product Managers?

Very often I'm asked how product managers should be measured. I have long believed that the only true measure of the product manager is the success of his or her product. While I still believe that, it's not a very satisfying answer, as it's not clear what is the best way to measure a product's success. Is it revenue? Profit?

The number of users? Page views? All of these indicators can be useful, but they don't really provide the big picture needed for a true measurement of a product manager's success.

Recently, a new business metric has been gaining traction across a number of different industries: Net Promoter Score (NPS). It's a very simple metric, and you can read all about it at www.netpromoter.com.

Here's how it works: You ask your customers how likely they would be to recommend your product to others, on a scale of 0-10. Those who rate 9 or 10 are considered “promoters” (they're out there telling their friends how much they love your product, and are actively evangelizing for you); those who rate 7-8 are lukewarm or neutral; and those who rate 0-6, the “detractors,” that is, they not only won't recommend your product, they may even actively warn their friends or the public against your product. If you take the percentage of promoters and subtract the percentage of detractors, you get the NPS, which essentially tells you if you have more people cheering for you or against you.

Quite a few companies already track this metric, and those that rate very highly won't surprise you—companies like Apple, Amazon, Google and eBay.

I like this metric a lot because it puts the focus on the product and the overall customer experience. If, as we like to say in this business, it's all about creating happy customers, then this is a measure of exactly that. Yes, in theory you could have 100% very happy customers, but you end up going out of business because you're losing money on every customer. But for a single metric, I believe this keeps the focus of the company on creating happy customers, which is what fuels growth. And in terms of profitability, the most cost-effective sales or marketing program is your own customers doing the sales and marketing work

--- Page 66 ---

Highlight (orange):

for you. A great product with happy customers lowers these other (often very significant) costs, which contributes to profitability.

Another benefit of this metric is that it leads to the concept of good revenue and bad revenue. For example, let's say the company is approached by a big potential sponsorship or advertising partner that covets your user base and believes they can effectively sell their product on your site. This could be a good thing or a bad thing, depending on how it's done.

If it's done poorly, the short-term revenue might be nice, but if it hurts your customer experience, this will be reflected in the NPS, and your business growth will be slowed. On the other hand, if it's done well—for example, by working collaboratively with the advertising partner—it could be either neutral to the customer experience or even contribute to the experience. This will help your business grow more quickly.

This is why specials (doing explicitly-defined work for a specific customer typically in exchange for their agreement to purchase your product) are so dangerous. They represent bad revenue, and hurt your company's ability to deliver products that create happy users.

You can compare your NPS across companies and even across industries, which is interesting, but NPS is most useful as a way to measure your own progress towards improving your products and services. So if you don't already measure your NPS, consider doing so as soon as possible. Then you can start watching how the changes you make to your products impact the score. Make sure you're always moving in the right direction, and consider the impact on the NPS of everything you do.

--- Page 81 ---

Highlight (orange):

ASSESSING PRODUCT OPPORTUNITIES

Defining The Problem To Be Solved

Opportunities for new products exist all around us, in every market—even mature markets. This is because what is possible is always changing. New technologies are constantly emerging, competitors come and go, and new people with new talents and new ideas join your company.

--- Page 82 ---

Highlight (orange):

opportunity assessment. I ask product managers to answer ten fundamental questions:

1. Exactly what problem will this solve? (value proposition) 2. For whom do we solve that problem? (target market) 3. How big is the opportunity? (market size) 4. How will we measure success? (metrics/revenue strategy) 5. What alternatives are out there now? (competitive landscape) 6. Why are we best suited to pursue this? (our differentiator) 7. Why now? (market window) 8. How will we get this product to market? (go-to-market strategy) 9. What factors are critical to success? (solution requirements) 10. Given the above, what's the recommendation? (go or no-go)

--- Page 130 ---

Highlight (orange):

DESIGN VS. IMPLEMENTATION

Define The User Experience Before Proceeding To Build

--- Page 137 ---

Highlight (orange):

There are three important types of validation that you need to perform before you hand over a final product specification to the engineering team:

Feasibility Testing

One immediate question is whether or not the product is going to be buildable,

--- Page 138 ---

Highlight (orange):

with the technology time and funds currently available. Your engineers and architects should be very involved in investigating technologies and exploring possible approaches. Some paths will be dead ends, but hopefully others will prove viable.

What is most important is that, if there are obstacles the engineering team considers insurmountable in this product's timeframe, it is important to know this now rather than much later in the process—after the time and money has been lost.

Some products have more technical risks than others, but if yours has significant risks regarding feasibility, make sure you address them early.

Usability Testing

Your interaction designers will be working very closely with you to come up with ways of presenting the functionality in the product so that users can figure out how to use it.

Usability testing will often uncover missing product requirements and, also—if done well—identify product requirements that are not as necessary as originally thought. You should plan on multiple iterations before you come up with a successful user experience.

The purpose of the prototype is to have something to test on real people, and usability testing is the art and science of getting useful feedback on your product from your target customers. Certainly, the product manager and designers will use the prototype and learn a great deal from it, but there is no substitute for putting the prototype in front of real people from the target customer base.

Note that for usability testing purposes, it is perfectly fine if complicated back-end processing is simulated—the key is to evaluate the user experience.

Value Testing

Finally, it is not enough to know that your product is feasible to build and will be usable. What really matters is whether or not your product is something users

--- Page 139 ---

Highlight (orange):

will find valuable and want to buy—that is, how much do users and customers like and value what you're doing?

This testing can typically be combined with the usability testing process, and the prototypes used are the same. But in usability testing, you're seeing if users can figure out how to do the necessary tasks, while in value testing you're seeing if they actually care about those tasks and how well you've solved them.

For a few small product efforts, simply working your ideas out on paper may be sufficient. But for most products—with complex user interactions or new uses of technology—prototypes are absolutely critical in order to assess whether or not the product will meet its objectives.

Most often the prototype is simply quickly assembled and clickable pages representing the eventual web site or software service. But for other types of products the prototype may be a physical device or a combination of device and software. The key is that it needs to be realistic enough that you can test the prototype on actual target customers and they can give you useful feedback.

Until recently, there was debate over the relative merits of “highfidelity” prototypes (what I'm describing), versus “low-fidelity” prototypes (essentially paper drawings). Today, I consider this debate meaningless because the cost of high-fidelity prototypes has dropped so low, and the quality of the feedback is so much higher.

In the past, there were two major obstacles to these prototyping approaches. The lack of good prototyping tools meant that it could take a long time to construct the prototype. Another problem was in unenlightened management not understanding the difference between a prototype and the real product. Here, teams would be pressured to use the prototype as the basis for the final product, with predictable results in the quality of the implementation.

Today, there are outstanding prototyping tools that can let engineers or designers rapidly create very functional prototypes (often in hours or days) that can effectively emulate the future product—to the degree necessary—and form the basis of realistic user testing. Moreover, most managers today understand that building a simulation and building the actual product are very different animals —akin to building a scale model of a house versus building the actual home.

These are not the only ways to validate your product—especially for Internet

--- Page 140 ---

Highlight (orange):

services, there are other techniques that are also easy and effective. But I can't emphasize enough how important and valuable it is to validate your ideas before you actually go and build the product. There are always surprises, and it is far better to discover them early rather than when the product is in beta or released. Further, once the real engineering begins, a special type of inertia sets in—it becomes very difficult to make significant changes and the costs of these changes rise dramatically.

--- Page 154 ---

Highlight (orange):

Help Prevent User Abuse

User abuse is when you unnecessarily and (hopefully) unintentionally mistreat your users by releasing changes to the user community that they don't appreciate. 

Highlight (orange):

So what causes user abuse?

Mainly change. As a general rule, users don't like change. Sure they want the software to be great, and they clamor for new functionality, but most people aren't excited about taking the time to learn a new way to do something they can already do.

--- Page 160 ---

Highlight (orange):

SUCCEEDING WITH AGILE METHODS

Top 10 List

Highlight (orange):

Note that this list is meant for product software teams. For custom software, there are some very different considerations.

1. The product manager is the product owner, and he represents the customer. He will need to be extremely involved with the product development team, helping to drive the backlog and especially answer questions as they arise. Some misguided product managers think they get off easy in an Agile environment—they couldn't be more wrong. Some also like to have different people covering the product manager and the product owner role, but this is usually just a symptom of a deeper problem (see the chapter Product Management vs. Product Marketing) 2. Using Agile is not an excuse for a lack of product planning. As a product manager/owner, you still need to know where you're going, what you're trying to accomplish, and how you'll measure success. That said, in an

--- Page 161 ---

Highlight (orange):

Agile environment, your planning horizon can be somewhat shorter and rolling. You should use the lightweight opportunity assessment instead of a heavy MRD (see the chapter Opportunity Assessments). 3. You and your designers should always try and be one or two sprints ahead of your team. This allows you to validate difficult features with sufficient time to improve them. Insist that the designers (interaction designers and visual designers) are front and center in the process, and make sure they don't try to do their design work during the sprint—while the implementation is already underway (see the chapter Design vs. Implementation). Make sure, however, that someone from the engineering team is reviewing your ideas and prototypes every step of the way to provide feedback on feasibility, costs, and insights into better solutions. 4. Break the design work into as small and as independent chunks as possible, but not too small—make sure you don't try to design a house one room at a time. But remember the emphasis on coming up with the minimal product possible. Note that, in an Agile environment, the designers may need to work faster than they're comfortable with. You'll find that certain designers, and certain design methodologies—such as rapid prototyping— are more compatible with the pace of an Agile environment than others. 5. As a product manager/owner, your main responsibility is to come up with valuable and usable prototypes and user stories that your team can build from. Replace heavy PRDs and functional specs with prototypes and user stories. Do prototypes for three reasons: (1) so you can test with real users, (2) to force yourself to think through the issues; and (3) so you have a good way to describe to engineering what you need built during the sprint. Be sure to test prototypes with real users. Try out your ideas and iterate on the prototype until you've got something worth building. You still need to make sure that you don't waste sprint cycles. 5. Let engineering break up the sprints into whatever granularity they prefer. Sometimes the functionality in a prototype can be built in a single sprint, other times it may take several sprints. You will find that having good prototypes will help significantly in estimating the amount of work and time required to build. Remember that the engineering team has considerations in the areas of quality, scalability, and performance, so let them chunk the functionality into sprints as they see fit. 6. Make sure you as product manager/owner and your interaction designer are at every daily status meeting (aka standup or daily scrum). These morning meetings are the beginning of the communication process, not the end. There will be a constant stream of discussion about the product. Designers

--- Page 162 ---

Highlight (orange):

should be previewing functionality to the developers and QA. Developers should be showing off completed code to each other, QA, and the designers and product manager. QA and developers should be identifying potential pitfalls during prototyping, and helping the team to make better functionality, design and implementation trade-offs. 8. Don't just launch every sprint—reassemble sprint results in a staging area until you have enough to make a release as defined by the product manager/owner. It's the product manager's job to ensure that there is sufficient functionality to warrant a release to the user. Remember that in a product environment, constant change can be upsetting to your customers (see the chapter Gentle Deployment). 7. At the end of each sprint, make sure you demo the current state of the product, as well as the prototype for the next sprint. Having everyone see what you finished validates the team's hard work, gives the entire company insight into the product, and keeps the evangelism going. 8. Get Agile training for your entire team. Hire a consultant to help your product team move to Agile, but make sure the consultant has proven experience with product software teams and understands the difference between product software and IT or custom software. If everyone understands the mechanisms around Agile, then you can focus on the execution. If people don't understand, you'll get bogged down in the semantics and dogmatic issues.

--- Page 164 ---

Highlight (orange):

Many are surprised to learn that Scrum, the most popular of the Agile methods, is now over 20 years old. It was created in 1986 in Japan. (Yet another example of just how long it can take for a new idea to reach the tipping point).

But most importantly, these methods originated in the custom software world.

The custom software world—building special purpose software for specific customers—has long been a brutally difficult type of software. This is partly because customers notoriously don't know what they want, but they have a need so they write a contract with a custom software supplier, or sit down with their internal IT folks, who then work to deliver. When they do deliver, the customer invariably responds that it really wasn't what they had in mind, so the cycle repeats and frustration mounts. But the core need still exists, so this provides job security for countless IT developers, custom software shops, and professional services businesses.

Further, custom software has long been on the short end of the stick when it comes to recruiting and retaining top software talent.

This is partly the case because many top software professionals prefer to work for companies that are in the business of creating software for thousands, if not millions of customers. And partly it's because software professionals get paid more working for product software companies where the product team is responsible for coming up with software products that please many people, or they don't make money. So these companies know they must hire the talent

--- Page 165 ---

Highlight (orange):

necessary to create winning products, and they pay accordingly. But to put this in perspective, only a relatively small percentage of software people actually work on commercial product software—most work on custom software.

In the custom software model, since the customer believes he knows what he needs, you'll rarely find the role of the product manager. Likewise, you'll almost never find user experience designers. The reasons for this are more complex, and involve a degree of ignorance (relatively few in the custom software world realize what user experience designers do and why they're needed), and cost sensitivity (cut costs by letting the developers design). But to be fair—due to the shortage of user experience designers in our industry—the few available are immediately grabbed by the product companies that realize how critical they are, so custom software teams can rarely find designers even if their leaders realize they need them. Similarly, QA as a discipline is rarely found in custom software projects—again, the developers are typically expected to do the required testing.

Another crucial element in understanding the custom software world is that the vast majority of custom software projects are relatively small and done to support the internal operations of a company—applications such as HR, billing, and manufacturing—where the limited number of users means that issues such as scalability and performance are usually less critical.

Historically the custom software world used the Waterfall process because the various stakeholders needed a way to monitor progress during the long process of creating these contract applications. In fact, the Waterfall methods originated here as well.

In the product software world, where the software must sell on its own merits, we introduced the roles of product managers to represent the needs of a wide range of customers, user experience designers to create effective user experiences, and QA testers to ensure the software worked as advertised in the range of customer environments.

But in the custom software world, the same fundamental issues of coming up with something that satisfied the customer continued.

For these teams, especially, the Agile methods represent significant improvements. They improve communication between the customer and the engineers. They significantly reduce the risk by building smaller, more frequent

--- Page 166 ---

Highlight (orange):

iterations so that the customer can learn whether he really likes something or not much sooner—rather than waiting for the end of a long process. They help introduce some modern software testing concepts, and they help relieve the team from spending countless hours preparing documents that are rarely read—and quickly obsolete.

In general, these are great benefits for product software teams as well, but I always explain that a few adjustments are required. I've written earlier about these topics—such as how to insert user experience design into the process, and how to manage releases and deployments—but another area that has struggled is architectural design.

Agile methods encourage engineers to not get attached to their implementation, believing that things can be re-factored or rearchitected relatively quickly and easily. This is true for the vast majority of custom software, but for many product software systems, such as large-scale consumer Internet services— which must support hundreds of thousands if not millions of users—this approach can be naïve.

So it shouldn't be a big surprise that the main issues many product software teams encounter with Agile methods stem from their custom software origin. Many Agile books, articles, and training classes still don't mention product managers—or any form of user experience designers (interaction designers and visual designers)—because they aren't meant for product software teams.

My suggestion to teams moving to Agile is to make sure the firm you hire to help your organization transition to Agile actually understands the differences that product software demands. Most don't, but some do.

--- Page 168 ---

Highlight (orange):

The Waterfall method can be applied either informally or very formally, as in the US Department of Defense Standard 2167A (and later 498), which describes in excruciating detail every step of the process along with the many document deliverables.

Similarly, the Waterfall method is also at the heart of the following very informal and much more common scenario: Someone from the marketing department gathers some market requirements and delivers them to engineering, which comes up with a schedule and works on an architectural design, and then some detailed designs for the more complicated areas. The product then moves into implementation and testing, often a beta, and finally deployment.

While we will soon discuss the most serious limitations of this approach, it is also useful to acknowledge the key traits that have kept this process in use for so long:

Management appreciates the (perceived) predictability of the process. It is possible, although not common, to come up with fairly accurate schedules for even large and complex software projects. This assumes, however, that you completely and accurately understand the requirements and the technology, and that there will be no changes. With iterative approaches, you don't really know how many iterations will be required, and this can be disconcerting to management. There are deliverables throughout the process. Many people (managers, customers/clients, and even some engineers) are reassured by seeing well thought-out and thorough documents and design diagrams. It helps these people to gauge progress towards the end, and it also helps them feel better about the level of thinking that has gone into the project (even though there is no way to test whether or not the confidence is justified because unlike software you can't execute paper documents). Many people make the mistake of feeling unjustifiably reassured by impressive specifications and documents.

Highlight (orange):

Product Management Concerns

There are a number of well-known concerns with this process, especially from

--- Page 169 ---

Highlight (orange):

the product manager's perspective:

Validation Occurs Too Late in the Process

Highlight (orange):

Changes Are Costly and Disruptive

Highlight (orange):

Responding to the Market

--- Page 171 ---

Highlight (orange):

STARTUP PRODUCT MANAGEMENT

It's All About Product Discovery

Highlight (orange):

Here's how the model typically works: Someone with an idea gets some seed funding, and the first thing he does is hire some engineers to start building something. The founder will have definite ideas on what she wants, and she'll typically act as product manager and often product designer, and the engineering team will then go from there. The company is typically operating in “stealth mode” so there's little customer interaction. It takes much longer than originally thought for the engineering team to build something, because the requirements and the design are being figured out on the fly.

After six months or so, the engineers have things in sort of an alpha or beta state, and that's when they first show the product around. This first viewing rarely goes well, and the team starts scrambling. The run rate is high because there's now an engineering team building this thing as fast as they can, so the money is running out and the product isn't yet there. Maybe the company gets additional funding and a chance to get the product right, but often it doesn't. Many startups try to get more time by outsourcing the engineering to a low-cost off-shore firm, but they're still left with the same process and the same problems.

Here's a very different approach to new product creation, one that costs

--- Page 172 ---

Highlight (orange):

dramatically less and is much more likely to yield the results you want: The founder hires a product manager, an interaction designer, and a prototyper. Sometimes the designer can also serve as prototyper, and sometimes the founder can serve as the product manager, but one way or another, you have these three functions lined up—product management, interaction design, and prototyping— and the team starts a process of very rapid product discovery.

I describe this process in detail in the chapter Reinventing the Product Spec, but there are two keys:

1. The idea is to create a high-fidelity prototype that mimics the eventual user experience 2. You need to validate this product design with real target users.

In this model, it's normal to create literally dozens of versions of the prototype— it will evolve daily, sometimes with minor refinements and sometimes with very significant changes. But the point is that with each iteration you are getting closer to identifying a winning product.

This process typically takes between a few weeks and a few months. At the end of the process, you have (a) identified a product that you have validated with the target market, (b) a very rich prototype that serves as a living spec for the engineering team to build from, and (c) a much greater understanding of what you're getting into, and what you'll need to do to succeed.

Now, when you bring on an engineering team, they'll start off with a tremendous advantage—a clear understanding of the product they need to build and a stable spec. You'll find that the team can produce a quality implementation much faster than they would otherwise.

So why don't all startup teams do this? Because we're such an engineering-driven industry that we just naturally start there. But any startup has to realize that everything starts with the right product, so the first order of business is to figure out what that is before burning through $500K or more in seed funding.

This model applies beyond startups to much larger companies as well. The difference is that bigger companies are generally able to underwrite the several iterations it takes to get to a valuable product, while startups often can't. But there's no reason for the inefficiencies that larger companies regularly endure.

--- Page 173 ---

Highlight (orange):

So on your next startup or new product development effort, give this approach a try.

--- Page 174 ---

Highlight (orange):

INNOVATING IN LARGE COMPANIES

Difficult But Worth The Effort

--- Page 175 ---

Highlight (orange):

Innovation via the 20% Rule

Many of you have heard that at Google, engineers get to spend 20% of their time on the projects of their choice. More than 20 years ago, this was also the policy for our team at HP Labs, and we borrowed the idea from Xerox PARC. It worked then and it still works now. At HP Labs, our job was to come up with innovative technologies that the product divisions could then incorporate into commercial products. In the group I was in, we took five new products to market, and only one of them was for a technology that came from above (and that product was the one that actually failed badly in the market). The other four innovations were fruits of the 20% rule.

As much as we might like to think that the great product ideas are the result of great strategic planning, or that they come down from the executive team, in many cases, the best ideas come from the bottom up. What's great about the 20% rule is that lots of ideas can be tried out. And when you inject the feeling of ownership that comes from thinking up the ideas yourselves, the ideas are pursued with more passion and creativity.

Highlight (orange):

Innovation via Skunk Works

Skunk works is a very old industry term that originally referred to secret military projects, but today refers to chasing ideas under the radar, unhampered by bureaucracy, on your own time if necessary. Skunk works projects have saved countless large companies.

In large organizations, it's hard to get permission to officially explore ideas. However, once you have proven an idea, it's remarkably easy to get the project funded. So long as you continue to carry out your official job responsibilities, management is usually supportive—many times they'll even pitch in and help.

Just remember that your company likely owns the intellectual property of

--- Page 176 ---

Highlight (orange):

anything you come up with on the job, so I'm not suggesting that this is how you pursue your new startup idea. If you do decide to chase a skunk works idea, and the result looks good but your company doesn't want to pursue for whatever reason, you might want to discuss an arrangement where you pursue the idea on your own. Those of you that know your Silicon Valley history may recognize this situation as the birth of Apple Computer when Steve Wozniak's employer HP wasn't ready to enter the personal computer market.

Highlight (orange):

Innovation via Observation

One of the easiest ways I know of to innovate is to just watch (and listen) as actual users attempt to use your current product or a competitor's product.

Highlight (orange):

Innovation via User Experience Design

Another good source of innovation is to step back, relax your technical constraints for a moment, and consider what the ideal user experience would be for your product. Not just more efficient implementation of tasks, but

--- Page 177 ---

Highlight (orange):

eliminating tasks altogether. What is really essential, and what is there just because it's a side effect of the way the product is designed and built?

Highlight (orange):

Innovation via Acquisition

Finally, we do need to talk about innovation via acquisition. Many product managers view an acquisition as a failure on their part. But in truth, acquisition can be an excellent technique for innovation—especially in areas where the risks are high. In essence, the company lets dozens of startups test the waters, try out their ideas, and either succeed or fail. The few remaining companies with products that work out may be good candidates for acquisition. Not only does this sort of acquisition bring in innovative new technologies, but they also bring in new blood with new ideas that you can leverage for your own purposes.

--- Page 187 ---

Highlight (orange):

How many times have you seen the situation where a sales rep brings to the CEO a proposal from a prospect that says, “If you will just add these seven features to your product, then we'll buy your software.”

Highlight (orange):

So what's wrong with doing a special? One of the surest ways to derail a product company is to confuse customer requirements with product requirements.

I've talked in several chapters about the reasons why you can't count on customers to describe the product that they need, but to summarize: first, it's extremely difficult for the customer to know what he needs until he sees it; second, customers don't know what's possible; and third, customers don't often interact with each other in order to identify common themes.

But, more generally, even if the customer doesn't have these issues, it's not clear

--- Page 188 ---

Highlight (orange):

that these are the best things to focus on right now. By pursuing these special features now, what important work are you delaying? What is the business cost of that delay?

Assuming these are not issues, specials are still dangerous. How come? Because your job is to meet the needs of a broad range of customers—that's what distinguishes product companies from customer software shops. If a year from now the market changes, you need to be able to quickly change and adapt. If you are contractually obligated to keep supporting a specific way of doing things, then your business will not be as nimble as it needs to be. Remember that every version of your product will have to be built, maintained, tested, released, documented, and supported. It doesn't take too many specials to weigh down a company to the point where it takes them months to do even the smallest release.

Don't get me wrong—there's nothing wrong with custom software shops. They provide an essential service for countless companies that need specialized solutions, and can often deliver that specialized solution in a fraction of the time and at a fraction of the cost of inhouse developed solutions. But custom software is a very different business than commercial product software.

So how do you avoid the pitfalls of specials? Undeniably, it takes corporate discipline to be able to recognize specials for what they are and be willing to walk away. 

Highlight (orange):

First, it is natural for any customer to want to describe their problem in terms of the solution they can envision rather than the underlying problem itself. But as product manager it's your job to work with the customer to tease out the core issues and needs. You can help them recognize that there may be other approaches to this problem that provide a solution they would like even better. Most customers do not want to be running on a custom version of software. They want to be running on your mainstream product—the one that gets the most attention, support and improvement.

Second, consider looking at how you could keep your product general purpose but allow the product to be tailored/customized/ extended by the customer or by a solutions provider. And then have ready the names of a couple of system integrator/solution provider companies that can tailor your product to meet this specific need. You may need to partner with the solution provider so that your

--- Page 189 ---

Highlight (orange):

customer doesn't have to manage two relationships and have to worry about finger pointing if there are issues.

--- Page 190 ---

Highlight (orange):

WHAT ABOUT REQUIREMENTS MANAGEMENT TOOLS?

Highlight (orange):

The thing is, in most cases the Wiki works just great, so there's little need for expensive software with its own learning curve that just ends up distracting you from the real thinking that must go on in order to come up with a winning product.

--- Page 191 ---

Highlight (orange):

THE NEW OLD THING

What Is Possible Is Constantly Changing

--- Page 194 ---

Highlight (orange):

FEAR, GREED AND LUST

The Role Of Emotion In Products

I find it ironic that so many of us in the product world come from science- and business-oriented backgrounds, yet such a large part of what we do every day is really all about emotion and human psychology. Most of us may not think of our job this way, but we should.

People buy and use products largely for emotional reasons. The best marketing people understand this, and the best product people ensure that their products speak to these emotions.

In the enterprise space, the dominant emotion is generally fear or greed. If I don't buy this product, my competitors will beat me to market, hackers will penetrate my firewalls, or my customers will desert me. Or, if I do buy this product, I will make more money, save more money, or stop spending so much money.

In the consumer space, the dominant emotions get more personal. If I buy this product or use this Web site, I will make friends (loneliness), find a date (love or lust), win money (greed), or show off my pictures or my taste in music (pride).

You may not have thought about your product or service in these terms before, but if you apply this emotional lens, you can start to view things much more in line with how your users and customers view your service—and potential competitors. Where else can they go to get these needs met? What could be done to the visual design to speak more directly to these emotions? What features can we provide that speak more directly to these emotions? What features get in the way of clearly speaking to these emotions?

Keep in mind also that different types of users may bring different emotional needs to the table. An eBay power seller is not the same as a buyer looking for a

--- Page 195 ---

Highlight (orange):

great bargain, or a buyer looking for the thrill of competing with others to “win” an item.

When you do prototype testing with your target users, after you determine whether or not the test subject can actually figure out how to use the product or service, you should take the opportunity to essentially do a one-on-one focus group to try to learn what emotion is driving this user, and how well your product meets that emotional need.

You can hopefully see why user experience design (interaction and visual design) and usability testing play such a key role in coming up with a winning product.

Once you have clearly identified and prioritized the dominant buying emotions your customers bring to your product, focus on that emotion and ask yourself where else they might be able to get that need met? That's your real competition. In many cases you'll find that the competition you should be worrying about is not the startup or big portal that's after the same thing you are, but rather the offline alternative.

--- Page 196 ---

Highlight (orange):

Jeff Bonforte—as of this writing an exec at Yahoo! responsible for several industry-leading products used by millions—argues for adding a layer of analysis to the technology adoption curve, based on the driving emotions of the users in each group.

In this interview, Jeff shares his views on the role of emotions in product development.

Marty: Why do you like to focus on anger?

Jeff: Because angry people dictate the future of technology.

I like my product managers to focus on the most miserable thing people have to deal with everyday. If you can solve that problem, that actually changes behavior, and that can lead to the truly big product wins.

Don't focus on the technology of your product, just think about the people that you're trying to help. What are the problems they're dealing with? What are the things that they're frustrated with?

--- Page 197 ---

Highlight (orange):

The Lovers (Innovators) are the techies who buy the product because they find the technology cool. These people are very dangerous to product managers because they are driven by very different needs than the larger population. They look at solving tough technical problems as fun.

On the other hand, the Irrationals (Early Adopters) feel the same emotions as the general population, but with more intensity. These are often negative emotions such as anger, fear, or loneliness, but in any case, the strength of these feelings can lead to buying behavior that is not economically rational, for example, they'll spend more time learning something than the value they get just so they can get the satisfaction of addressing these emotional needs.

The good news is that as the product improves, ordinary people who feel the more subdued versions of the same emotions will also be motivated to buy.

Highlight (orange):

In my view, far too many product managers talk in terms of features and technology, and we don't really talk in terms of the user's core needs or emotions.

Marty: Let's go back to the technology adoption curve. What do you see as the underlying emotions and needs driving each of the groups of users?

Jeff: In the Technology Adoption model, we're told that there's a technology adoption curve, and it's nice and clean. But there's also a chasm, and maybe there's a tornado in there too. But, what does that mean exactly? What are we supposed to do to design around these things?

Instead of thinking about these groups using the labels that we were given by Geoffrey Moore—which, by the way, I found to be counterintuitive—I instead assign one of the emotional states for their adoption of technology. So, I talk about the Lover, the Irrational, the Efficient, the Laugher, and the Comfortable.

Marty: What does each of these groups represent?

--- Page 198 ---

Highlight (orange):

The Efficients (Early Majority) will adopt when the technology becomes practical. Again, they feel the same emotion, but they're more pragmatic about the benefits versus the costs.

The Laughers (Late Majority, and Yahoo's core constituency) feel the same emotion, but it's more muted and they don't want to deal with any grief in order to get the benefits.

The Comfortable (Laggards) are the 15% that want the benefits but it just has to be drop dead simple and convenient for them to make the move.

In this view of adoption, there is tremendous power in the Irrationals.

Lovers and Irrationals are often coming in the door at the same time, despite the traditional adoption curve that seems to imply there's first one and then the other. While Lovers and Irrationals may enter in at the same time, Lovers are the worst possible people in the world from a product manager's perspective.

Marty: Why is that?

Jeff: Because they mislead you one hundred percent of the way. Lovers buy a Prius because they like the battery technology.

On the other hand, Irrationals buy a Prius because they love the environment so much that they'll spend $22,000 over the benefit of the environment. They could just buy carbon credits and carbon neutralize themselves, or they could get a motorcycle, but they overspend on the solution because they're passionate about the problem they're trying to solve.

The bottom line is that Irrationals are really interesting, and Lovers are really not.

People that obsess over your product because they like battery technology don't buy your product for the same reasons anyone else does, but the Irrationals do.

Irrationals are essentially overreacting to the anger, but the emotional reaction they have is more of a multiplier times their logic. They exaggerate the value. But if you can tap into what they're thinking and what they feel, this can be very powerful.

--- Page 199 ---

Highlight (orange):

The Irrationals can teach you the value of your product all the way down the line.

The latent frustration is highest amongst the Irrational and then it dissipates, but it's still always there. The Lovers are largely unconcerned with the core solution —they're more concerned with the technology involved.

One of the reasons startups in particular fall into the chasm is that they misread the situation—they confuse the Irrationals with the Lovers.

Marty: So how do you address this at Yahoo!?

Jeff: One of the challenges Yahoo! and many large companies face is that we envy a lot of startups, and we think, “We want to do cool stuff like that.” But Yahoo has made its fame and fortune off serving the Laughers, so we will serve our user base much better by understanding Irrationals, and not by kowtowing to the Lovers.

Sometimes marketing folks confuse the emotional groups with demographics. They'll look at the Irrationals and say, “Oh, this group is comprised of males 18-30,” but it's not true. If you're in finance, you may have an Irrational group that's very different looking—it could be retired women. You have to look at each product individually, and look at the core emotions for this particular product.

Marty: So what do teach your product managers to look for?

Jeff: Look for anger, exasperation, and frustration. If you just take a look at all those we love to hate—the telcos, banks, consumer credit firms, the tax man, government bureaucracy, airlines, health-care—these are all great opportunities for innovation because the consumer latent frustration is so high.

Look at the music industry. We have to pay $15.98 for a CD with one good song on it. Is it any surprise that so many people feel good about stealing from these people?

We're all so impressed with Skype's growth, and yet, had we looked and seen the latent anger and frustration in the space, it would have been relatively predictable to say, it's not about standards or technology, or being open versus proprietary. The Skype guys rejected all that thinking and said we're just gonna

--- Page 200 ---

Highlight (orange):

make it work, and they then tapped into that latent frustration. It was like heroin, you couldn't stop it.

Contrast this with the webcam business. The problem here is there's no angry person in the webcam business—we don't hate our webcam providers, or our video conferencing guys—and webcam satisfies a need that's high up in Maslow's pyramid. It's “I wanna see my kid,” and while there's love involved there, not all of us have kids, and you can easily call your kids, so we're not all dying for a webcam.

So, when you add video to Skype, not much happens. Their user base doesn't grow that much, the usage of webcam and messenger doesn't go down—nothing changed. And so the chasm for webcam is actually huge because taking it to the mainstream for webcam means you don't have much frustration to leverage— you don't have that driving emotional need.

You really need the Irrationals to slingshot your business into the Efficients and the Laughers. Without that emotion from those irrational people you don't get the passion that carries the product over the chasm. So as with so many things in life we're brought back to Maslow's pyramid. If you look at the needs, the further down you go, the more you're tapping into core emotions, and the better off you are because these are the deepest emotions for humans.

Politicians like to tap into the fear emotion and explain that bad people are gonna destroy your cities, or come and bomb you, or you're not going to have food tomorrow. Well it's not that hard to motivate you to change your behavior when you energize these core emotions. It's much harder to get people to do something by appealing to their aspirations.

Google is the big winner in this way of thinking because the nature of a search engine is to help address countless critical human needs. If you've been diagnosed with a disease you go to Google to learn how to treat it. If you have to buy something, Google finds it for you. They're the good guys that are there to help you with whatever problem you have.

So the question we ask is, “What are the emotions that are driving the behavior?” And then we look for ways to tap into those emotion with features and all the other things. We assess for each of our projects which core emotions they appeal to, and how acute is the user's pain.

--- Page 201 ---

Highlight (orange):

Marty: Do you have a favorite approach for assessing these core emotions?

Jeff: One technique I use is what I call the “freshman test.” Think back to the first day you walked into high school. You feel more pure emotions of human frailty in that one day than in any other day in your life. You're small, your hormones are all out of whack, anything you had acheived in your previous school completely gets washed away and you're a nobody—and you know you're a nobody.

If you can tap into any one of those emotions that every human everyday feels— loneliness, insecurity, fear, frustration, anger—some bit of that freshman thing, then you're on the right track.

--- Page 202 ---

Highlight (orange):

USABILITY VS. AESTHETICS

Both Are Important

--- Page 205 ---

Highlight (orange):

Customer support. One of the biggest (and least fun) surprises that most consumer service companies run into is customer support. Traditional models of customer support can quickly bankrupt even the best services companies. This is oversimplifying a complicated topic, but you have no alternative other than designing and building the product to absolutely minimize customer support costs—especially if you charge a fee for your service. Yet, always remember that it is not about controlling customer support costs—it is about ensuring a great customer experience.

--- Page 206 ---

Highlight (orange):

Community management. Every company is dependent on its customers, but for consumer Internet service companies, this community of users takes on even more powerful importance—they can make you or break you. It has never been easier for them to communicate how much they love your product—or how badly you just treated them. If your users value your product, they will want to be loyal, and they will want to be a part of the great community you are creating. But they also want to be appreciated and

--- Page 207 ---

Highlight (orange):

recognized—and not just with lip service. There are many ways to reach out to your community—to learn from them and understand where they want to see your product go. There are also many ways to show your gratitude to the community and to recognize those that make especially valuable contributions. Do this, and make community awareness a top priority for everyone in your company—from the CEO on down.

--- Page 208 ---

Highlight (orange):

KEYS TO ENTERPRISE PRODUCTS

--- Page 211 ---

Highlight (orange):

Product update. Installing a new version of enterprise software is never fun. The vendor thinks it's the biggest event of the year, but the customer has a business to run, and installing updates of vendor software isn't something they typically want to be spending their precious time and resources on. Having problems upgrading or requiring complex data migration is extremely frustrating to the customer. Again, most consumer products realize this and make a much bigger investment in technology to upgrade, and in testing the upgrade process.

--- Page 215 ---

Highlight (orange):

KEYS TO PLATFORM PRODUCTS

High Leverage But Not Easy

One of the most difficult—but highest leverage—types of product management is to define successful platforms. By platforms, I am referring to foundation software that is used by application developers to create end-user solutions. Examples include operating systems (e.g., Windows, MacOS, Palm OS), operating environments (e.g., Java, Flash), Web services (e.g., Amazon's or eBay's integration APIs), game developer platforms (e.g., XNA), and application-level platform runtimes (e.g., Facebook and Salesforce.com).

Before I go further, it's important to point out what is not a platform. There are too many so-called “platforms” out there that are really just unfinished products. The team didn't do the work required to provide a complete solution, so they market it as a platform and push the work off on the customer or a developer to finish. If you can't program the platform through some form of API, and if you don't have multiple commercial software products or services built upon your software, then you're not a platform in the sense I'm describing.

But assuming you are, then you know how difficult platform product management can be. To begin with, there are three very different constituencies:

The application providers—the businesses that choose to use your platform to build their solution. The developers—those who work for the application providers and who write their software using your platform services. The end-users—the ones who run the application provider's products, and ultimately use your services.

Each of these three constituencies brings to the table very different needs and requirements. You simply can't be a successful platform without meeting the key needs across all three.

--- Page 216 ---

Highlight (orange):

The application provider is going to be concerned with business viability—their viability if they use your services, and your viability in case you go out of business or discontinue support for the platform. The application provider cares about your pricing, licensing, quality, support, and global availability, among other factors.

The developers are looking for services that make it easy for them to quickly create maintainable, reliable code in the languages they want to use, working with their favorite tools and infrastructure, on the devices they need to deliver on.

The end-users care mainly about the end result. If the features and services they want aren't there or don't work in the way they need, they don't buy the application, and the application provider fails. You lose a customer, and eventually you fail too.

One of the biggest mistakes platform product managers make is in the prioritization of the three constituencies. Developers are the most vocal group and the easiest for the company to relate to, so they usually get considered first. The application provider is the one writing the check, so they come close behind. But the end-user is often so far removed from the platform provider that they rarely interact directly. Unfortunately, this is precisely the reverse of what's needed. It is a big (but common) mistake to optimize for developers over the end-user.

I know this may sound heretical, but it is okay for the developers to work a little harder if the application is something end-users like and use, versus making the developers happy but nobody wants the end result.

Countless platform-wannabes made this mistake. The reasoning is very simple: I'm a developer—I know what other developers want, so I'll create something to help both my colleagues and myself. I would have to include client-side Java in this camp—great development environment, terrible user experience, terrific opportunity for Macromedia (now Adobe).

Many extremely successful platforms have been downright awful for the developers. But they succeeded because of compelling value to the end-users and—therefore—to the application providers. You don't have to look further than early Windows for an example of this.

--- Page 217 ---

Highlight (orange):

I'm not advocating platforms that make life miserable for developers, but product management is all about choices and priorities, and it's essential to understand that the delivered application is what matters the most.

There are other important dimensions to platform product management that make this area challenging. For example, there are many different delivery models (e.g., embedded, private-label, co-branded, hosted) and many forms of customization that may be required (e.g., end-user, customer's IT, solution provider/SI, vendor, source code). Each of these is a topic in itself.

Support is also very difficult for platform providers. The bar is high because you're a critical dependency for all of your customers. That said, the great thing about working on platforms is that they're very high leverage—if you do it well, you can create a thriving ecosystem where you and your application provider partners succeed together.

--- Page 219 ---

Highlight (orange):

BEST PRACTICES SUMMARY

Top 10 List

In my more than 20 years of industry experience, I have observed many practices used to create successful and inspiring products—here are what I consider to be the 10 most important.

Each is described in detail elsewhere in the book, but this summary will hopefully give you a sense of what I consider the most important practices, and I hope you'll give them all a try.

1. The role of product management. Too many product leaders spend their time on other activities, especially product marketing and/or project management. These activities are not a substitute for true product management. 2. The role of user experience. For most software products, the user experience is all-important. Devising a good user experience requires that you collaborate closely with an interaction designer and an engineer to come up with something that is valuable, usable, and feasible. 3. Opportunity assessments. These lightweight, to-the-point assessments replace the old “MRD” (market requirements documents). Before you jump into the solution, this makes sure you know what problem you're trying to solve, who you're trying to solve it for, and how you'll know if you are successful. 4. Charter user program. It is shocking to me how many product teams think they can come up with great products without talking to users and customers. If you only do this one thing, it will ensure that you do several other things right, starting with direct and intense user interaction. 5. Product principles. Product management is all about making choices, and many of the techniques here are about helping you make good choices. The product principles help you identify and prioritize what you believe is important.

--- Page 220 ---

Highlight (orange):

1. Personas. Another key technique for making the difficult choices required for an inspiring product is to use personas as a way to focus your release and to understand the key behaviors and underlying emotions of the target users. 7. Focus on discovery. The primary responsibility of the product manager is to discover a product that is valuable, usable, and feasible. It makes no sense to proceed to building something until you have evidence that you have discovered this product. 8. The use of prototypes. One of the most important product discovery techniques is to create a high-fidelity prototype. We do this for several reasons: First, it forces you to think much deeper about the solution; second, it enables you test your ideas out with real users; and third, it is the most useful way to describe the product to be built to the rest of the product team. 9. Test prototype with target users. Once you have a prototype, you can find out which of your ideas works and which do not. The techniques for this prototype testing are something that all product managers and designers need to master. Knowing how to get feedback on product ideas is probably the single most important skill for product managers. 10. Measure to improve. The successful product manager uses data to make important decisions, especially when trying to improve an existing product. Improving a product is not about adding features that customers request; it is about analyzing the product's actual use, and then relentlessly driving the product to improve the key metrics.

--- Page 221 ---

Highlight (orange):

PRODUCT MANAGER WORRY LIST

Top 10 List

The strong product manager is constantly obsessed with the current and future state of her product. Here are the questions she is constantly asking herself:

1. Is my product compelling to our target customer? 2. Have we made this product as easy to use as humanly possible? 3. Will this product succeed against the competition? Not today's competition, but the competition that will be in the market when we ship? 4. Do I know customers who will really buy this product? Not the product I wish we were going to build, but what we're really going to build? 5. Is my product truly differentiated? Can I explain the differentiation to a company executive in two minutes? To a smart customer in one minute? To an industry analyst in 30 seconds? 6. Will the product actually work? 7. Is the product a whole product? How will customers actually think about and buy the product? Is it consistent with how we plan to sell it? 8. Are the product's strengths consistent with what's important to our customers? Are we positioning these strengths as aggressively as possible? 9. Is the product worth money? How much money? Why? Can customers get it cheaper elsewhere? 10. Do I understand what the rest of the product team thinks is good about the product? Is it consistent with my own view?

The reason that “thinking time” is so critical each day—and why the job of product manager is so all-consuming—is that these questions require serious and ongoing consideration.

--- Page 225 ---

Highlight (orange):

ABOUT THE AUTHOR

During the course of the past 20 years, Marty Cagan has served as an executive responsible for defining and building products for some of the most successful companies in the world, including Hewlett-Packard, Netscape Communications, America Online, and eBay.

Before founding the Silicon Valley Product Group to pursue his interests in helping others create inspiring and successful products through his writing, speaking, and workshops, Marty was most recently senior vice-president of product management and design for eBay, where he was responsible for defining products and services for the company's global e-commerce trading site.