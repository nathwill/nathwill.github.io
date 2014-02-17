---
layout: post
title: 'Uprooting Unity: In which the pursuit of profit costs Ubuntu big'
categories: amazon ubuntu unity
---

As I'm sure everyone who reads Linux news has heard by now, Ubuntu has introduced Amazon product results with the Unity Dash, and provoked quite an uproar from the community as a result. But is this another case of a few over-reactive, FUD-mongering freetards? Or, has Canonical finally gone too far in asserting its corporate goals in the design of their ambitious Linux desktop OS?

Let's start with a review of what's happened to date.

# Why all the ruckus?

So, it's one thing to say that Ubuntu now shows shopping search results, and it's another thing to actually see what that means. You should [take a look](http://i.imgur.com/DxHu5.jpg) at exactly what's going on.

The introduction of the 'unity-lens-shopping' package in 12.10 causes searches  in the Unity Dash Home Lens to query a Canonical-provided API that provides relevant search results from e-commerce giant Amazon, though plans are supposedly in the works to include results from other merchants as well.

As shipped, this feature is enabled by default, and no graphical method of disabling these results is provided, beyond removing the unity-lens-shopping package in the Ubuntu Software Center.

# Generating controversy and responding callously

As seen in the comments on [news](http://yro.slashdot.org/story/12/09/22/1319216/ubuntu-will-now-have-amazon-ads-pre-installed) [sites](http://news.ycombinator.com/item?id=4558049) reporting the issue, user response has not been as positive as Canonical may have hoped. Many Ubuntu users and observers have raised concerns around [security](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054677), [privacy](https://bugs.launchpad.net/unity-lens-shopping/+bug/1054741), and [control](https://bugs.launchpad.net/ubuntu/+source/unity-lens-shopping/+bug/1054746). Some have even gone so far as to call the change "adware".

On the flip side of the debate, vocal Ubuntu die-hard Benjamin Kerensa (a friend of mine) has responded by [calling their concerns](http://benjaminkerensa.com/2012/09/24/unity-shopping-lens-privacy-security-and-fud) sensationalist FUD. The Ubuntu community leader, Jono Bacon [attributed concerns](http://www.jonobacon.org/2012/09/23/on-the-recent-dash-improvements/) over the feature to fundamentalist objections to generating revenue from an open source product. Founder and self-appointed-benevolent-dictator-for-life, Mark Shuttleworth, has [asked](http://www.markshuttleworth.com/archives/1182) that everyone just "Chill out", because the design is still under heavy development, and is not in its final form. In regards to user concerns about sending search terms to Canonical, Mark responded, _"Don’t trust us? Erm, we have root."_

# What the hell is actually going on here?

As is often the case when something controversial happens in the Linux world, pretty soon, accusations and recriminations start flying back and forth and it's easy to lose track of who said what, and when. Let's look at user concerns, and examine the official responses from Canonical spokesmen.

## 1. Why are you putting ads in Ubuntu?

Many in the Ubuntu user community have raised concerns over having commercial products incorporated into the OS, calling them advertisements and saying that the feature constitutes Ubuntu becoming "adware".

Canonical has denied the charge, disputing labelling the results as ads due to their not being "paid placement". Additionally, they have accused users of being fundamentally opposed to making money from open source, as Canonical does through its affiliate relationship with the vendors whose products are shown in response to user searches.

**Evaluating Claims:** Amazons own [affiliate developer site](https://affiliate-program.amazon.com/gp/advertising/api/detail/main.html) refers to the affiliate relationship as advertising, so Canonical isn't fooling anybody here. Self-appointed-benevolent-dictator-for-life? Looks more like semi-benevolent-ruler-of-male-bovine-defecation to me.

But does this make Ubuntu adware? Dictionary.com [defines adware](http://dictionary.reference.com/browse/adware) as:

> 1. software that displays advertisements and is integrated into another program offered at no charge or at low cost

Hmmm, it seems it does.

As far as users having fundamental objections to Ubuntu making money, this is the purest kind of political misdirection. It avoids talking about the issue altogether, instead appealing to a users emotions. The subtext here is: "Don't you want us to succeed?", and "Why are you so closed minded?" I can't speak for everyone, but it's pretty reasonable to assume that if a person is using Ubuntu, they want it to succeed.

Any reasonable person understands that keeping a project the size of Ubuntu going takes money, and ideally that money comes from sustainable revenue sources like the sale of Ubuntu-themed swag, service and support subscriptions and, yes, affiliate revenue. As a person who understands the financial considerations, I've been happy to give Canonical money for services like Ubuntu One Storage and Ubuntu One Music Streaming over the years, and I buy music from the Ubuntu Music Store, despite the availability of cheaper and, arguably, better products in the same space (Dropbox, anyone?).

**Verdict:** It's time to stop mincing words, Canonical. Drop the double-speak and own up to embedding ads in Unity.

## 2. This constitutes a violation of privacy

As noted in the bugs linked to above, some have raised security/privacy concerns over the shopping lens, specifically: a) queries are not encrypted, and b) Amazon and Canonical end up with sufficient data to analyse user behaviour, in a context where users have a reasonable expectation of privacy.

Canonical has responded to the first concern by quickly incorporating secure queries to the product search API. Kudos; though whether this should ever have landed without is another matter entirely.

They also [denied](http://www.markshuttleworth.com/archives/1182) that information on queries was shared with Amazon, and asserted that Canonical having records of user queries isn't an issue, because they're already a trusted entity, who has root through the update mechanism.

**Evaluating Claims:** This is probably the issue that's seen the most attention in the debate, both because of the interest in the exact mechanism, and the relevance of the implementation to the question of who's being informed of user searches.

As discussed by [Ben Kerensa](http://benjaminkerensa.com/2012/09/25/technical-diagram-of-how-unity-shopping-lens-likely-works) and [Etienne Perot](https://perot.me/ubuntu-privacy-blunder-over-amazon-ads-continues), Canonical has been walking a fine line in their response to the question of the spying issue, and is trying to sidestep the question entirely by only telling half the story, choosing to address only where user search queries are sent.

Ben and Etienne are correct in pointing out that the issue is more complex than Canonical is pretending, because although the queries are only sent to Canonical, the ad content is fetched directly from Amazon. So by the time those ads show up on the Dash, both companies are actually provided with data points to analyse.

<em>Verdict</em>: Despite assurances to the contrary, it's clear that the Unity Dash Home Lens is leaking information to at least 2 companies, in a context where users quite reasonably expect privacy to be default.

<strong>3. Then, there's the question of this <em>trust</em> issue.</strong>

Mark is right to point out that users implicitly trust Canonical by installing the software they provide. Though open source software is theoretically reviewed by many eyes, there have been several cases where a vulnerability or exploit is added to an open source project and escapes detection for quite a while before it is caught and removed. I certainly don't have time to read the source of all the programs I use daily.

There's something about this argument really sticks in my craw, though. It simultaneously fails to address and disparages the real concern. It also got me thinking, because even though it misses the point entirely, it goes straight to the heart of why this is upsetting the community, which is "Yes, I've trusted you with root. How are you handling the responsibility?"

Imagine that I've hired Canonical to do a job, to provide me with a user-friendly Free Software OS. I do, after all, pay them, both in terms of Ubuntu One subscriptions, and revenue sharing they collect from Google and the Ubuntu Music Store. So what's in the contract?

Here's the terms we're all well acquainted with:

{% highlight bash %}
We trust you have received the usual lecture from the local 
System Administrator. It usually boils down to these three 
things:
    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.
{% endhighlight %}

Ouch. Let's take them one at a time then, shall we?

_Respect the privacy of others._

I'm sorry, Canonical, but you've failed here. You effectively inserted a monitoring device into my operating system, without providing me warning that it was coming, clear instructions on how to disable it, or listening to our feedback when we objected to it. You also failed to take even _basic_ steps to protect my privacy before foisting it upon me, like encrypting the data you're harvesting before transferring it back to headquarters.

_Think before you type._

I really get the sense that the responses I've seen to user concerns were made defensively, rather than after consideration of the complaints. I don't blame any of the people involved, as it's hard to keep cool when people are accusing you of things you didn't intend to do. I know that everyone involved is a good person. Be that as it may, they're still accountable for those things, and I believe they ought to apologise to the community for the misleading responses and accusations of fundamentalism.

_With great power comes great responsibility._

Herein lies the crux of the matter. By installing Ubuntu, we give Canonical the power to do things against our interest, but with the understanding and expectation that they _won't_, that they'll behave responsibly with that power. At its core, the protest and vehemence over the ubuntu-lens-shopping by privacy advocates and concerned users is due to perceptions that Canonical has misused that power to do something that is more in their own interest than in the interest of users.

# Conclusion: Canonical, you're fired!
As an Ubuntu user, contributor, and advocate, I _fucking *hate* this_, but the only reasonable conclusion I can reach as a conscientious person who believes in privacy, security, and control (I am a Linux user, after all) is that I need to revoke privileges from an entity who has failed to live up to their end of the bargain.

This article was written from a fresh install of Fedora, and I don't anticipate going back to Ubuntu any time soon. To my friends within Canonical and the Ubuntu community, I thank you for the wonderful experiences and opportunities, and I wish you luck as you continue to pursue success as a FOSS desktop operating system.
