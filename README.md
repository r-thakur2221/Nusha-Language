# Nusha-Language
A language for solving puzzles...


#Nusha Language Definition

Nusha is different from programming languages you may have used before. It is a logic language. You don’t tell the computer what to do. You give it a problem, and the computer solves it.

Nusha was designed to solve logic puzzles. There are a few types of entities in our definition of a logic problem:

Enums – Short for enumerations, these are collections of names under a category. They are used as options for a particular variable. For example:
Flavor = { Vanilla, Chocolate, Strawberry, Coffee}

Structures – Structures are a set of Enums that are grouped together in the logic puzzle. In a traditional logic puzzle grid, the items in a row are Structures in Nusha. A Structure may hold any number of items. An item in a structure is made up of an Enum type, a name and optionally the word “unique”, indicating that in an array of Structures (see below), every instance of the item must be unique. Without unique, repetition across the array is allowed.
Example:
Friend = [ unique Teen teen, unique Teen bestFriend, Subject favoriteClass]
A Structure is a definition – to use a Structure, you must create it as part of an Array.

Arrays – an array is a collection of Structures. They are numbered, starting at 0. Note the key word “var” – that indicates that we are allocating a variable.
Example:
var OurFriends : Friend[4]

Rules – A rule is a statement that must be true in order for the solution to the logic puzzle to be true. Your Nusha file may have any number of rules. The rules eliminate invalid solutions. Missing rules will result in too many solutions. Extra rules may result in no solutions. There are two different types of rules – Simple and Complex.

Simple Rule – these rules define an exact element in a Structure and the value that element must have. These are often used to “pin” a choice to a row of the array; without doing this, you could have trivial permutations that make the solutions redundant. For example, consider if you have 2 names, Tanya and Fred. One solution could be:
OurFriends[0].teen = Tanya
OurFriends[1].teen = Fred

But without “pinning”, Nusha would also produce:
OurFriends[0].teen = Fred
OurFriends[1].teen = Tanya

Example:
OurFriends[0].teen = Tanya

Complex Rule – these rules don’t specify a particular row in the array. They operate as an “if-then” rule. If condition is true, then some set of conditions must also be true. When the row of the array is omitted, the row that makes the “if” part of the rule true is applied to all of the rest of the rows.
Example:
OurFriends.favoriteClass = ComputerScience =>
OurFriends.bestFriend = Tanya
OurFriends.teen != Fred

This rule says that if a row of OurFriends has a favoriteClass of ComputerScience, then that row’s bestFriend must be Tanya and the teen must not be Fred.

Naming in Nusha
Names must all be single words (without spaces). Capitalization must be consistent (flavor is different from Flavor) but all lower case, all upper case or mixed case can be used.
