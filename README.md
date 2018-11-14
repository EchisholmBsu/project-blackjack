# project-blackjack
This repository contains files for Project 2.

OVERVIEW
--
In this problem, you will complete an implementation of the popular card game, Blackjack. The version of the game that you will complete allows a single player to compete against the dealer. To simplify the logic, we will not allow betting.

RULES OF THE GAME
--
In Blackjack, the goal is to assemble the hand with the highest value, without going over a value of 21. Cards numbered 2-10 are worth their stated value. Face cards (Jacks, Queens, and Kings) have a value of 10. Aces have a value of 11, unless doing so would make the hand's value exceed 21, in which case they have a value of 1. The best outcome is a combination of an ace with either a 10 or a face card; this is known as blackjack (regardless of whether the face card is black or a jack!).

The dealer starts by dealing two cards to the player and two cards to the herself. One of the dealer's cards is shown to the player; the other is dealt face down.

The player then begins his turn. He repeatedly decides whethers to request another card (which is known as a hit) or to hold his current hand. The player's turn continues until he holds or until the value of his hand is 21 or more.

Once the player's turn is completed, the dealer begins her turn. She first reveals her hidden card. Then she gives herself hits as needed in an attempt to win the game. If the player's hand has a value of less than 21, the dealer attempts to exceed the value of the player's hand. If the player's hand has a value of 21, the dealer attempts to match it, unless the player has Blackjack (21 from the first two cards). And regardless of the value of the player's hand, the dealer must take hits until her own hand has a value of at least 17.

STRUCTURE OF THE PROGRAM
--
The code for this program will be divided into a number of different classes. We are giving you complete implementations of the following classes:

Card.java
--
This class is a blueprint for the objects that represent the individual cards. Each Card object has a type and a suit, as well as a default value that can be obtained by using the getDefaultValue() instance method. The default values are as follows:

card type   default value
Ace             1
2-10            same as number on card
Jack            11
Queen         12
King            13
Note that the default values don't always match the values specified for Blackjack, because the Card class is designed to be used in different types of card games. You will adjust the values as needed in the context of the Blackjack-specific objects that you will write for this assignment.

A String representation of a card is provided by the toString() method, which is called implicitly when you try to print a Card. For example, if you attempt to print the Card object representing the King of Spades, you will get the string "KS". In addition, each Card has methods called isAce() and isFaceCard() that return either true or false.

Deck.java
--
This class is a blueprint for objects that represent a deck of 52 cards. These objects have several methods, the most useful of which are the shuffle and dealCard methods.
Hand.java: This class serves as a blueprint for objects that represent a hand of cards -- i.e., the collection of cards belonging to an individual person. It contains the state and behavior common to any hand of cards, regardless of the game being played. Key methods include the addCard method for adding a card to the hand, and the getValue method for getting the total value of the hand. You will extend this class to create subclasses for the the player's hand and the dealer's hand in Blackjack.

Player.java
--
This is an abstract class that serves as a superclass for classes that represent different types of players -- in particular, the ways in which players decide whether to take another hit. This class has an abtract method called wantsHit that takes two parameters: the player's own hand and the opponent's hand. Implementations of this abstract method should return true in cases in which the player should take another hit and false otherwise. We have given you one simplistic subclass of this abstract superclass (see below). You will create two others.
RecklessPlayer.java: This class extends Player. It implements a simplistic version of wantsHit that always returns true, which means that this type of player always asks for another hit!
You should not modify the code in any of the above classes.

In addition, I am providing a working incomplete implementation of Blackjack.java.
--
The Blackjack class contains the main method of the program; you will run this class to start the program. The class also includes several static methods, some of which you will need to modify or complete. Note that this class is cliet code, not a blueprint. It has no instance fields, and all of its methods are static.

Run the program by running Blackjack.java.
--
The version of the program provided runs, but it is incomplete in a number of ways. You will complete the implementation of the program so that it behaves as described in the section Rules of the Game above.
--

Task 1
--
Review the provided code.  Begin by reading over the code that we have given you. Explain the code to another person or out loud to yourself!  Quiz yourself on the methods that are available in the each class.

Task 2
--
Create a class for a hand in Blackjack.

As mentioned above, the Hand class is a blueprint for a generic hand of cards. You will need to define a subclass of Hand that can be used in the context of Blackjack. **Give the subclass the name BlackjackHand**, and make sure that your class header indicates the class that is being extended.

Your BlackjackHand class will inherit the fields and methods of the Hand class. You will need to decide whether your class needs any additional fields or methods (it's possible that it won't), and which of the inherited methods should be overriden. **One method that must be overriden is the getValue method.** The inherited method uses the default values of the cards (see the description of the Card class above). You will need to write a new version of the method that uses the Blackjack-specific values to the cards. One tricky aspect of this method is handling any Aces that may be present in the hand, since these cards may have a value of 11 or 1, and the value of a given Ace depends on the values of the rest of the cards in the hand. Hint: if there is more than one Ace in the hand, at most one of them can have a value of 11.

Don't forget that any new methods that you define will not have direct access to the fields in the superclass. For example, methods in the subclass cannot directly access the cards array from the superclass. Instead, they will need to make use of the getCard method to access the cards in that array.

In addition to overriding one or more methods, you will also need to **define a constructor for your subclass**. This constructor does not need any parameters of its own, and it should invoke the superclass constructor so that the superclass constructor can initialize the fields defined in the superclass. Use a value of 20 for the parameter of the superclass constructor, which will create a hand that can hold up to 20 cards.

Once you have defined your BlackjackHand class, **modify the two lines at the beginning of the playHand method in Blackjack.java** so that they create objects using your new subclass instead of the Hand class. Compile and run the program, and check to make sure that the values given for the hands are now correct. Make any corrections that are needed to produce the correct values.

Task 3
--
Create a class for the dealer's hand. 

The BlackjackHand class isn't exactly right for the dealer's hand, because we want to be able to hide the dealer's first card when the hand is printed -- displaying the String "XX" instead of the card's usual string. This first card should be hidden until the player's turn is done, at which point it should be revealed.

**Create a new class for the dealer's hand, giving it the name BlackjackDealerHand**. It should be a subclass of one of the existing classes -- you'll need to figure out which one makes the most sense to extend. Your new class will inherit the fields and methods of the class that it extends. In addition, it will need a **field that keeps track of whether or not the first card is currently being hidden**, and a **method that allows you to change the value of that field**. Use appropriate names for both the field and the method. In addition, you should **override the toString method** so that the dealer's hand will be printed correctly both during and after the player's turn. Note that the total value of the dealer's hand should not be printed until after the first card is revealed.

Once you have defined your BlackjackDealerHand class, **modify the second line of the playHand method so that it uses the new subclass for the dealer's hand**. In addition, you will need to **add whatever lines are needed to "reveal" the dealer's first card after the player's turn is over.** Compile and run the program to test the changes that you made for this task, and make any additional changes as needed.

Task 4
--
Create subclasses of Player.

The version of Blackjack.java that we gave you uses RecklessPlayer objects for the two players. This subclass of the abstract Player superclass has a very simplistic version of the wantsHit method that always returns true -- which is why it produces reckless behavior by both the player and the dealer.

**Create two new subclasses of Player: one for the user of the program (call it ConsolePlayer), and one for the dealer (call it BlackjackDealer), and give them appropriate implementations of the wantsHit method**.

**The ConsolePlayer class should have a field for a Scanner object that it will use to read from the console.** **The Scanner should be passed in as a parameter to the ConsolePlayer constructor, and the constructor should assign it to the field in the ConsolePlayer object.** (Don't forget to include an import statement for the java.util package at the top of the file for this class.) **The wantsHit method for this class method should ask the user if he/she wants another hit and use the Scanner to read the user's reply.** A reply of "y" should cause the method to return true, and any other reply should cause the method to return false.

**The BlackjackDealer class does not need and should not have a constructor or any additional fields. Its implementation of the wantsHit method should use the two hands passed in as parameters to determine if the dealer should give herself another hit, and return true or false accordingly.** See the section entitled "Rules of the game" to see when the dealer should take another hit and when she should hold.

Once you have these subclasses implemented, **change the lines in the main method of Blackjack.java that create the two player objects, and change them so that they create instances of your new subclasses, rather than RecklessPlayer objects**. Here again, you should compile and run the program and make whatever additional changes are needed to make them work correctly.

Task 5
--
Implement the printResult method.

In Blackjack.java, implement the printResult method so that it prints an appropriate message summarizing the results of a given hand.

Here are some special points to keep in mind when writing this method:

* If the user goes over 21, he loses the game, regardless of what happens to the dealer.

* If the user and dealer both end up with the same value less than or equal to 21, the message "Push!" should be displayed to indicate a tie.

* If the user gets 21 from his first two cards, a special "Blackjack!" message should be displayed unless the dealer also has 21 from her first two cards.

See the sample output for what the messages should look like.

Once all of these tasks are completed, you will have a working Blackjack game!
--

Implementation guidelines
--
* Do not change the headers of any of the methods provided. You may think that it is necessary to do so in light of the new subclasses that you are writing, but polymorphism allows you to keep the existing types of the parameters of the methods. For example, the playHand method takes two parameters of type Player. Those parameters can be used for objects of any subclass of Player, thanks to the power of polymorphism.

* Limit yourself to the concepts we have covered in class.  Do not use any programming constructs that are not in the assigned reading. 

* Employ good programming style. Use appropriate indentation, select descriptive variable names, insert blank lines between logical parts of your program, and add comments as necessary to explain what your code does. In particular, you should add comments to the start of each subclass file and before each new method that you write. 

Suggested approach
--
Begin by reviewing class notes on inheritance, the corresponding sections of the textbook, and our example programs for inheritance.

Implement, debug, and test one piece of code at a time. Compile frequently; don't wait until after all of your methods have been written to compile. If you are unable to get a given method to compile, make sure to comment out the body of the method (keeping the method header and possibly a dummy return value) so that I'll still be able to test your other methods.

Submitting your work
--
Upload multiple files to Blackboard:

* your modified Blackjack.java file
* the files for the subclasses that you wrote for Tasks 2, 3, and 4

Do not submit the files that did not change.

Check your submission for any possible problems, and alert me promptly if you encounter any.

