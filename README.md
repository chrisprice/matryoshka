#Intro
Chris Price
Work at SL, Technical Evangelist
Spend my days building research and trading apps for financial institutions.
But I'm more than a little obsessed with git and bitcoin...
Maybe I can teach you what *Matryoshka* dolls, maybe a little about git or bitcoin, or maybe, just the limits of metaphore stretching...
@100pxls
http://scottlogic.com/blog/cprice
http://github.com/chrisprice

#Matroushka Dolls
I'm sure you've seen them before, normally refered to as Russian dolls (unless you're trying to get a talk accepted), each doll opens up to reveal another progressively smaller doll within. The main attraction is normally the very cute tiny dolls nestled right in the center but I was struck by something else, you *could* use the dolls to represent a sequence that can't be tampered with.

#Sequences


A sequence can be made up of any number of states, where a state itself could be anything, a character, the contents of a file or even a financial transaction. But to keep things simple, and within my artistic reach, let's choose a sequence of colours - 

YELLOW -> BLUE  -> RED -> GREEN 

That's great but what makes it so special, why choose that over a list?

#Tampering
Well if you gave me a stack of dolls, just by keeping a hold of the outer doll, I know that you, or anyone else, can't change the sequence without me knowing (unless your name is Derren Brown). In order to change the sequence you would need to open the doll which I'm holding. We've solved the problem of a secure sequence/history but at a price, every state we add to the sequence comes at a greater and greater storage cost, we'll very quickly run out of space.

What if there was a way to make all the dolls the same size?

#Pictures
One way of doing that would be to stop nesting the dolls themselves, and use a photo of the next doll instead. Each doll can now be made just large enough to hold a picture, and we can store the next dolls in the sequence elsewhere until they're needed. Great, we've now massively reduced the overhead of adding a new state to the sequence (the dolls are now all the same size)!

But we've also inadvertently broke our secure sequence/history... We can only hold onto one doll at a time, if someone opens one of the dolls in the pool and swaps out it's photo we'll never know. What if there was someway of nesting the photos of the dolls?

#The Infinite Picture
That's a harder one to explain, so I'll talk you through the process -

* Take a photo of the last doll in the sequence
* But before placing it within the next doll, take a photo of it alongside the next doll then place it inside.
* Repeat

You can see that this could work nicely, every time we pull a doll from the pool we can check it against the photographs we have, if we spot a doll that doesn't match the photos we know it's been tampered with. However, it does have the downside that we're back where we started...these photos would now have to continually increase in resolution otherwise we wouldn't be able to make out the nested pictures.

But it felt like we were so close... surely there must be some clever maths that can save us?!

#Hashing
Luckily there's a whole branch of maths dedicated to this stuff, hashing functions. Unable to break entropy laws, they turn to an easily overlooked part of the problem, probability. What if I was willing to accept that each photograph might not be 100% accurate, but say 99.9999999% accurate - what difference could that make to it's size?

Surprisingly, the answer is an enormous difference, as soon as you stop dealing with absolutes you can hugely reduce the storage space. You'll have heard of if not seen common algorithms like SHA-1 and SHA-256 which produce 20 and 64 byte respectively.

These algorithms also have a final trick up their sleeves to thwart would be tamperers, their calculation is intentionally highly computationally intensive, that means that if you try to find something with an indistinguishable photograph/hash, you'll have to invest a huge amount of effort.

#The Point
Both git and BitCoin use this exact technique to help maintain a secure history despite being distributed across the web.

Git is used as the source control system for the linux kernel, which I'm sure one or two secretive agencies wouldn't turn down a chance to slip in some of their own code if they got the chance. You've probably already seen through the scraps of metaphor left, but in case it wasn't obvious the dolls represent a commit, their colour the state of the files and the photograph is the commit hash. The sequence is built up by each commit containing the commit hash of the previous commit.

BitCoin's need for a secure history is probably more obvious, if you can break it you can become very rich (or not, I did check the exchange rate 3mins ago before I came up but that doesn't really count for anything). The dolls in this case represent a block, their colour the transactions contained within that block and the photograph is the block hash. The sequence is build up by each block containing the block hash of the previous block.

#Conclusion
Thanks for listening
If I've tickled anyone's interest in how else probability can help with compression, then I'd recommend bloom filters for some truely mind blowing stuff
http://en.wikipedia.org/Bloom-Filters
Git Internals
Chris Price
@100pxls
http://scottlogic.com/blog/cprice
http://github.com/chrisprice
