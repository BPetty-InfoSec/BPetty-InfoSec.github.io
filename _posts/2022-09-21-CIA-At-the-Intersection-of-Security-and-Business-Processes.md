---
layout: post
title: "CIA: At the Intersection of Security and Business Processes"
category: Security Thoughts
tags: infosec cybersecurity confidentiality availability integrity business usability
---
## Summary
Fair warning: I've had less than 2 hours of sleep, and this may ramble a bit. See the Table of Contents on the right sidebar to skip to sections.

The CIA triad is something that we all pay attention to in this industry. If you've been to college for #InfoSec then you've had it drummed into you from almost day 1. If you learned in other ways, I seriously doubt that you've managed to avoid hearing/learning about the CIA Triad at some point in time. It's ubiquitous enough that you can find it mentioned fairly casually and often on Twitter threads from both leaders of the industry as well as newbies (Hi!).

----

## What is the CIA Triad?
The CIA Triad is kind of a basis of what security is, and is (naturally) made up of three parts:
1. Confidentiality
2. Integrity
3. Availability
A successful security plan must take in to account all three of these categories. Simple, right? Well...no, not necessarily. Lets look at each of these in turn. I won't be going into a super amount of detail on these, just a brief, 1000-yard overview.

----

## Confidentiality
Confidentiality is what most people think of when they think of Cybersecurity. This is where we make sure that people who _aren't_ supposed to have access to information _don't_ have access to that information. Pretty basic, right?

Well...when do you need to think about confidentiality? (the answer is a generic _yes_) Do we worry about confidentiality when the data is being moved around or outside of the system? Of course. Do we care about protecting confidentiality when the data is sitting on our internal hard drives? You bet. Encryption is the most common way of thinking about confidentiality, as it (trys to) prevent access by unauthorized people.

Given that, this brings up another part of confidentiality: access control. If you want to keep data confidential, then in addition to encrypting the data "at rest" and "in motion", you might also want to deny access to the data at all. This is where the Identity and Access Management (IAM) policies for the company come into play.

----

## Integrity
Integrity is the part of security that doesn't get thought of as much by people outside of the industry, at least anecdotally from what I've seen. Data integrity refers to preventing unauthorized modifications to data. Encryption and IAM plays a role in this as well, attempting to prevent unauthorized modification. Consider the sharing of research for, I don't know, vaccines. What would happen if someone changed the proportions of the ingredients (no, I am not a virologist, work with me here) to something that is fatal when administered to humans? Well, if there are good integrity checks, then hopefully nothing. First, the data should be encrypted at rest and in transit, making it more difficult to modify. Further, nobody except the people who need to have access to that information should be allowed to view it at all, per the IAM policy. Finally, the information should be audited in some way. This can be a manual audit, just to make sure that what comes through makes sense (the common sense check should always occur), or it could be something like comparing a hash of the original file to a hash of the file that arrives. This would reveal any tampering or alterations that have occurred. It wouldn't show _what_ had changed, however, just that it _had_ changed since it was originally sent. Integrity of data is critical to any business process, and so it's a leg of the Triad.

----

## Availability
This is probably the most-overlooked leg of the triad, at least from what I have seen from people. You can have the best security in the world, with data that is locked up like a safe in the middle of Fort Knox, and access to it provided to only two people, who all have to authenticate via a PIN number, a passphrase, retina scan, voice print, and a hardware token, with ongoing authentication via typing patterns and diction scanning. You can have it hashed in three different formats, so that changes are always noticed, immediately, and the system might even roll it back to a previous, matching version if it detects a change. (This...is not a good idea or setup, by the way...it's overkill, which is part of the point. Stick with me here.) Every one of those controls is a potential single point of failure. That is...bad, especially when you're talking about complex technological controls. Also...have you made sure that those two people who need to access the data _can_ actually get to it when they need to? This is where availability comes in. You can have "bulletproof" (ha) security, but if nobody can access their data when they need it, you not only don't have security, but you don't have a product. Businesses, naturally, aren't fans of this sort of thing. Securing your data and infrastructure is important, but if you can't use it, then it's a waste of time and money.

----

## Which is the most important?
You'll find in some college classes that the correct answer is "All legs of the triad are equally important, and should have equal attention paid to implementation." Yeah, that's kind of bullshit. The real answer is: It depends. Security isn't just about making things harder to mess up by threat actors or accident, it's _primarily_ about doing those things _while also maintaining usability_. A business isn't going to pay you (or shouldn't) if you "secure" their data and networks, but then the business is unable to function. How did that help? Sure, they won't get sued or take reputational damage from a data breach...but they're going to get sued and take reputational damage from _the service that people are paying for not being available_. One thing I see a lot of people lose sight of is the Cybersecurity is a business function. It doesn't exist in a vacuum, and it _has_ to play well with the rest of the business. Take the example under "Availability" just above: do you really think that those two people who have to jump through all of those hoops just to access, much less make changes to, that super-important data haven't found a way to copy that data, work on it on their own workstations and email/message back and forth to work collaboratively with each other? Yeah, I give that 1-2 days, a work week, tops, before that happens. Simply put, if you make things too difficult for people to easily use, then they'll look for ways to circumvent your controls. These aren't "malicious insiders" or "threat actors"...these are people trying to do their jobs, which they are also (I hope) being paid for..._and you are making their life harder_. That just isn't OK.

----

## Cybersecurity and Business
Most of us are going to be paid by a business to do cybersecurity work for them at some point. This may be as an employee, a contractor, a consultant, or whatever you want to call yourself: we are offering services and/or products to secure a business. This is against both internal and external threats. Some of those threats are honestly accidental. Some are the result of faulty notions or even a simple oversight. Some, naturally, are genuinely malicious. We have lots of different ways to address those issues. That's the whole reason for NIST and other frameworks, after all. That said, there has to be a balance.

I don't have a whole lot of experience in InfoSec. I _do_, however, have a whole lot of experience in business, management, project management, HR, sales, tech support, and the like. What I can tell you from that experience is this: they don't really care. Sure, some individuals do in the higher echelons of the company that will have to approve any new expenditures, but the company itself _does not care_. The company exists to make money for the owner or the shareholders. That's it. Remember that, and pitch your ideas with that in mind. This is where the "divide" comes in between the line staff, the middle management, and those in the C-Suites. Small changes might be able to be approved by middle management, provided that they have the budget and freedom to make those sorts of changes. Anything big, though, and it's going to get kicked up the food chain. Most of those people don't know you, and don't really know what you do. They are going to evaluate anything that you propose in a few different ways.

- Cost/Benefit Analysis:
	+ What does this proposal do for me/the company?
	+ What is this going to cost?
	+ What is this potentially going to cost us if we _don't_ follow this proposal (<- Lean into this one!)
- Productivity:
	+ Is this going to hamper productivity?
	+ If so, how much?
	+ Is this going to make _my_ workday more difficult/frustrating?
- Legal:
	+ Is doing this going to get us sued?
	+ Is _not_ doing this going to open us up to liability?
	+ Does this "check a box" for regulatory compliance?
	+ Is this a better thing than what compliance mandates, but we're going to have to explain it on every audit? (Here's looking at you, PCI-DSS, and your "wonderfully" antiquated password policies and practices)
- Is this person going to shut up without me firing them?
- How will approving/denying this affect _my_ standing in the company and in society if word gets out?
- How does doing/not doing this reflect on the company?

This can give you some pretty good ideas on how to pitch a new proposal. Make it beneficial to the company's public image, emphasize reputational and legal risks of _not_ implementing the new solution, and make sure that costs can be kept as low as possible and that productivity is minimally impacted, unless you find the unicorn control that increases both security _and_ productivity...that one's generally get the green light.

----

## Cool, but really...Which is the most important?
Again, it depends. From a security practitioner standpoint, we frequently focus on Confidentiality and Integrity as a knee-jerk reaction. It's right there in the acronym: CIA. That's the standard way of looking at it. While individual executives might not feel this way, a board that doesn't really understand security, and just wants to not be in legal jeopardy, not lose repuation publically, and spend as little as possible to get that way while still being able to use their product/service. For a business...even fintech businesses that have so many regulations on confidentiality (which is a big part of _why_ those regulations exist...), the order is really kind of reversed. AIC, if you will. From a business perspective:
- Availability: Can my employees or customers access what they need to in order for them to make/provide me with money?
	+ If services, internal or external, are not easily accessible, this immediately affects the business' bottom line.
	+ Would you pay for a service that you couldn't use?
	+ If you were an employee, if using something was a massive pain in the butt that took forever and broke your flow, would you not look for ways around using it?
- Integrity: Is this the right information?
	+ We're going to lose money if people mess up our stuff
- Confidentiality: Dang regulations making things hard...
	+ Legal trouble if we have a data leak with PII in it, and we were negligent in storing the data.
	+ Worse, the _reputation_ hit when it goes public!

----

## So how do we work with this?
So our job is to make sure that we balance all of these needs. Not everything has to be secured. Try to figure out what the company's risk tolerance is. Find out what is most important to them, and what they don't care about. Learn about all of the regulatory hurdles that the company faces. Then, don't propose a new control or process as something to fix a potential security problem. Remember: most of the actual decisionmakers either don't know what you're talking about, don't care, or both. Make it like a business proposal.

```This process will lead to better compliance with PCI-DSS requirements and should reduce the amount of time and personnel that we have to assign to our normal audits. The process itself is business-neutral, and can be implemented behind the scenes without any direct impact, positive or negative, on productivity and employee workflow. Not implementing this or some other process to cover [here are the technical parts where their eyes glaze over] will lead to a high risk of non-compliance, with legal and reputational damage far beyond the cost of implementation in the case of a security breach in this manner.```

(Yes, this is off the cuff. No, it's not for a specific product, which makes it difficult to write anything decent)

Tie the control or process that you're pushing to how it benefits the business, and tie the _lack_ of that product or service to a detriment to a business. In hospitality and sales, this is the difference between features and benefits. A feature is just something cool that you have or offer. A benefit, however, is a feature that is specifically good for your client/customer. Naturally, benefits are going to weigh more heavily into their purchase/expenditure decisions.

----

## Conclusion
What have we talked about? The CIA triad is important to consider when coming up with controls. Also, our perception as security practitioners is very different from those who run/own the businesses that we work for. Our priorities are different. In order to be successful in a business, we have to be able to present our proposals in such a way that it not only makes sense to the person, but also how it benefits them personally or the company. Think about talking security to your CEO. If you don't work for a security-focused company, they aren't going to know what the hell you're talking about. The CISO? Maybe, it depends on the CISO, but generally they'll at least speak the language. You have to meet people where they are, and talk to them in a way that they can understand. That's why I say that soft skills are _more_ important than technical skills in a lot of ways. Sure, you need to have the tech chops, but if you can't communicate it...it will never matter.