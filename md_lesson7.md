How to insert doc into collectio 
1.insert one 

db.<collection>.insertOne()
db.grades.insertOne()
grades is a collection 
if doesn't exist it automatically creates one 

2.insert many 

db.<collection>.insertMany([
<doc 1>,
<doc 2>,
<doc 3>
])


2. Finding documents in a mongoDB collection
find()
db.<collections>.find()

db.zips.find()

it for more docs

to retrieve specific doc in collection 
: eq

specific syntax 


db.zips.find({state:"AZ"})

db.<collections>.find({city:{$in:["PHOENIX","HICAGO"]}})


#Comparision operators 
$gt - greater then 
$lt - less then 
$lte - less then equal 
$gte - greater then equal 

<field> : { <operator> : <value> }


$gt: 
returns doc where the field greather then the specified value 
ex: db.sales.find({ "items.price": { $gt: 50}})
similarly lt,gte and lte


