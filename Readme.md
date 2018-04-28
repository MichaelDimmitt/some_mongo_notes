<pre>
mongo terminal -
db.createCollection("code_review") 
db.code_review.insert( { repository: "reactjs-app", commit: "https://github.com/americanman/reactjs-app/commit/2cc6aadfea9a746de3629f0f5acda16e8aa1b3ba" } )

package.json - needs to hold the older version "^2.2.33"
https://stackoverflow.com/questions/43779323/typeerror-db-collection-is-not-a-function

handler -
// sourced from, https://mongodb.github.io/node-mongodb-native/driver-articles/mongoclient.html
const MongoClient = require('mongodb').MongoClient

MongoClient.connect("mongodb://localhost:27017/test", function(err, db) {
    if(!err) {
      console.log("We are connected");
      db.collection('code_review').aggregate([ {$project:{commit:1}} ], function(err, collection) {res.json(collection)}) 
      db.close();
    }
  });
});
</pre>
