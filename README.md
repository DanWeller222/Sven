# Sven
Sven (Smart vending machine)
https://repl.it/@DanielWeller/Java-Sven-version-1-3

I upgraded Sven so that in Customer Mode when a choice is selected out of the two items that are for sale on Thursday May 30th the item will be correctly removed from the list, as it caused an error before I completed this.
Also I initialized an arraylist called custChoices that is will contain the customer's choices in customer mode and is being updated to print the arraylist for the customer to see.
I did this on lines 143-165 using an if else statement that removes the item that is selected by the customer and adds it to another arrayList called custChoices (initialized on line 23) .
