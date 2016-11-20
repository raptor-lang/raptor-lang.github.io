---
title: "Collections"
---

### Vectors
RaptorScript has Vectors as the most basic form of collection. Due to how memory is implemented in [RaptorTime](/raptortime), the primitive collection in RaptorScript is variable size and mutable. The syntax for vector construction is as follows:

    var data: Int[] = [0, 3, 1, 5, 2, 3]
    
You can access elements in a vector like this. Indexes start from 0:

    data[2] # => 1
    
As mentioned, vectors are mutable, meaning you can replace the elements at specific indexes:

    data[2] = 8
    
Of course all elements in a vector have the same type.
