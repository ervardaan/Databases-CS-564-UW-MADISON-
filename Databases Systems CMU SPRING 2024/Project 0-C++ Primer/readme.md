All the programming projects this semester will be written on the BusTub database management system. This system is written in C++. To make sure that you have the necessary C++ background, you must complete a simple programming assignment to assess your knowledge of basic C++ features. You will not be given a grade for this project, but you must complete the project with a perfect score before being allowed to proceed in the course. Any student unable to complete this assignment before the deadline will be asked to drop the course.

All of the code in this programming assignment must be written in C++.

In this project, you will implement an Observed Remove Set (OR-Set), a common Conflict-free replicated data type (CRDT).

# definition and problem stem
- Imagine a group of friends is drafting a travel plan together on Google Docs. Everyone is typing, adding pictures, and striking off items all at once. But here's the cool part: there's no stepping on each other's toes. Every change, from a new destination to a deleted activity, seamlessly integrates into the document. This real-time, harmonious editing is the magic of CRDTs at play, transforming a potentially chaotic collaboration into a smooth, enjoyable experience.

In general, Conflict-Free Replicated Data Types (CRDTs) are data structures designed for distributed systems where multiple nodes operate independently without the need for immediate synchronization. These data structures can be updated independently and concurrently across multiple nodes, and still converge to the same state once all updates are propagated and processed. To this end, we need an abstraction with commutative, associative, and idempotent operations, then we could create a Merge method to "eventually" reconcile to a definitive final state.

The OR-Set is a specific type of CRDT that handles the addition and removal of elements in a set. In an OR-Set, each element added to the set is tagged with a unique identifier. When an element is removed, its identifier is moved to a "tombstone" set, instead of being completely deleted. This allows the system to track both the additions and deletions of elements, so we could re-add elements after deletion.

When a concurrent add and remove operation over the same element occur, one among several post conditions can be chosen: add-wins, remove-wins or an error mark. The OR-Set can also be called add-wins set since it always lets add operations win over remove operations. Therefore, the OR-Set always leads to a predictable state.

Key POINTS:we have to use BusTub database management system designed for cmu

we have to build the OR-Set(which is predictable:it always works in "add-wins" methodology)

CRDTs are used for distributed systems and works in a predictable way-there is no need of immediate sychronization between all of the computers working on one database

- these data structures lie on all of the computers working currently and when all of the updations happen by all of the computers, still then the data structures and the last final result can be converged because all of the computers were using CRDTs
- the Observed Removed Set is a Type of CRDT
- operations and post results on one element of the database: add wins, remove wins, error(for ORS, we have predictable "add wins")
