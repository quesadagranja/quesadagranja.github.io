---
layout: post
title: "The science behind 'Magic: The Gathering'"
date: 2021-08-02
image: /thumbs/mtg-logo.jpg
---
**Magic: The Gathering** (**MTG**) is a funny trading card game inspired by fantasy role-playing games. MTG emulates a combat between players' creatures, where not only their strength matters but also their abilities. Everything revolves around magic, which is present in the form of enchantments, artifacts, sorceries and many other exciting spells. There is a huge variety of creatures (and other spells) with which to compose your deck, roughly organized in five colors:

* **white** for angels, clerics and spells that evoke life;
* **black** for demons, vampires and other deadly spells;
* **red** for goblins, dragons, fire and explosions;
* **green** for elves and wild forest creatures;
* and **blue** for aquatic monsters and psychic spells.

**Uncolored** and **multi-colored** cards also exist. And cats, [many kinds of cats](https://hobbylark.com/card-games/best-cat-cards-mtg). The catalog is really huge, continually expanding since 1993 and can be consulted on [*Gatherer*](https://gatherer.wizards.com/Pages/Default.aspx), the MTG card database.

MTG, however, has a steep learning curve that makes it hard to understand at first. The complexity of its rules may be discouraging  (each card has its own instructions!) and, to top it off, it's often considered a *game for nerds*. If, despite that, you want to learn how to play, I recommend the computer version, [*MTG Arena*](https://magic.wizards.com/es/mtgarena), which is freemium, fully playable and has an excellent tutorial.

### Turing completeness of MTG
It has recently been ([Churchill et al.](https://arxiv.org/abs/1904.09828)) stated that **MTG is Turing-complete**. A system is Turing-complete when it can be used to simulate any **Turing machine**. Or, in other words, a Turing-complete system can solve any computational algorithm. So, MTG can be used to *program* things!

But let's take it step by step. Turing machines, proposed by the mathematician **Alan Turing** in 1936, are a class of **automata** able to take a program, run that program and show some result. A Turing machine is made up by four components:

1. an infinite one-dimensional **tape** divided into squares;
2. a finite alphabet of **symbols** for the tape;
3. a tape scanner with a finite number of **states** (as in [finite-state machines](https://en.wikipedia.org/wiki/Finite-state_machine)); and
4. a finite **instruction table** that tells what to do with each combination of scanner state and tape symbols.

This is how it works: the machine positions its tape scanner over a square on the tape and *reads* the symbol written on it. Then, based on the symbol read and the state of the tape scanner, the machine looks in the instruction table for

1. which new symbol to write in the square;
2. whether to move the tape one square to the left or to the right; and
3. whether to change the scanner state or stop (halt) the process.

If the process has not halted, the tape scanner reads the current square and so on.

With these simple rules it is possible to run any conceivable algorithm. However, the instruction table may not necessarily be easy to find, and the number of steps required to reach a result may not necessarily be small.

[This website](https://turingmaschine.klickagent.ch/einband/?&lang=en#__) illustrates step by step how some Turing machines compute simple operations between numbers. For example, they use a 2-symbol, 17-state machine to solve products of two integers represented by the unary numeral system (in which 5 is 11111). Solving [3 x 4](https://turingmaschine.klickagent.ch/einband/?&lang=en#3_*_4) requires 261 steps! Not so cool, considering that you have to count the twelve 1s to know the result.

### The prove
To prove that a programming language, device or system is **Turing-complete** all you have to do is to show that it can be used to implement a [**universal Turing machine**](https://www.i-programmer.info/programming/theory/10068-the-trick-of-the-mind-turing-complete.html?start=1) (UTM). That is, that it can simulate the behavior of **any other** Turing machine.

In general, a system that has a control flow that allows conditionals and loops, and has something that works as a memory is usually Turing-complete. All general-purpose programming languages such as C, Python or Java are Turing-complete. But accidentally, there are other systems that are also Turing-complete if you force them a little. This is the case of the zero-person [game of life](http://rendell-attic.org/gol/tm.htm), the videogames [*Minecraft*](https://www.youtube.com/watch?v=1X21HQphy6I) and [*Cities: Skylines*](https://kotaku.com/cities-skylines-map-becomes-a-poop-powered-calculator-1836398063), and even Microsoft Office  [*PowerPoint*](https://www.andrew.cmu.edu/user/twildenh/PowerPointTM/Paper.pdf), to mention a few.

In the following [XKCD comic strip](https://xkcd.com/505/), the starring sticksman creates a UTM only with rows of stones.

![](/img/a_bunch_of_rocks.png)
*<center><small>A bunch of rocks, by XKCD.</small></center>*

A set of very small UTMs are often used to prove that a system is Turing-complete. Among them are the ones found by Yurii Rogozhin in his paper [*Small universal Turing machines*](https://www.sciencedirect.com/science/article/pii/S0304397596000771) (1996). The smallest one, known as Rogozhin UTM(4, 6), has 4 states, 6 symbols and 22 instructions. <!--No lesser complexity is known.--> Other Rogozhin UTMs are UTM(15, 2), UTM(9, 3), UTM(6, 4), UTM(5, 5), UTM(3, 9), and UTM(2, 18). If you can embed one of these in your system, you've got it!

### What about MTG?

Churchill et al. embed the **Rogozhin UTM(2, 18)** in MTG. How they achieve this is very complex and requires a fairly high level of knowledge of MTG mechanics, but some key points are as follows.

* The **tape** is emulated by means of creature tokens. The *power/hardness* values of the creature tokens represent their position relative to the tape scanner, which is centered at 2/2. The color of the creatures represents whether the tape moves to the left (green) or to the right (white).
* The 18 **symbols** of the Turing machine are represented using 18 creature types: (1) Aetherborn, (2) Basilisk, (3) Cephalid, (4) Demon, (5) Elf, (6) Faerie, (7) Giant, (8) Harpy, (9) Illusion, (10) Juggernaut, (11) Kavu, (12) Leviathan, (13) Myr, (14) Noggle, (15) Orc, (16) Pegasus, (17) Rhino, and (18) Sliver. For example, a white 6/6 Kavu creature indicates that the 11th symbol is written on the 4th square to the right of the tape scanner.
* Certain cards, such as [*Rotlung Reanimator*](https://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=170415) (creates 2/2 black Zombie creature tokens), [*Artificial Evolution*](https://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=170318) (replaces the creature type), and [*Glamerdye*](https://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=180649) (replaces the creature color), are used to generate the creature that is needed at any time. This allows the **instruction table** to be fully implemented.
* Similarly, [*Cloak of Invisibility*](https://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=3329) allows creatures to be *phased in* and *phased out*, which makes it possible to implement the two **states** of the machine. In addition, other cards are required for other relevant purposes, such as halting the device, changing states, generating unlimited mana, and so on.

The following video explains the whole process in more detail:

<div class="youtube-video-container">
    <iframe 
        width="100%"
        src="https://www.youtube.com/embed/YzXoFldEux4"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
    ></iframe>
</div>

### Some final remarks
In a normal game you cannot arbitrarily play the cards you want. Indeed, you must prepare a deck of 60 cards and randomly draw a starting hand of 7 cards. However, Churchill et al. propose in their paper a sequence of cards to start with that is very unlikely to appear randomly in an initial hand. There are other weaknesses, such as all the time and space it would take to manually run the Turing machine with the MTG cards.

The exercise of embedding a universal Turing machine in _Magic: The Gathering_ is a very original theoretical work (that I admire) but, from my point of view, it's hardly transferable in a real game. 