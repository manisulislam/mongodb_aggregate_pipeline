## This is the mongodb aggregate pipeline

# Qestion 1: How many users is active?
# 1. match and count operator


```
[
  {
    $match: {
      isActive: true
    }
  },
  {
    $count: 'activeUsers'
  }
]
```
# 2. What is the average of all users?

```
[
  {
    $group: {
      _id: null,
      avgAge:{
        $avg: "$age"
      }
    }
  }
]
```


# 3. List the top 5 most common favourite fruits among the users?
```
[
  {
    $group: {
      _id: "$favoriteFruit",
      count:{
        $sum: 1
      }
    }
  },
  {
    $sort: {
      count: -1
    }
  },
  {
    $limit: 5
  }
]
```
# 4. Find the total number of males and females.
```
[
  {
    $group: {
      _id: "$gender",
      genderCount:{
      	$sum: 1
      }
    }
  }
]
```
# 5. Which country has the highest number of registered users?
```
[
  {
    $group: {
      _id: "$company.location.country",
      count:{
        $sum: 1
      }
    }
  },
  {
    $sort: {
      count: -1
    }
  },
  {
    $limit: 1
  }
]
```
# 6. List all unique eye colors present in the collection.

```
[
  {
    $group: {
      _id: "$eyeColor"
    }
  }
]
```
# 7. What is the average number of tags per user?
```
[
  {
    $addFields: {
      numberOfTags: {
        $size: {
          $ifNull: ["$tags",[]]
        }
      }
    }
  },
  {
    $group: {
      _id: null,
      avgNumberOfTags:{
        $avg:"$numberOfTags"
      }
    }
  }
]
```
# 8. How many have 'enim' as one of their tags?

```
[
  {
    $match: {
      tags: "enim"
    }
  },
  {
    $count: 'enimTags'
  }
]
```
# 9. What are the names and age of users who are inactive and have 'velit' as a tags?

```
[
  {
    $match: {
      isActive: false,
      tags: "velit",
    },
  },
  {
    $project: {
      name: 1,
      age: 1,
    },
  },
]
```
# 10. How many users have a phone number starting with '+1(940)'?
```
[
  {
    $match: {
      "company.phone": /^\+1\(940\)/,
    },
  },
  {
    $count: "users",
  },
]
```
# 11. Who has registered the most recently?

```
[
  {
    $sort: {
      registered: -1
    }
  }
]
```
# 12. Categories user by their favourite fruits and how many?

```
[
  {
    $group: {
      _id: "$favoriteFruit",
      users:{
        $push: "$name"
      }
    }
  }
]
```
# 13. How many users have 'ad' as the second tag in their list of tags?
```
[
  {
    $match: {
      "tags.1": "ad"
    }
  },
  {
    $count: 'users'
  }
]
```
# 14. Find users who have both 'enim' and 'id' as their tags.
```
[
  {
    $match: {
      "tags": "enim",
      "tags": "id"
    }
  }
]
```
# 15. List all companies located in the USA with their corresponding user count
```
[
  {
    $match: {
      "company.location.country": "USA",
    },
  },
  {
    $group: {
      _id: "$company.title",
      userCount: {
        $sum: 1,
      },
    },
  },
]
```