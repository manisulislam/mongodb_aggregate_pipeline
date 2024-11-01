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