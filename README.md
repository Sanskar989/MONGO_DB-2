# MongoDB Aggregation Assignment –

```shell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\Users\Minfy.ABHINANDANKALLU> mongosh
Current Mongosh Log ID: 68383e173eac11547c6c4bcf
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.5.1
Using MongoDB:          8.0.9
Using Mongosh:          2.5.1

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/

------
   The server generated these startup warnings when booting
   2025-05-28T15:43:19.637+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

test> use ggregationAssignmentDB
switched to db ggregationAssignmentDB
ggregationAssignmentDB> db.products.insertMany([
  { name: "Laptop Pro", category: "Electronics", price: 1200, quantity: 10, tags: ["computer", "portable", "work"], date_added: new Date("2023-01-15T10:00:00Z"), supplier: { name: "TechGlobe", location: "USA" } },
  { name: "Wireless Mouse", category: "Electronics", price: 25, quantity: 100, tags: ["peripheral", "computer", "wireless"], date_added: new Date("2023-02-01T11:30:00Z"), supplier: { name: "GadgetPro", location: "China" } },
  { name: "Mechanical Keyboard", category: "Electronics", price: 75, quantity: 50, tags: ["peripheral", "computer", "mechanical"], date_added: new Date("2023-01-20T14:00:00Z"), supplier: { name: "TechGlobe", location: "USA" } },
  { name: "Cotton T-Shirt", category: "Apparel", price: 20, quantity: 200, tags: ["clothing", "cotton", "casual"], date_added: new Date("2023-03-10T09:00:00Z"), supplier: { name: "FashionHub", location: "India" } },
  { name: "Denim Jeans", category: "Apparel", price: 60, qua...   { name: "Denim Jeans", category: "Apparel", price: 60, quantity: 80, tags: ["clothing", "denim"], date_added: new Date("2023-03-01T16:45:00Z"), supplier: { name: "FashionHub", location: "India" } },
  { name: "Espresso Machine", category: "Home Goods", price: 250, quantity: 30, tags: ["kitchen", "appliance", "coffee"], date_added: new Date("2023-02-15T08:20:00Z"), supplier: { name: "HomeBest", location: "Germany" } },
  { name: "Smartwatch", category: "Electronics", price: 199, quantity: 25, tags: ["wearable", "gadget", "portable"], date_added: new Date("2023-04-01T12:00:00Z"), supplier: { name: "GadgetPro", location: "China" } },
  { name: "Leather Wallet", category: "Accessories", price: 45, quantity: 120, tags: ["fashion", "leather"], date_added: new Date("2023-03-20T10:10:00Z"), supplier: { name: "StyleCraft", location: "Italy" } },
  { name: "Yoga Mat", category: "Sports", price: 30, quantit...   { name: "Yoga Mat", category: "Sports", price: 30, quantity: 90, tags: ["fitness", "exercise"], date_added: new Date("2023-04-05T13:00:00Z"), supplier: { name: "ActiveLife", location: "USA" } },
  { name: "Bluetooth Speaker", category: "Electronics", price: 80, quantity: 60, tags: ["audio", "portable", "wireless"], date_added: new Date("2023-02-25T17:00:00Z"), supplier: { name: "SoundWave", location: "USA" } }
]);

{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68383fe53eac11547c6c4bd0'),
    '1': ObjectId('68383fe53eac11547c6c4bd1'),
    '2': ObjectId('68383fe53eac11547c6c4bd2'),
    '3': ObjectId('68383fe53eac11547c6c4bd3'),
    '4': ObjectId('68383fe53eac11547c6c4bd4'),
    '5': ObjectId('68383fe53eac11547c6c4bd5'),
    '6': ObjectId('68383fe53eac11547c6c4bd6'),
    '7': ObjectId('68383fe53eac11547c6c4bd7'),
    '8': ObjectId('68383fe53eac11547c6c4bd8'),
    '9': ObjectId('68383fe53eac11547c6c4bd9')
  }
}
ggregationAssignmentDB> show status
MongoshInvalidInputError: [COMMON-10001] 'status' is not a valid argument for "show".
ggregationAssignmentDB> db.products.aggregate([
  { $match: { category: "Electronics" } }
]);

[
  {
    _id: ObjectId('68383fe53eac11547c6c4bd0'),
    name: 'Laptop Pro',
    category: 'Electronics',
    price: 1200,
    quantity: 10,
    tags: [ 'computer', 'portable', 'work' ],
    date_added: ISODate('2023-01-15T10:00:00.000Z'),
    supplier: { name: 'TechGlobe', location: 'USA' }
  },
  {
    _id: ObjectId('68383fe53eac11547c6c4bd1'),
    name: 'Wireless Mouse',
    category: 'Electronics',
    price: 25,
    quantity: 100,
    tags: [ 'peripheral', 'computer', 'wireless' ],
    date_added: ISODate('2023-02-01T11:30:00.000Z'),
    supplier: { name: 'GadgetPro', location: 'China' }
  },
  {
    _id: ObjectId('68383fe53eac11547c6c4bd2'),
    name: 'Mechanical Keyboard',
    category: 'Electronics',
    price: 75,
    quantity: 50,
    tags: [ 'peripheral', 'computer', 'mechanical' ],
    date_added: ISODate('2023-01-20T14:00:00.000Z'),
    supplier: { name: 'TechGlobe', location: 'USA' }
  },
  {
    _id: ObjectId('68383fe53eac11547c6c4bd6'),
    name: 'Smartwatch',
    category: 'Electronics',
    price: 199,
    quantity: 25,
    tags: [ 'wearable', 'gadget', 'portable' ],
    date_added: ISODate('2023-04-01T12:00:00.000Z'),
    supplier: { name: 'GadgetPro', location: 'China' }
  },
  {
    _id: ObjectId('68383fe53eac11547c6c4bd9'),
    name: 'Bluetooth Speaker',
    category: 'Electronics',
    price: 80,
    quantity: 60,
    tags: [ 'audio', 'portable', 'wireless' ],
    date_added: ISODate('2023-02-25T17:00:00.000Z'),
    supplier: { name: 'SoundWave', location: 'USA' }
  }
]
ggregationAssignmentDB> db.products.aggregate([
  { $group: { _id: "$category", count: { $sum: 1 } } },
  { $sort: { _id: 1 } }            // optional, just for deterministic order
]);

[
  { _id: 'Accessories', count: 1 },
  { _id: 'Apparel', count: 2 },
  { _id: 'Electronics', count: 5 },
  { _id: 'Home Goods', count: 1 },
  { _id: 'Sports', count: 1 }
]
ggregationAssignmentDB> db.products.aggregate([
  { $project: { _id: 0, name: 1, price: 1 } },
  { $sort: { price: -1 } }
]);

[
  { name: 'Laptop Pro', price: 1200 },
  { name: 'Espresso Machine', price: 250 },
  { name: 'Smartwatch', price: 199 },
  { name: 'Bluetooth Speaker', price: 80 },
  { name: 'Mechanical Keyboard', price: 75 },
  { name: 'Denim Jeans', price: 60 },
  { name: 'Leather Wallet', price: 45 },
  { name: 'Yoga Mat', price: 30 },
  { name: 'Wireless Mouse', price: 25 },
  { name: 'Cotton T-Shirt', price: 20 }
]
ggregationAssignmentDB> db.products.aggregate([
  { $group: {
      _id: "$supplier.name",
      totalQuantity: { $sum: "$quantity" }
    }},
  { $sort: { _id: 1 } }
]);

[
  { _id: 'ActiveLife', totalQuantity: 90 },
  { _id: 'FashionHub', totalQuantity: 280 },
  { _id: 'GadgetPro', totalQuantity: 125 },
  { _id: 'HomeBest', totalQuantity: 30 },
  { _id: 'SoundWave', totalQuantity: 60 },
  { _id: 'StyleCraft', totalQuantity: 120 },
  { _id: 'TechGlobe', totalQuantity: 60 }
]
ggregationAssignmentDB> db.products.aggregate([
  { $unwind: "$tags" },
  { $group: {
      _id: "$tags",
      averagePrice: { $avg: "$price" }
    }},
  { $sort: { averagePrice: -1 } }
]);

[
  { _id: 'work', averagePrice: 1200 },
  { _id: 'portable', averagePrice: 493 },
  { _id: 'computer', averagePrice: 433.3333333333333 },
  { _id: 'appliance', averagePrice: 250 },
  { _id: 'coffee', averagePrice: 250 },
  { _id: 'kitchen', averagePrice: 250 },
  { _id: 'gadget', averagePrice: 199 },
  { _id: 'wearable', averagePrice: 199 },
  { _id: 'audio', averagePrice: 80 },
  { _id: 'mechanical', averagePrice: 75 },
  { _id: 'denim', averagePrice: 60 },
  { _id: 'wireless', averagePrice: 52.5 },
  { _id: 'peripheral', averagePrice: 50 },
  { _id: 'fashion', averagePrice: 45 },
  { _id: 'leather', averagePrice: 45 },
  { _id: 'clothing', averagePrice: 40 },
  { _id: 'exercise', averagePrice: 30 },
  { _id: 'fitness', averagePrice: 30 },
  { _id: 'cotton', averagePrice: 20 },
  { _id: 'casual', averagePrice: 20 }
]
ggregationAssignmentDB> db.products.aggregate([
  {
    $match: {
      date_added: {
        $gte: new Date("2023-02-01T00:00:00Z"),
        $lt:  new Date("2023-03-01T00:00:00Z")
      }
    }
  },
  {
    $project: {
      _id: 0,
      name: 1,
      category: 1,
      formattedDateAdded: {
        $dateToString: { format: "%Y-%m-%d", date: "$date_added" }
      }
    }
  },
  { $sort: { formattedDateAdded: 1 } }
]);

[
  {
    name: 'Wireless Mouse',
    category: 'Electronics',
    formattedDateAdded: '2023-02-01'
  },
  {
    name: 'Espresso Machine',
    category: 'Home Goods',
    formattedDateAdded: '2023-02-15'
  },
  {
    name: 'Bluetooth Speaker',
    category: 'Electronics',
    formattedDateAdded: '2023-02-25'
  }
]
ggregationAssignmentDB>
```
#EASY ASSINGMENT 


![Screenshot 2025-05-29 165139](https://github.com/user-attachments/assets/2c71d123-c6a8-40eb-be0c-2aa638bc9b72)

.............................................................................................................................................................................

![Screenshot 2025-05-29 165243](https://github.com/user-attachments/assets/995b34d1-6c7a-4300-ad51-00f5fbda1142)

.............................................................................................................................................................................

![Screenshot 2025-05-29 165328](https://github.com/user-attachments/assets/095751a8-c825-42c6-8054-a5a21693d973)

.............................................................................................................................................................................

#Medium Assigment 

![Screenshot 2025-05-29 165524](https://github.com/user-attachments/assets/e6f8ec18-9846-480d-acfe-73556e70ea9e)

...................................................................................................................

![Screenshot 2025-05-29 165606](https://github.com/user-attachments/assets/1bd626ed-e57c-448e-bd95-77298562a2a8)

....................................................................................................................

![Screenshot 2025-05-29 170002](https://github.com/user-attachments/assets/a7df4934-1c85-4ba9-9a88-eaf38e242951)

