# trends

This project develops a geographic visualization of twitter data across the United States

# Phase 1: The Feelings in Tweets

Creates a data abstraction for Tweets, splits the text of a tweet into words, and calculates the amount of positive or negative feeling in a tweet.

Define a data abstraction for Tweets. To ensure that we do not violate abstraction barriers later in the project, we will create two different representations:

(A) The constructor make_tweet returns a Python list with the following items:

    text: string, the text of the tweet, all in lowercase
    time: datetime object, when the tweet was posted
    lat: a floating-point number, the latitude of the tweet's location
    lon: a floating-point number, the longitude of the tweet's location

(B) The alternate constructor make_tweet_fn returns a function that takes a string argument that is one of the keys above and returns the corresponding value.

The missing selector and constructor functions for these two representations: tweet_text, tweet_time, tweet_location correspond to representation (A); make_tweet_fn corresponds to representation (B).

**tweet_location** returns a position. The constructors and selectors for this data abstraction can be found in geo.py.

The two representations created by **make_tweet** and **make_tweet_fn** do not need to work together, but each constructor should work with its corresponding selectors.

**analyze_tweet_sentiment** takes a tweet and returns a sentiment.

The **tweet_words** function combines the tweet_text selector and extract_words function from the previous questions to return a list of words in a tweet.

# Phase 2: The Geometry of Maps

This phase implements two functions that together determine the centers of U.S. states. The shape of a state is represented as a list of polygons. Some states (e.g. Hawaii) consist of multiple polygons, but most states (e.g. Colorado) consist of only one polygon (represented as a length-one list of polygons).

**find_centroid** takes a polygon and returns three values: the coordinates of its centroid and its area. The input polygon is represented as a list of position values that are consecutive vertices of its perimeter. The first vertex is always identical to the last.

The centroid of a two-dimensional shape is its center of balance, defined as the intersection of all straight lines that evenly divide the shape into equal-area halves. The **find_centroid** function returns the centroid coordinates and area of an individual polygon.

**find_state_center** takes a state represented by a list of polygons and returns a position, its centroid.

The centroid of a collection of polygons can be computed by geometric decomposition. The centroid of a shape is the weighted average of the centroids of its component polygons, weighted by their area.

# Phase 3: The Mood of the Nation

In this phase, you will group tweets by their nearest state center and calculate the average positive or negative feeling in all the tweets associated with a state.

* **us_states** is bound to a dictionary containing the shape of each U.S. state, keyed by its two-letter postal code.
* **group_tweets_by_state** takes a sequence of tweets and returns a dictionary. The keys of the returned dictionary are state names (two-letter postal codes), and the values are lists of tweets that appear closer to that state's center than any other.

If a state does not have any tweets, you should not include it in the returned dictionary.

**average_sentiments** takes the dictionary returned by group_tweets_by_state and also returns a dictionary. The keys of the returned dictionary are the state names (two-letter postal codes), and the values are average sentiment values for all the tweets that have sentiment value in that state.

If a state has no tweets with sentiment values, leave it out of the returned dictionary entirely. Do not include a state with no sentiment using a zero sentiment value. Zero represents neutral sentiment, not unknown sentiment. States with unknown sentiment will appear gray, while states with neutral sentiment will appear white.

