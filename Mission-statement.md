```coffee
missionStatement = """
CodeCombat is an integral part of the programming community, like StackOverflow and GitHub.
It's where newcomers learn how useful, rewarding, and fun coding can be, and where
programmers of every skill level come to challenge and expand their abilities. It reflects
the best parts of the community: openness, collaboration, and continual learning.

It's also the funnest game in the universe.
"""

until missionStatement is true
  try
    @improve()
  catch error
    @improveHarder()
    # Possible infinite loop.
```

### A Community Project

CodeCombat lets players participate in the project at every level. If CodeCombat is to be a major part of the programming community, it must be a product of the community. The [/contribute page](http://codecombat.com/contribute) was the first step on this process, providing a general outline of what people can do to take part and make this project theirs. From building and testing levels, to translating the game and writing documentation, to helping other players and coding on this GitHub, we've already seen amazing contributions from all over the world--but there is yet much to do to reduce friction for contributors.

### A Startup

CodeCombat is also a for-profit technology company, founded in 2013 by [three comrades-in-code](http://codecombat.com/about) with seed funding from [Y Combinator](http://ycombinator.com/). "Why is a for-profit startup open-sourcing all of their code, art, and music?", you may ask. Because it's the right thing to do, software should be free, the community is important, and because we don't think keeping our source closed would be a competitive advantage. We hope to keep CodeCombat free to play and make money by helping our players find jobs, since that will align our players' interests with our own interests as a business. It's not a proven revenue model yet, though.

### The Best Way To Learn Programming

For every programmer out there, ninety-nine other people have dismissed programming as something that's just for geeks and never given it a second thought. Perhaps ten of those actually tried programming, but were immediately turned off by the fundamental problem that it's *really hard* to write code that makes a computer do anything interesting, so introductory programming materials tend to be either really hard or unappealing.

CodeCombat wants to solve that by making it really easy to do cool things with real code. By providing a game environment whereby everything becomes meaningful and intuitive ("I want my soldiers to jump over the pit, fight the ogres, and grab the gold") and a programming environment where it's easy to solve hard problems (visual worlds, live-coding, autocomplete, timeless debugging, helpful guides, timely hints, friendly error messages, and collaborative multiplayer), players get to write code that would be impossibly difficult to do if they were trying to muddle their way through a textual problem in a read-eval-print-loop. They learn faster, have more fun, and learn from the beginning how much fun programming can be--for anyone, not just that one geek in a hundred.

### The Funnest Kind of Programming

Humans have rich sensory experiences through sight, hearing, touch, taste, and smell. We don't have senses for coding, though. So when you're on an epic coding rush, you don't actually feel the wind from your function executions rushing through your hair. You don't smell the fresh tang of your regular expressions warming in the sun. You don't hear that harmonious arpeggio of recursive functions echoing up and down the call stack. You don't see the verdant fields of strings concatenating together under beautiful blue modules. You don't taste the sweetness of a platter of HTTP 200 OK responses garnished with salty 304 Not Modified tidbits.

Why not? Why can't the thrill of writing a correct algorithm feel as sensorily rich as that of a performing a triple-backflip into a pool of chocolates, orchids, and bunnies while a choir of angels sing? Not fair! Stupid physical limitations.

We can't blow wind in your hair or make network traffic taste good. What we can do, though, is make programming richer. Writing a graph partitioning algorithm is fun, but writing it as your troops rally around you, the clash of steel rings in the air, and the fate of the kingdom rests on your wizardly magic--now that's what we're talking about. Now add in other wizards, friendly and hostile, all in pitched battle as lightning flies under your fingertips. This is what coding should feel like.

We want developers to be playing CodeCombat instead of Call of Duty. We want you to practice your skills in our 2.5-dimensional battlefields, not the sterile stdin of TopCoder. We want to make programming feel like the magic that it is. So put on your robe and wizard hat and join us!