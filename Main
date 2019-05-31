// Dan W.
// imported libraries

import java.util.Scanner;   // keyboard & file inputs & outputs
import java.io.File;        // connecting to external files
import java.io.IOException; // handle unexpected input/output runtime errors
import java.io.FileWriter;  // writing data to external file
import java.util.ArrayList;

class Main 
{
  // constants

  static final String NAME = "Sven";    // name of program  
  static final int EXIT_CHOICE = 3;     // menu choice to exit program

  // external data file containing list of items sold in vending machine   
  static final String INVENTORY_LIST_FILENAME = "ItemsForSale.txt";

  public static void main(String[] args)
  {
    // local variables 
    ArrayList<String> custChoices = new ArrayList<String>();
    
    // list of items for sale
    InventoryList itemsForSale = new InventoryList();

    // to obtain human's input  
    Scanner keyboard = new Scanner(System.in);          
  
    String userMenuChoice = "";   // human inputted menu choice
    String newItem = "";          // new item added to inventory
    
    // customer selection from menu list of items
    int customerSelection = 0;    

    boolean updateSuccess = false;  // flag to indicate if new item added or not

    //////////////////////  read list of items for sale 
    //////////////////////  from external data file
    try
    {
      Scanner externalFile = new Scanner(new File(INVENTORY_LIST_FILENAME));
      
      while (externalFile.hasNext())
      {
        String nextItem = externalFile.nextLine();
        itemsForSale.addItem(nextItem);
      }
      externalFile.close();

    }
    catch (IOException ioe) // if error occurs trying to read data to file
    {
      System.err.println(ioe);
    }
    
    ////////////////////// setting up the screen
    clearScreen(); // calling the clearScreen method that clears the console output
    System.out.println("\n");       // blank lines to space output

    System.out.println("Hello, I am the world's first smart vending machine. My name is " + NAME + "!");
    
    System.out.println("\n");       // blank lines to space output
    
    ////////////////////// interact with customer

    // loop until human inputs the choice to exit the menu
    // TODO - find a better way to convert an int (EXIT_CHOICE) to a String
    while (!userMenuChoice.equals(EXIT_CHOICE + ""))
    {
      displayMenu();

      System.out.print("Choice: ");
      // trim leading & trailing spaces
      // TODO - allow user to input lowercase letters
      userMenuChoice = keyboard.nextLine().trim();
      if (userMenuChoice.equals("3") || userMenuChoice.equals("E"))
      {
        System.out.println("");
        break;
      }
      ////////////////////// Admin Mode
      // TODO - create separate programs for customers and admins
      
      else if (userMenuChoice.equals("1") || userMenuChoice.equals("A"))
      {
        System.out.println("IN ADMIN MODE.....");
        //System.out.println("What is the pin number?");
        System.out.print("What is the new item to add to the machine's inventory? ");
        newItem = keyboard.nextLine();    // obtain user's input via keyboard
        
        updateSuccess = false;
        
        if (!itemsForSale.addItem(newItem))
        {
          System.out.println("The update failed. Perhaps the item was already in the list.");    
        }
        else
        {
          
          try
          { 
            // add the new item to the end of the file
            // connect to external file, true specifies append mode
            FileWriter externalFile = new FileWriter(INVENTORY_LIST_FILENAME, true);  
            externalFile.write(newItem + "\n");
            System.out.println(newItem);
            externalFile.flush();                      
            externalFile.close(); 

            updateSuccess = true;   
            System.out.println("Your updated inventory list is: ");
            itemsForSale.displayList();                                 
          }                                                           
          catch (IOException ioe) // if error occurs trying to write data to file
          {
            System.err.println(ioe);
            System.out.println("The update failed due to an error working with an external data file.");
          }

        }

      }
      ////////////////////// Customer Mode
      // TODO - create separate programs for customers and admins
      else if (userMenuChoice.equals("2") || userMenuChoice.equals("C"))
      {
        System.out.println("IN CUSTOMER MODE.....");
        System.out.println("Available items:");

        // display the list of items as a numbered list
        for (int i = 0; i < itemsForSale.numberOfItems(); i++)
        {
          System.out.println((i + 1) + ". " + itemsForSale.selectItem(i));
        }

        System.out.println("What would you like to purchase? ");
        customerSelection = keyboard.nextInt();

        System.out.println("DEBUGGING: the customer input is #" + customerSelection);
        
        if (customerSelection == 1)
        {
        itemsForSale.removeItem("avocados");
        custChoices.add("avocados");

        for (String next: custChoices)
        {
          System.out.print(next + " ");
          System.out.println();
        }
        
        } 
        else if (customerSelection == 2)
        {
          itemsForSale.removeItem("bananas");
          custChoices.add("bananas");
          
          for (String next: custChoices)
          {
          System.out.print(next + " ");
          System.out.println();
          }
        }
        

        // TODO save / write the current most upated list of items (one by one) 
        // back to the external file
        // close the file


        try
        { 
          FileWriter externalFile = new FileWriter(INVENTORY_LIST_FILENAME, false);  
          // false specifies write mode (thanks KP)

          for (int i = 0; i < itemsForSale.numberOfItems(); i++)
          {
            externalFile.write(itemsForSale.selectItem(i) + "\n");
          }

          System.out.println("The updated list is: ");
          itemsForSale.displayList();      

          externalFile.flush();                      
          externalFile.close();                                    
        }                                                           
        catch (IOException ioe) // if error occurs trying to write data to file
        {
          System.err.println(ioe);
        }

        // TODO
        // display available item by reading those values from an external data file
        // allow customer to input a choice
        // trust the user to select the correct item from the machine & 
        // deposit exact amount of MinichPay (not ApplePay or AndroidPay) money 
        // in our Room 311 cash till on the honesty system
      }
    
    } // end of while loop
    
    System.out.println("Goodbye");
  } // end of main method

  /////////////////////// static functions


  // display menu
  public static void displayMenu()
  {  
    System.out.println("1. (A)dmin Mode");
    System.out.println("2. (C)ustomer Mode");
    System.out.println(EXIT_CHOICE + ". (E)xit");
  }
   public static void clearScreen() // clears console output
  {  
    System.out.print("\033[H\033[2J");  
    System.out.flush();  
  }  

} // end of Main class
