




print the collection of called numbers


db.users.find()

db.users.find({"name"}:1) ascending order
db.users.find({"name"}:-1) descending order



db.users.find({ totalEpisodes: { $gt: 50} })


$or then 
different commands separated by {}
{} separated by,  

db.users.find({$or:[{"children":[]}, {"address.state":"FL"}]}, {name1,_id:0}})





{    $or[   {},{}   ]  }



$max

$min

$avg

$count

db.runcommand

