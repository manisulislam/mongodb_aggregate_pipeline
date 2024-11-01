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

# 3. List the top 5 most common favourite fruits among the users?

# 4. Find the total number of males and females.

# 5. Which country has the highest number of registered users?

# 6. List all unique eye colors present in the collection.

# 7. What is the average number of tags per user?

# 8. How many hava 'enim' as one of their tags?

# 9. What are the names and age of users who are inactive and have 'velit' as a tags?

# 10. How many users have a phone number starting with '+1(940)'?

# 11. Who has registered the most recently?

# 12. Categories user by their favourite fruits and how many?

# 13. How many users have 'ad' as the second tag in their list of tags?

# 14. Find users who have both 'enim' and 'id' as their tags.

# 15. List all companies located in the USA with their corresponding user count