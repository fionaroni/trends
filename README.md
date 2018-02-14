# trends

This project develops a geographic visualization of twitter data across the United States

Phase 1: The Feelings in Tweets

Creates a data abstraction for Tweets, splits the text of a tweet into words, and calculates the amount of positive or negative feeling in a tweet.

Define a data abstraction for Tweets. To ensure that we do not violate abstraction barriers later in the project, we will create two different representations:

(A) The constructor make_tweet returns a Python list with the following items:

    text: string, the text of the tweet, all in lowercase
    time: datetime object, when the tweet was posted
    lat: a floating-point number, the latitude of the tweet's location
    lon: a floating-point number, the longitude of the tweet's location

(B) The alternate constructor make_tweet_fn returns a function that takes a string argument that is one of the keys above and returns the corresponding value.

_Phase 3: The Mood of the Nation_

In this phase, you will group tweets by their nearest state center and calculate the average positive or negative feeling in all the tweets associated with a state.

The name us_states is bound to a dictionary containing the shape of each U.S. state, keyed by its two-letter postal code.
**group_tweets_by_state** takes a sequence of tweets and returns a dictionary. The keys of the returned dictionary are state names (two-letter postal codes), and the values are lists of tweets that appear closer to that state's center than any other.

If a state does not have any tweets, you should not include it in the returned dictionary.

**average_sentiments** takes the dictionary returned by group_tweets_by_state and also returns a dictionary. The keys of the returned dictionary are the state names (two-letter postal codes), and the values are average sentiment values for all the tweets that have sentiment value in that state.

If a state has no tweets with sentiment values, leave it out of the returned dictionary entirely. Do not include a state with no sentiment using a zero sentiment value. Zero represents neutral sentiment, not unknown sentiment. States with unknown sentiment will appear gray, while states with neutral sentiment will appear white.

