


# Basics


**CRUD operation**



**Insert**
	db.collection.insertOne()
	db.collection.insertMany()

**Find**
	db.colleciton.find(,)
	db.collection.findOne(,)	

**Update**
	db.collection.update(,)
	db.collection.update(,,{upsert: true})

**Remove**
	db.colleciton.remove(,)

# Queries and Aggregation


aggregation pipeline: 

input: docs enter pipeline
stage-by-stage processing: each stage transforms or processes the documents
output: the final transformed documents are returned


average = 

db.sales.aggregate([
		
		$group: {
			_id: null
			averageQuantity: {$avg: "$quantity"}
		}

])

see hoe firstly its **$group** ed

# $avg
# $max
# $min

or
# $count

db.sales.aggregate([
{
	$count:"totalSales"
}
])


db.sales.aggregae([
	{
		$match:{product: "A"}
	},
	{
			$count: "totalSales"
	}
])








Replication & sharding and Review