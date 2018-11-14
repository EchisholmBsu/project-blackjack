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

In addition, we are providing a working but incomplete implementation of the following class Blackjack.java.
--
The Blackjack class contains the main method of the program; you will run this class to start the program. The class also includes several static methods, some of which you will need to modify or complete. Note that this class is cliet code, not a blueprint. It has no instance fields, and all of its methods are static.\

Run the program by running Blackjack.java.
--

