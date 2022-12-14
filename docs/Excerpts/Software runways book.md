Software Runways - Robert L. Glass
Lessons learned from Massive Software Project Failures

For at least a decade, the software industry has heard the advice "do a post mortem". The advice is to spend a few days after a software project completes analyzing what went right and what went wrong during the project. The advice falls on a deaf ears usually. However, it is only through analyzing our success and failures that we can possibly improve.


1. Most of the runaway projects are (or were) huge. It is well known in he field that huge projects are much more troublesome than smaller ones. These stories support that finding.
2. Most runaway projects results from a multiplicity of causes. There may or may not be one dominant cause, but there are always several problems contributing to runaway.
3. Many of the runaway projects were lauded early in their history as being "breakthroughs", significant advances over the systems they were replacing. It appeared that visibility into the possibility of failure did not emerge until the project was well under way.

But the unpredictable is much more fascinating. Here are some characteristics of these runaway projects that none of my reading (and I suspect yours as well) prepared me for:

1. Technology was just as often a cause of failure as management. The literature, especially in the software engineering field, tends to say that major failures are usually due to management. But for nearly half of these 16 failure stories the dominant problem was technical.
2. There were two especially surprising and dominant technical problems. The first was the use of the new technology. Four of the projects, fully expecting to be breakthroughs because they were using the latest in software engineering concepts, instead failed because of them! One used a megapackage approach to replacing its old, legacy software, betting the company on the approach - and losing. Another used a Fourth Generation Language ("4GL", a problem-focused programming language) for a large project, and found (after the work was complete!) that is was not capable of meeting performance goals for the (on-line) system. Yet another tried to port an existing mainframe system to client/server, and found the complexity increase got out of hand. And the fourth put together so many new technologies that the project foundered from their sheer weight (that didn't prevent some of the project's principals from proclaiming the project a success in their company's house organ!).
3. The second dominant technical problem was performance. Many of these runaway projects were in some sense real-time (that in itself is a pertinent finding), and all too often the as-built systems simple were too slow to be useful. This is particularly interesting because most academic curricula now downplay the importance of system efficiency, with the thought that brute force hardware speed has done away with the need for more subtle software solutions. This data, at least, suggests that the field may have overplayed that hand.

... software runaway... is a project that goes out of control primarily because of the difficulty of the building the software needed by the system.
The implication of "out of control" is that the project become unmanageable; it was not possible to manage it to meet its original target goals, or to come even close to them. If those goals are thought of in terms of schedule - and this is the most likely kind of runaway - then the project consumed close to double of its allotted estimated time or more. If the goal was cost, and usually projects that go well over budget also exceed cost targets, then the project consumed close to double its estimated cost or more. If the  goal was a reliable product that met its functional requirements, then the product could not meet those targets, and in fact, all too often, failed to meet any targets at all because the project had to be canceled.

It is now 1998, and we are only 40 something years into the history of the software field. At this primitive, early stage, the most common problem in building software systems is not the construction of them itself, but rather the estimation of the costs of that construction.
<...>
Because the construction of software is an extremely complex task - some say - it is the most complex task ever undertaken by human beings.

Most of those who cry crisis and are trying to sell or promote something are offering a better technology to build software. But most of the case studies of software failure find that poor management technique, not poor technology, is the cause of the problems.

Study after study of software estimation in practice has shown that most often cost and schedule targets are set by marketers or customers, next most often by managers, and least often by the technologists who will do the work. Without control of their own destiny, practitioners still get blamed when things go wrong.


Crunch Mode is a term used by John Boddle in his book of the same name \[Boddie, 1987\]. It is a term describing the status of a project. A project that is in crunch mode is there due to a threat to its reaching its original targets (cost, schedule, functionality, ...), and the project team is working very hard to try to overcome that dilemma. "We're in crunch mode, and I won't be home 'til after midnight," a software specialist might say in a call from the office to this life partner. The life partner won't be surprised - crunch mode tends to last for days, weeks or even months, depending on the duration of the project itself, and the degree to which it is off-target.

Death Match is a term used by Ed Yourdon in his book of the same name \[Yourdon 1997\]. It is a term that also describes the status of a project. A project is a death march if the parameters for that project exceed the norm by at least 50 percent.

1. Crunch mode is used to describe a project that has an extremely tight schedule. It speaks to the pressure being felt by the project participants.
2. Death match is used to describe a project that has a nearly impossible schedule. It speaks to the oppressive smell of potential failure surrounding the project participants.
3. Runaway is used to describe a project nearing or after its termination. It speaks to the failure of the project to stay within its boundaries. Often it speaks about a project that has either already failed (usually in a spectacular way), or is about to.

A typical project to which these terms might apply could progress in the following way: The project looks from the outset to be crunch mode because someone has promised project results that are too much, too soon. As the project gets underway, project participants all too soon find themselves on a death match, trying to achieve these increasingly unachievable targets. When it becomes obvious that the project probably cannot succeed and will fail in a major way, the project becomes a runaway.

Not all projects that are death marches fail, of course (remember that the death march is the normal way of running a project these days, according to \[Yourdon 1997\]. Although some of those death marches become runaways, others will become successes). But all of them, successes or failures, will have functioned in crunch mode.


Software personnel are motivated by things such as challenging projects and/or a chance to use new technology rather than the mote traditional ones of power or money.


Because we know so little about accurate schedule estimation, and because estimates are usually made by the people who are least able to make accurate estimates (e.g., marketers and customers), it is simply the norm that schedule targets, and thus cost targets, are unreasonably short. Thus project achievement of them is at best problematic.
<...>
The problem for systems and software is worsened, however, by the fact that the field is so young, and because we know so little about it compared to other fields, we are really never quite sure that the unreasonable schedule is, in fact, THAT unreasonable.


Research on the computing field is all about too often focused on theory to the exclusion of practice. That is, computing researches are very interested in developing new algorithms, new data representations, or new formal methods, but very seldom are they interested in the formalization of the best practices or the learning experience that be derived from worst practices.
That is an important failure of the computing research field.
<...> the invention of the steam engine preceded the development of the theory of thermodynamics, and the invention of the airplane preceded the development of theory of aerodynamics. In a newly-emerging feild - and what field in our time is more "newly-emerging" that software? - there is a great deal that theory can learn by studying practice (some theorists even say that "theory is the formalization of practice"), and computing theorists are not taking advantage of that possibility.


{Findings from the studies}
1. Many of the runway projects are (or were) "overly ambitious". It is well known in the field that large projects are problematic.
2. Most of the projects failed from a multiplicity of causes. There may or may not have been a dominant cause, but there were several problems contributing to many of the runaways.
3. Management problems were more frequently a dominant cause than technical problems. But see the list of surprising findings below.
4. Schedule overruns were more common (89 percent) then cost overruns (62 percent).

The surprising findings are:
1. Survey respondents though that there would be more runaways in the government and financial sectors, and fewer in service and manufacturing. But the survey findings found all such sectors equally suspectible.
2. Respondents were optimistic about the trend in runaways; 42 percent believed they would decrease in number, while only 8 percent felt they would increase.
3. The use of packaged software did not help in reducing the incidence of runaways. Of the runaway projects studied, 47 percent consisted of mixed custom and packaged software; 24 percent were custom software; and 22 percent were packaged software.
4. Runaway projects showed their true colors early in the project history. More than half started showing symptoms during system development, and 25 percent showed those symptoms during initial planning.
5. In spite of the above, visibility into the existence of a runaway came first of all from the project team (72 percent); only 19 percent were spotted initially at the senior management level.
6. Technology is dramatically increasing as a cause of runaways. "Technology is new to the organization" was the fourth most common problem in the runaways projects. See this topic discussed also under trends, below.
7. Risk management appears more and more frequently in the software management literature. But 55 percent of the runaway projects had not performed any risk management, and of those 38 percent who did (some respondees did not know whether it was used or not), half of them did not use the risk findings once the project was underway.

The trends are:
1. Companies were much more reluctant to discuss runaway project in 1995 than they were in 1989. The number of respondees in the newer study was half that of the earlier one in spite of the fact that the survey population (about 250 major organizations) was roughly the same.
2. Technology is a rapidly increasing cause of the runaway projects. Whereas in 1989 only 7 percent reported it as a cause, in 1995 the figure was 45 percent. (Interestingly, only 16 percent of respondents felt the technology was "wrong" for the job.)
	 \[KPMG 1995\} concludes "Technology is developing faster than the skills of the developers." (This conclusion will be questioned in what follows.)

<...>
There are two other conclusions that might be drawn from our own runaway reports in this book that are not found in the KPMG study. They are:
1. Early on, those responsible for our runaway project often bragged about the "breakthrough" nature of the project, either in terms of its business relevance or its technical (computing) advances. There seemed to be little or no understanding by those making such claims of the perilous course they were undertaking. <...>
2. Of all the technology problems noted earlier, the most dominant one in our own findings in this book is that performance is a frequent cause of failure. <...>


"Frankly, one of the challenges facing Microsoft is that many of its employees have not suffered much failure yet. Quite a few have never been involved with a project that didn't succeed. As a result, success may be taken for granted, which is dangerous... When you're failing, you're forced to be creative, to dig deep and think hard, night and day. Every company needs people who have been through that."
-- Bill Gates, in "The importance of Making Mistakes,"
USAur Magazine, July 1995

<...> runway projects could be categorized by their primary cause. These causes, in order of decreasing importance <...> are:
1. Project Objectives Not Fully Specified - 51%
2. Bad Planning and Estimating - 48%
3. Technology New to the Organization - 45%
4. Inadequate / No Project Management Methodology - 42%
5. Insufficient Senior Staff on the Team - 42%
6. Poor Performance by Suppliers of Hardware/Software - 42%
7. Other - Performance (Efficiency) Problems

**Project Objectives Not Fully Specified**
There is little doubt that project requirements are the single biggest cause of trouble on the software project front. Study after sutdy has found that where there is a failure, requirements problems are usually found at the heart of the matter.

Requirements problems occur when:
1. There are far too many of them. Huge projects fail far more often than smaller ones.
2. They are unstable. The user cannot decide what problem they really want to solve.
3. They are ambiguous. it is not possible to determine what the requirements really mean.
4. They are incomplete. There is insufficient information to allow a system to be built.

There are other possible problems with requirements, but the above list covers the most common ones. And, in fact, the first two rise head and shoulders above the others. Huge projects as well as projects whose requirements cannot be pinned down dominate the list of project runaway causes.

<...>

De-scoping the massive project to a more modest but achievable target appears now to be the way out of the morass.

**Bad planning and estimating**

<....> projects are often in schedule trouble simply because the estimate was far too optimistic to match the reality of the task to be performed.
<...>
"Hofstadter's Law": "Software development always takes longer than you think, even when you take into account Hofstadter's Law".

---

The business of creating new computer software - the programs that make computer work - is one of the most complex, painstaking even exasperating job around.
<...>
So difficult is the process that it baffle even such industry stars as Mitch Kapor, the founder of Lotus Development Corp., and Peter Miller, a well-known veteran.
<...>
Besides the inherent complexity of the work, there are other problems. Most software-development planning stinks. A joke in the industry is that programmers spend 90% of their time on the first 80% of a project, then 90% of the remaining time on the final 20%. And most design stinks too: Programmers either don't understand their customers well enough or load up products with features that please themselves but perplex everyone else.

---
<...> two truths in software design: Simplicity is paramount, and less is often more.

---
Jeff Gibbons, a 37-year-old senior programmer, says it is relatively easy to know how long it will take to add a feature, but hard to know how log it will take to turn a feature from bug-ridden code into a finished version.

---
**Technology New to the Organization**

New technology, often touted as the cure to software's problems, is frequently not the solution to, but the cause of, some of those problems.
<...>
In the stories that follow, the technologies in question were used on projects where:
- They did not scale up (it is important that the limitations of the new technologies - and they all have them - are well understood before they are used on a major project)
- They are a solution to the wrong problem (just because a technology is new does not mean it is appropriate for any problem you may be trying to solve).
- They did not have the required functional capability (on one of our stories below, the new technology could not address one facet of the user's problem. Not now, not ever!).

In other words, the mix of inexperienced people using immature technologies is a dangerous one.
<...>
The lessons learned on these projects are nicely presented in this collection of pithy quotes:
- "If you've got enough cinder blocks (untried technologies) in a rowboat, it's going to sink," even if not one of them alone would cause a failure.
- "Elegant solutions based on new technology often seem great in theory, but are difficult and expensive to learn and deploy"
- "The DMV's operation fell apart ... because of their prescribed remedy rather than the problem they had diagnosed."
- "If there appears to be more buzzword than substance, turn off the money spigot..."

---
Sweeping automation, when it works, can bring about greater efficiencies and reap big savings for a company. But the dark side of computerizing organizations is that often it doesn't work.

---
No software arrives in the marketplace bug-free and in final working form. Many problems surface only after extended use. The vendor provides fixes and adds functions and features - enhancements - when it developers complete them. The "maturing" process proceeds unpredictably.
<...>
Users should approach any vendor's claims with some skepticism. 

---
Large development projects frequently encounter legitimate, unexpected costs overruns. Rational compromises in such situations - perhaps a sharing of the extra expenses by developer and client for contract jobs or a budget revision for in-house projects - allow for happy endings to these situations.

---

I think it was here that I began really forming doubts about CS90. There's a strong buzzword flavor to this page. We've already seen an "engine", "reuse", "object-orientation", and "formal-approaches". None of these things necessarily characterize a project doomed for failure, of course, but the buzzword-to-reality ration is getting dangerously high.

---
... as someone wiser than I once said, "if it sounds too good to be true, it probably is"
<...>
When some crazy-sounding new proposal comes along, watch the buzzword quotient. If there appears to be more buzzword than substance to the proposal, turn off the money spigot. And don't let it flow again until those buzzwords are converted, perhaps in pilot studies with small (read "inexpensive") teams of key players, into something real, something with technical credibility.
If that doesn't happen, just think of it this way. Better to stay with your old, non-buzzword technology, than to appear on the pages of the news media. With your name paired in a headline with the word "Runaway".

---

**Inadequate / No Project Management Methodology**
It is clear from the preceding war stories in this chapter that no runaway project gets that way because of a single problem occurred. There may be technical snafus, or poor planning, or shaky requirements, but there are lots of other things going wrong as well.
One of the most prominent of those "lots of other things" is mis-begotten project management. After all, with suitable management it is often possible to avoid many technical snafus, improve planning, and stabilize requirements. The historic software engineering belief that poor management is the cause of the most software project failures is solidly founded.
<...>
Management, for all the knowledge and skills required of those in charge of software projects, in and will probably be an art. There is no blueprint, or recipe, or methodology that can convert a poor manager into a good one.

---
Some of those lessons are painfully obvious: The keys to success remain string leadership, technical competence and clearly stated goals and targets. Other nuggets of advice include the following:
- **Avoid big bangs.** "The words 'IT' and 'megaprojects' do not belong in the same sentence, " said Gopal K. Kapur, president of the Center for Project Management in San Ramon, Calif. He and others advise "chunking" projects into small, stand-alone. modules, that deliver value in themselves. "You need to ask, 'If the project were halted today, would we be able to use what we delivered?' If the answer is no, go back," said John Hammitt, former chief information officer at United Technologies Corp. and now a vice president at Giga Information Group in Cambridge, Mass.
- **Pin down committed leadership.** At the IRS, critics say the lack of clear project champions has been a big problem.

---
- **Use small time frames.** <...>
- **Make sure you have the talent to do the work.** <...>
- **Use your best people to manage subcontractors.** <...>
- **Set your customer service sights high.** <...>
- **Start fresh if necessary.** Don't be afraid to kill a runaway project, said Michael Hammer, president of Hammer and Company in Cambridge, Mass.
  "Burn it down and start again," he said. "By not doing that, you make the project worse."

---

**The Five-Risk Analysis** [of the technology projects before start - A.P.]
<...>
1. Financial Risk [can company accept the risk of loosing investments into the project - A.P.]
2. Technical Risk - ... the possibility that the project just cannot be accomplished because the supporting technology is not available. <...>
3. Project Risk - ... the possibility that the firm cannot execute the task. ... possibilities as the project is too large or complex or the skills and expertise of the staff do not match the needs of the project. Project risk has the broadest reach and thus demands detail along many different dimensions. Therefore, this section will be broken into five subsections.
	a. Management Philosophy and Vision
	b. Consultants
	c. Management Capability and Continuity
	d. Organizational Factors
	e. Other System Projects [as an overloading factor on the company - A.P.]
4. Functional Risk - ... the possibility that the completed project either does not do what the user wants or users needs have changed enough to make the system useless.
   <...> [system] functionality was additionally complex because it had to satisfy so many different groups.
5. Systemic Risk - ... the possibility that the system has such a large impact that it alters the environment and all assumptions about costs and benefits. ... very little can be done to combat it.

---

The idea behind the visionary is more than the strong guidance. The organization that sees upper management concerned and excited about its project will be motivated to perform to high standards.

---

**Insufficient Senior Staff on the Team**

One of the best known books in the software field is Software Engineering Economics, by Barry Boehm. On the cover of that book there is a bar chart that presents the most important factors that affect software productivity. There are things like programming languages, and tools, and methods, and lots of other information. But head and shoulders above the rest in terms of its impact on productivity is the quality of the people and the team doing the work.
<...>
Research studies over the years have found that individual software workers differ by factors of anywhere from 5:1 to 30:1 in their capabilities. Savvy software managers hire carefully and fire frequently in order to get and keep the best possible people: those 30:1 hotshots who can make the difference between a successful project and a failed one. It is no surprise that one of the important causes of runaway projects is the lack of appropriate people to do the job.
There are many ways of identifying those "appropriate people"; the research study from which we borrowed our categories used the term "senior staff." Certainly senior, experienced people bring enormous value to a project simply through that experience. Here, we choose to broaden the meaning of of "senior staff" to all those whose capabilities are considerably stronger than the norm.

---
[when] Things turned ugly [in a project failures], and when accusations begin flying, truth is usually the first casualty.

---

Companies must be careful not to underestimate the amount of training required to move to a new warehouse system, says Ron Gable, managing partner of Systecon Logistics, a distribution division of Coopers & Lybrand in Atlanta. "These kinds of virtually instantaneous change-overs result in all kind of chaos."

---
 
Principles for Managers of the Service Provider

1. In the business of software development, you always know when you start a project, but you never know when you will complete it. <...> When outlining the project schedule, be realistic and include an adequate "slack" time. Technical and other problems may occur. Problems often occur when a project involves interfacing two or more IS. Trying to entice the client with an unrealistically short schedule is not only unethical, but may eventually hurt your own effort.
2. When the phases must be sequential to assure quality, never start phase *n* before you resolve all of the problems of the phase *n-1*, and avoid shortcuts. <...>
3. Executives should not make any "calming" statements about the project status before they learn the facts. Making uncorroborated statements is not only unethical to the client; it may also send wrong signals to employees.
4. Adopt a Code of Professional Standards and communicate it to the employees. The code should detail what an employee is to do when experiencing a persistent problem with a systems under development, to whom he or she should report the problem, and what steps he or she should take if immediate supervisors are not responsive to complaints. A clear policy ensures that both managers and their employees know what is expected of them, and fosters more ethical behavior.
5. Most important: being dishonest may hurt your client, but it may also hurt you and your company. The financial impact of lost business because of a failure due to lies may prove much greater than the lost income from a single mishap. if it is not the monetary gain that drives your judgement but the reluctance to admit professional weakness, think again. Failure to disclose the real status of the project to the client may exacerbate the damage. Unfortunately, honesty if not always in one's economic self-interest. Often, there is economic incentive to lying (e.g., when the transaction is a one-shot deal and if information of the incident does not spread). But in the age of fast communication, especially in the IS industry, the news will travel fast. And your own employees may follow the bad example: they will lie to their superiors.

Principles for Employees

The first to observe technical problems are, usually, the employees: system analysts and programmers. Employees have an obligation both to their employer and the client. When you realize there is a persistent problem, notify your supervisor. <...>

Principles  for Clients
1. <...> Previous success does not guarantee success with the system that is developed for you. Check the status of the project periodically. If you do not have qualified personnel, hire an independent consultant to do that for you.
2. <...> Communicate to the developers exactly what your requirements from the new system are. You must realize that later modifications may result in a higher price and a latter completion date.
3. Pay attention to alerting signals. When executives and other employees of the developer are either massively dismissed or voluntarily looking for new positions, ask questions. When the rats abandon the ship, it is probably sinking.

---

An ancient proverb says: "You are a wise person if you do not make mistakes; you are a clever person if you make mistake but do not repeat it; you are a stupid person if you make a mistake and repeat it." If may be hard to be wise the first time around, but let us not be stupid, either. As professionals, we are expected to learn from our own and our colleagues' mistakes.
<...>
Large development projects rarely proceed exactly exactly as planned. This is true of IS development efforts as well. Management should be deeply involved in the progress of large-scale projects. If the professional team cannot overcome difficulties to comply with promised cost and timetable, it is the professionals' responsibility to disclose the difficulties to the client and mutually outline a resolution.

---
**Poor performance by supplier of hardware/software**

It is interesting to note, in the war stories that have preceded this section, that most of these runaways have occurred in spite of the best efforts of vendors, consultants, and service firms. In other words, these projects typically did not fail for a lack of (at least claimed) technical expertise. When the runaway projects sand, some of the best companies in the supplier community were on board!
That fact is something of surprise. It is easy to imagine that runaway projects are staffed with inept people who are in over their heads on the projects in question, and stubbornly resistant to the idea of obtaining help. That, from our stories to date, does not seem to be the case.
[There will be no stories here because] ... there was not enought blame in these stories to cause suppliers to be called a dominant cause of failure.

----

**Other - performance (efficiency) problems**
What is surprising, however, is that our "Other" category turned out to represent only one additional type of failure. Several of the war stories above, and in particular the two stories that follow, were plagued by efficiency problems. The developed software system simply could not operate quickly enough to solve the user's needs on a timely basis. In the software engineering community, such problems are called "performance" problems.
This is a surprising finding because it resurrects an issue that mosts of us in the software business thought had been put firmly to rest several decades ago. In the early days of computing, it was not unusual to find a software developer spending half of his or her time to write a program, and the other half in making it operate faster. Machine time was valuable; machines were relatively slow (compared to today), and good programmers were those who could not only build software but optimize it.
All that died, we thought, with the advent of cheap and huge powerful computers. <...>
Something had gone wrong with that belief. That change probably began with the popularity of interactive computing. [People expects results interactively now and don't want to wait for batch processing.]

---

**Software Runaway Remedies**

*At last I've found the secret that guarantees success. To err, and err, and err again, but less, and less, and less.*
*-- Ogden Nash*

---
For another thing, Jone's concern about "low productivity" is also arguable. One notable software expert, Tom DeMarco, has been known to respond to the statement that programmers are relatively unproductive with the question "compared to what?" We do know one thing about the production of software; it is deeply intellectual exercise, using no raw materials, producing a product that is constructed purely out of intellect. There are few if any comparable disciplines; although it is easy to say that five function points per month seem low, it is not at all easy to suggest that it should be, or could be made, higher.

---

**Issue management**
Risks are problems that are (or at least may be) anticipated prior to the beginning of project work. Issues, on the other hand, are problems that arise while the project is in process. If all issues could be identified in advance, they would probably be addressed as risks. But, given the complexity of software constructions, there will always be plenty of (surprise) issues arising as work proceeds.
<...>
It may strike you that issue management is a bit like "crisis management," the usually-derided practice of firefighting (addressing problems as they arise on a helter-skelter basis) rather than planning. But there are some significant differences:
1. There are some generic issues that project managers must watch for, and can plan for.
2. There are some measurement techniques that can be used to evaluate the status of both the generic issues as well as some project-specific issues.
3. There are some management techniques that can be applied to management by issue. Issue management works best in a climate of openness and helpfulness. That is, for issue management to work well, technologists must feel open to discuss issues with their managers as they arise, and the managers must demonstrate that they are capable of helping resolve the issues that are brought to their attention. In some organizations, the management response to issues is blame. Blame kills openness, which makes issue management impossible. In a climate of blame rather than openness, lying to management is a common reaction (to learn more about the unfortunately widespread practice of lying to management in the software field, see [Glass 1993].
<...>
It is not simple, of course, to manage by issues. There is no one management approach that those who manage by issue can utilize, because the issues that arise typically are extremely project-specific. Managers who manage by issue must be nimble, reacting to ongoing events rather than relying on a formula or methodology that will tell then what to do next.
But at the same time, as the (somewhat profane) bumper sticker says, "Shit happens.". Issues are the excrement that threaten to derail the software project; the manager who is not managing issues is probably not managing terribly well at all.
Fortunately, there is some advice regarding issues to supplement what might otherwise be an essentially ad hoc approach. in a military-funded guidebook [JLC 1996], issues form the basis for the management approach it proposes (the guidebook says, "Program issues and objectives guide the measurement process."). The guidebook suggests this taxonomy of issues:
1. schedule/progress (this is where "management by schedule" comes in, but as an issue)
2. resource/cost
3. growth/stability
4. product quality (here is where managing the product comes in)
5. development performance (this, growth/stability, and resource/cost subsume process)
6. technical adequacy

---

[Following software runaways] there is plenty of emotional destruction. A team of people, probably, operating in crunch mode on a death march quest, went down to defeat. Their hopes and plans for the future were probably dashed. There was probably blame and recrimination as the end approached, and relationships were bent or broken. Self-belief came under attach, and for some participants it was probably plower under.
I have participated on a lot of software projects. A small percentage of them have failed. <...> Perhaps because software is a product built from no physical resources, a product constructed purely out of intellect, it is especially devastating to the psyche when it fails.

---
