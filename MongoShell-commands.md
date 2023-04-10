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

ranjith> db.employee.insertOne({Name:"rahul", age:24,Company:"solartis",_id: "sjkdcbdv"})
{ acknowledged: true, insertedId: 'sjkdcbdv' }

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
  },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }
]


deleteOne()
it delete 1st key value document in collection
ranjith> db.employee.deleteOne({age:23})
{ acknowledged: true, deletedCount: 1 }

ranjith> db.employee.find()
[
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
  },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }
]

ranjith> db.employee.deleteMany({Company:"solartis"})
{ acknowledged: true, deletedCount: 4 }

db.employee.insertMany( [{
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
  },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }])
  
  
  ranjith> db.employee.find({Name:"arun"})
[
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis'
  }
]



ranjith> db.employee.find({age: {$gt:23}})
[
  {
    _id: ObjectId("64306c1cb57d7454e99a0419"),
    Name: 'Vaishnavi',
    age: 26,
    Company: 'solartis'
  },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }
]


ranjith> db.employee.updateOne({Name:"Vaishnavi"}, {$set:{team:"amt_dev"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
ranjith> db.employee.find()
[
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
    Company: 'solartis',
    team: 'amt_dev'
  },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis',
    team: 'amt_dev'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }
]
ranjith> db.employee.updateOne({Name:"arun"}, {$set:{team:"amt_dev"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 0,
  upsertedCount: 0
}
ranjith> db.employee.find()
[
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
    Company: 'solartis',
    team: 'amt_dev'
  },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis',
    team: 'amt_dev'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }
]
ranjith> db.employee.updateOne({Name:"arun"}, {$set:{team:"devops"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
ranjith> db.employee.find()
[
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
    Company: 'solartis',
    team: 'amt_dev'
  },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis',
    team: 'devops'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }
  
  
  ranjith> db.employee.replaceOne({Name:"Vaishnavi"}, {age:25})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
ranjith> db.employee.find()
[
  {
    _id: ObjectId("643060f91cc4888da334ee0b"),
    Name: 'Surya',
    age: 23,
    Company: 'solartis'
  },
  { _id: ObjectId("64306c1cb57d7454e99a0419"), age: 25 },
  {
    _id: ObjectId("643071c4b57d7454e99a041a"),
    Name: 'arun',
    age: 24,
    Company: 'solartis',
    team: 'devops'
  },
  { _id: 'sjkdcbdv', Name: 'rahul', age: 24, Company: 'solartis' }
]







airline> db.passanger.insertMany([
...   {
...     "name": "Max Schwarzmueller",
...     "age": 29
...   },
...   {
...     "name": "Manu Lorenz",
...     "age": 30
...   },
...   {
...     "name": "Chris Hayton",
...     "age": 35
...   },
...   {
...     "name": "Sandeep Kumar",
...     "age": 28
...   },
...   {
...     "name": "Maria Jones",
...     "age": 30
...   },
...   {
...     "name": "Alexandra Maier",
...     "age": 27
...   },
...   {
...     "name": "Dr. Phil Evans",
...     "age": 47
...   },
...   {
...     "name": "Sandra Brugge",
...     "age": 33
...   },
...   {
...     "name": "Elisabeth Mayr",
...     "age": 29
...   },
...   {
...     "name": "Frank Cube",
...     "age": 41
...   },
...   {
...     "name": "Karandeep Alun",
...     "age": 48
...   },
...   {
...     "name": "Michaela Drayer",
...     "age": 39
...   },
...   {
...     "name": "Bernd Hoftstadt",
...     "age": 22
...   },
...   {
...     "name": "Scott Tolib",
...     "age": 44
...   },
...   {
...     "name": "Freddy Melver",
...     "age": 41
...   },
...   {
...     "name": "Alexis Bohed",
...     "age": 35
...   },
...   {
...     "name": "Melanie Palace",
...     "age": 27
...   },
...   {
...     "name": "Armin Glutch",
...     "age": 35
...   },
...   {
...     "name": "Klaus Arber",
...     "age": 53
...   },
...   {
...     "name": "Albert Twostone",
...     "age": 68
...   },
...   {
...     "name": "Gordon Black",
...     "age": 38
...   }
... ])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("64309a54b57d7454e99a0425"),
    '1': ObjectId("64309a54b57d7454e99a0426"),
    '2': ObjectId("64309a54b57d7454e99a0427"),
    '3': ObjectId("64309a54b57d7454e99a0428"),
    '4': ObjectId("64309a54b57d7454e99a0429"),
    '5': ObjectId("64309a54b57d7454e99a042a"),
    '6': ObjectId("64309a54b57d7454e99a042b"),
    '7': ObjectId("64309a54b57d7454e99a042c"),
    '8': ObjectId("64309a54b57d7454e99a042d"),
    '9': ObjectId("64309a54b57d7454e99a042e"),
    '10': ObjectId("64309a54b57d7454e99a042f"),
    '11': ObjectId("64309a54b57d7454e99a0430"),
    '12': ObjectId("64309a54b57d7454e99a0431"),
    '13': ObjectId("64309a54b57d7454e99a0432"),
    '14': ObjectId("64309a54b57d7454e99a0433"),
    '15': ObjectId("64309a54b57d7454e99a0434"),
    '16': ObjectId("64309a54b57d7454e99a0435"),
    '17': ObjectId("64309a54b57d7454e99a0436"),
    '18': ObjectId("64309a54b57d7454e99a0437"),
    '19': ObjectId("64309a54b57d7454e99a0438"),
    '20': ObjectId("64309a54b57d7454e99a0439")
  }
}
airline> db.flight.insertMany([
...   {
...     "departureAirport": "MUC",
...     "arrivalAirport": "SFO",
...     "aircraft": "Airbus A380",
...     "distance": 12000,
...     "intercontinental": true
...   },
...   {
...     "departureAirport": "LHR",
...     "arrivalAirport": "TXL",
...     "aircraft": "Airbus A320",
...     "distance": 950,
...     "intercontinental": false
...   }
... ]
... )
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("64309ae1b57d7454e99a043a"),
    '1': ObjectId("64309ae1b57d7454e99a043b")
  }
}



airline> db.flight.updateMany({},{$set:{status:{description:"on_time",lastupdate:"1 hour ago"}}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}
airline> db.flight.find({}, {name:1})
[
  { _id: ObjectId("6430a190b57d7454e99a0451") },
  { _id: ObjectId("6430a190b57d7454e99a0452") }
]
airline> db.flight.find()
[
  {
    _id: ObjectId("6430a190b57d7454e99a0451"),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true,
    status: { description: 'on_time', lastupdate: '1 hour ago' }
  },
  {
    _id: ObjectId("6430a190b57d7454e99a0452"),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false,
    status: { description: 'on_time', lastupdate: '1 hour ago' }
  }
]
airline> db.flight.updateMany({},{$set:{status:{description:"on_time",lastupdate:"1 hour ago",detail:{responsible:"ranjith"}}}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}
airline> db.flight.find()
[
  {
    _id: ObjectId("6430a190b57d7454e99a0451"),
    departureAirport: 'MUC',
    arrivalAirport: 'SFO',
    aircraft: 'Airbus A380',
    distance: 12000,
    intercontinental: true,
    status: {
      description: 'on_time',
      lastupdate: '1 hour ago',
      detail: { responsible: 'ranjith' }
    }
  },
  {
    _id: ObjectId("6430a190b57d7454e99a0452"),
    departureAirport: 'LHR',
    arrivalAirport: 'TXL',
    aircraft: 'Airbus A320',
    distance: 950,
    intercontinental: false,
    status: {
      description: 'on_time',
      lastupdate: '1 hour ago',
      detail: { responsible: 'ranjith' }
    }
  }
]



