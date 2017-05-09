Before writing the D3 code, I had to pull out the tweets, find their coordinates, and set up sentiment.

Pulling out the tweets by using [PubNub](https://www.pubnub.com/developers/realtime-data-streams/twitter-stream/)
I added the flowing code in the indext.html 
```
<script src="https://cdn.pubnub.com/pubnub.min.js"></script>
```
I also add the flowing code in the viz.js
```
var channel = "pubnub-twitter";
```
