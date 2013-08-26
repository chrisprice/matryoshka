#Intro
Chris Price
Work at SL, Technical Evangelist
Spend my days building research and trading apps for financial institutions.
But I'm more than a little obsessed with git and bitcoin...
Maybe I can teach you what Matroushka dolls, maybe a little about git or bitcoin, or maybe, just the limits of metaphore stretching...
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
Well if you gave me a stack of dolls, just by keeping a hold of the outer doll, I know that you, or anyone else, can't change the sequence without me knowing (unless your name is Derren Brown). In order to change the sequence you would need to open the doll which I'm holding. We've solved the problem of a secure isequence/history but at a price, every state we add to the sequence comes at a greater and greater storage cost, we'll very quickly run out of space.

What if there was a way to make all the dolls the same size, is there a smaller token which we could use to represent a doll?

#Pictures
A photograph of the next doll could work as such a token, here you can see the process for reading the sequence. The first doll is opened, the photo is then used to find the next doll from the pool, which is then opened and so on. Great, we've now massively reduced the overhead of adding a new state to the sequence but we've also inadvertently broke our secure sequence/history... We can only hold onto one doll at a time, if someone opens one of the dolls in the pool and swaps out it's photo we'll never know. What if there was someway of including photo within the doll in the photo of the doll?

#The Infinite Picture
This time we'll run through the process for creating the nested photos starting with the last item. Nothing in the green doll, take a photo of the green doll for inside the red doll, so far so good. Now for the photo of the red doll we include the photo of the green doll in the corner, again so far so good. Now for the photo of the blue doll, we need the photo of the red doll in the corner which itself contains the photo of the green doll. I'm starting to spot a problem, either we keep the resolution of the photograph the same and lose the ability to see the deeply nested tokens thereby breaking our secure sequence/history or we have to progressively keep making the resolution higher and then we're back to our ever increasing storage cost problem...

But it felt like we were so close... surely there must be some clever maths that can save us?!

*Because each photo contains a representation of each doll before it in the sequence, if we hold onto the last doll no one can change any of the dolls*

#Hashing
How strange you should mention it?! There's a whole branch of maths dedicated to this stuff, hashing algorithms! Unable to break entropy laws, they turn to an easily overlooked part of the problem, probability. What if I was willing to accept that each photograph might not be 100% accurate, but say 99.9999999% accurate - what difference could that make to it's size? 

The answer you may be suprised to learn is an enormous difference, as soon as you stop dealing with absolutes you can hugely reduce the storage space. i

The final trick these algorithms play is to be highly compuationally intensive, that means that if you try to find something with an indistinquishable photograph/hash, you'll have to invest a huge amount of effort.

#The Point
Both git and BitCoin use this exact technique to maitain a secure history despite being distributed across the web. 

Git is used as the source control system for the linux kernel, which I'm sure one or two secretive agencies wouldn't turn down a chance to slip in some of their own code if they got the chance. You've probably already seen through the scraps of metaphore left, but in case it wasn't obvious the dolls represent a commit, their colour the state of the files and the photograph is the commit hash. The sequence is built up by each commit containing the commit hash of the previous commit.

BitCoin's need for a secure history is probably more obvious, if you can break it you can become very rich (or not, I did check the exchange rate 3mins ago before I came up but that doesn't really count for anything). The dolls in this case represent a block, their colour the transactions contained within that block and the phtograph is the block hash. The sequence is build up by each block containing the block hash of the previous block.

#Conclusion
Thanks for listening
If I've tickled anyone's interest in how else probability can help with compression, then I'd recommend bloom filters for some truely mind blowing stuff
http://en.wikipedia.org/Bloom-Filters
Git Internals
Chris Price
@100pxls
http://scottlogic.com/blog/cprice
http://github.com/chrisprice
