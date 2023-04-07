>show dbs
used to show all db
admin     40.00 KiB
config   108.00 KiB
local     72.00 KiB
ranjith   72.00 KiB
use ranjith
create a new db or switch to existingdb
##db.collactionName.insertOne
ranjith>db.employee.insertOne({name:"ranjith", age:21})
{
  acknowledged: true,
  insertedId: ObjectId("64306c1cb57d7454e99a0419")
}
>db.employee.find()
[
  {
    _id: ObjectId("643058661cc4888da334ee0a"),
    Name: 'Ranjith',
    age: 23
  }
]

ranjith> db.employee.insertOne({Name:"surya", age:23,Company:"solartis"})
{
  acknowledged: true,
  insertedId: ObjectId("64306c1cb57d7454e99a0419")
}
ranjith> db.employee.insertOne({Name:"Vaishnavi", age:26,Company:"solartis"})
{
  acknowledged: true,
  insertedId: ObjectId("64306c1cb57d7454e99a0419")
}
[
  {
    _id: ObjectId("643058661cc4888da334ee0a"),
    Name: 'Ranjith',
    age: 23
  },
  {
    _id: ObjectId("643060f91cc4888da334ee0b"),
    Name: 'Surya',
    age: 23,
    Company: 'solartis'
  },
  {
    _id: ObjectId("64306c1cb57d7454e99a0419"),
    Name: 'Vaishnavi',
    age: 26,
    Company: 'solartis'
  }
]
