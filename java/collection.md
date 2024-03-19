#Java Collection

1. HashMap complexity
--
    - Add / delete  Item 
        - Average Case Complexity: O(1)
        - Worst Case Complexity: O(n)
  
    In JDK 8, HashMap has been tweaked so that if keys can be compared for ordering, then any densely-populated bucket is implemented as a tree, 
    so that even if there are lots of entries with the same hash code, the complexity is O(log n).


2. 
