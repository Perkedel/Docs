# Transactional Actions

In a Save Account, items (more like Consequences) flow by Transaction. As you Requested an operation, the Game listens, Verify, and then Commence the Transaction.

e.g., a Transaction of Reward containing these items.

## Why Transactional?

As we have learned, F2P Gacha games makes changes to their game system. Especially, if an update involves changes on the prerequisites of a Requestable Action that compensates previous happened action, **it'd be very hell to track down how many the customers did those actions, therefore how much should they be compensated so the counts of those actions equals to as if all done only by this updates**.  
Simple games were using a Rudimentary item counter, without anything else. Therefore doing this Developers cannot make an adjustment without compensating the correctional consequences for actions done before. Update, and that's it, you lost so much, you could've waited, but that thing comes after the fact, no idea they repent or what.  
With Transactional system, Actions are recorded in your save file. This is the history of your Actions you did in the game, and what item you made.  
And if there is a change, especially corrects or edits the supposed consequences, they'll just need to update such **Type of Action**. Like, **Drinking Energy Cereal**, previously cost much Coins, no no longer. As it happened, it feels like those Coins we used to buy Cereals are all refunded. And btw now we just have to concern that limit per day that's all.

An example we can give is from Zenless Zone Zero Classic. Before the update, Coff Cafe costs this much Dennies (similar to DNB Coin in MultiTalent here.). At certain version, the update changed it by removing those cost, both onward and new. Had the game uses Rudimentary Item counter, it is not possible and all loses goes to the customer. But in reality **the update did compensate all Coff Cafe actions, from where you did it first time, to now, and for oncward!!!**. Idk how did they even do that, especially we could have it so many of them, and has to be done to over thousands or even millions of the cusomters / proxies playing that at that time. Then again, we trust this is easily possible thanks to the genius dev who make the Actions **Transactional**. Action, Record, Clarify.

## How Transactional Works

In the game, every item that goes in and out means Action. You are now Requesting an action to do something.

Action is done. You get this reward. Behind the scene, this action is just recorded. It never even count any inventory in the first place, heck, that's just an illusion. The whole game is fully a bunch of Action Records, that's it!

How does that Inventory system works now? **There's no such thing as Inventory anymore!** This menu now is just the summary of all Action Record you did for it. In total you got and lost these items as of now.

The reward you got is because of the Action Definition. Each different type gets you different *Rewards* quote on quote. Action Defition defines prerequisite, so before it works, you need to have this much numbers of item. Say, changes of the definition changed the prerequisite to as if your other action records makes it no longer enough as if done fresh. No big deal, **fuck it**, who cares! Don't even scrutinize your lack of action records of today's update, and why the fuck would you do that in first place, am i right? Should've made it cheaper like Coff Cafe did instead. So it's that.  

Btw, DOOM records demo originally by keypresses. That's why there is desync, if the game design from assets down to the component have changed. A compatibility level and other requirements therefore have been enforced since then. Just a slight change ruins it all and you must make it again designed for that new design. Compatibility Level adjusts the core mechanics of how the DOOMing works. Popularly, this CL system enforces engine to do the same was as it did back in 1995, of course with Modern Graphics, and makes all demos designed for that CL standardized carryable across all tournaments and engines / Source Ports.  
Such kind of keypress sequence system is what makes it equivalent to today's F2P games that wholely uses Transactional system. You did something, so that's your point. Wanna do the others, you must have the point at an exact spec first, or else you'll hit the wall, and shoot it tf you're doing, stuck yourself in the corner.  
When this of Transactional system is originally seems bad, coz let's be honest, they could've done it as Animation fully (side point, then how would this demo be scrutinizable to check if it's a cheat?), Transpirationally, it instead is useful as the Iteming there instead. So, that's the new job & purpose of the Transactional.

## Versioned

Too expensive to compensate for previous Transactions? Well, fuck you, stingy ass! But eh, since you insist, yess, you can do so to upset the players, or perhaps to prevent unwanted mess-up on their save i.e. severe incompatibilities and other fatal bugs who knows how it'd looked like.

In Action Definition, you can see a `Version` field and `Max Datetime` of it. Now, you can add a new version, and make changes to it. Then write in the `Start Datetime`, so compensation only happens to the Transaction made after that start datetime.

### Dispute of discompensations

So say, if a player disagree, then as a Customer Support, e.g., you can have their Save Account edited, to edit that Transaction so the version uses that new one instead, to make it as if it happened on that new version, while it's that old, **overriding the usual Datetime based Rewardings**.

The Transaction field `Override version` (default is empty) lets you to pick version for the Action Definition. Usually, Transaction rewards based on `Datetime` happened according to the Version defined in Action Definition. If the `Override version` is filled, the Transaction will rewards you based on that version instead of datetimed version.