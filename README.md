# Sven
Sven (Smart vending machine)
https://repl.it/@DanielWeller/Java-Sven-version-1-3
Hello this is Daniel Weller and I made some addition to the Sven vending machine in my AP Java class, these additions are mentioned below.

I upgraded Sven so that in Customer Mode when a choice is selected out of the two items that are for sale on Thursday May 30th the item will be correctly removed from the list, as it caused an error before I completed this.
Also I initialized an arraylist called ```custChoices``` that is will contain the customer's choices (strings) in customer mode and is being updated to print the arraylist for the customer to see with spaces in between for good style.
I did this on lines 143-165 using an if else statement that removes the item that is selected by the customer from the availble products to buy, and adds it to another arrayList called ```custChoices``` (initialized on line 23).  ```custChoices``` is like a grocery cart to a person shopping at the store as it hold the items they would like to purchase.
