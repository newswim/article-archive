### What I think about when (and sometimes Why)

#### July 1, 2017

Yesterday I watched the video version of a podcast of a small company who had
recently adopted GraphQL after picking over a few alternatives. The question was posed
> If there is one thing you would like to see added to GraphQL, what would it be?

One of the engineers responded, "I know what I would want - an OT or CmRDT capability".

I hadn't heard of this yet, but a brief explanation and some googling made the idea
fairly clear: Send minimum messages over a socket to update a shared state which
all of the clients are interacting with.

Some examples are Google Docs, which has a [realtime API](https://developers.google.com/google-apps/realtime/overview)
which allows collaboration on any file hosted by Google Drive. Interesting.

I've been increasingly impressed with the incredible amount of tooling that
Google has been generating, from MLaaS, NLP, etc.

Several things from this interview jumped out:
- 2012 was referred as "the very early days"
- Meteor really was ahead of their time with oplog tailing and real-time multi-client
- Often the less reliant you are on a particular library the better
- Try to ditch your ORM if you're using GraphQL


#### July 3rd, 2017

There is so much Haskell to learn . . .