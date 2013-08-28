#Intro
Chris Price
Maybe I can teach you what *Matryoshka* dolls are, maybe a little about git or bitcoin, or maybe, just the limits of metaphor stretching...
@100pxls
http://scottlogic.com/blog/cprice
http://github.com/chrisprice

#Matryoshka Dolls

I'm sure you've seen them before, more commonly referred to as Russian dolls, each doll opens up to reveal another progressively smaller doll within. However, where most folk see cute tiny dolls, having spent too much time reading about bitcoin I saw a very elegant tamper-proof sequence...

#Sequences

A sequence is an ordered collection of things. They're everywhere from the letters of the alphabet to the colours of the rainbow, or more topically, from a series of commits in git to blocks of transactions in bitcoin. The important thing is that a sequence is not just a collection, but also the order in which they occur. The branch history in git can look enough of a mess without losing all sense of order!

#Tampering

So, how can we stop that happening? Or stop someone going back and fiddling the order of your bitcoin transactions?

Thinking back to the Matryoshka dolls, let's pretend I was presented with a nested sequence of dolls and that whoever nested the dolls choose them from a pool of coloured dolls. Just by keeping a hold of the outermost doll, I could guarantee that the sequence of those dolls couldn't change. Obviously there's nothing to stop someone bopping me over the head and grabbing the doll out of my cold dead fingers but at that point I'm probably beyond caring!

Put another way, just by having a copy of the very latest commit I would know that no one would be able to change the commits that proceeded it without me knowing, or by having a copy of the latest transaction block I know that the transactions before it can't be changed without me knowing.

There is one problem with this metaphor though

sequence of ust by keeping a hold of the outer doll you'd be able to guarantee that I couldn't change the sequence of those dolls.
So, the thing that had caught my attention looking at the Matryoshka dolls was that if you gave me a stack of dolls, just by keeping a hold of the outer doll, I know that you, or anyone else, can't change the sequence without me knowing. In order to change the sequence you would need to open the doll which I'm holding. We've solved the problem of a secure sequence/history but at a price, every state we add to the sequence comes at a greater and greater storage cost, we'll very quickly run out of space.

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
