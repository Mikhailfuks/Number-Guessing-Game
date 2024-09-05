using System;

public class NumberGuessingGame
{
    public static void Main(string[] args)
    {
        Console.WriteLine("Welcome to the Number Guessing Game!");
        Console.WriteLine("I'm thinking of a number between 1 and 100.");

        Random random = new Random();
        int targetNumber = random.Next(1, 101); // Generate a random number between 1 and 100
        int guessCount = 0;
        int maxGuesses = 7; // Allow a maximum of 7 guesses

        while (guessCount < maxGuesses)
        {
            Console.Write($"Guess a number: ");
            if (int.TryParse(Console.ReadLine(), out int guess))
            {
                guessCount++;

                if (guess < targetNumber)
                {
                    Console.WriteLine("Too low! Guess higher.");
                }
                else if (guess > targetNumber)
                {
                    Console.WriteLine("Too high! Guess lower.");
                }
                else
                {
                    Console.WriteLine($"Congratulations! You guessed it in {guessCount} tries.");
                    break; // End the loop if the guess is correct
                }
            }
            else
            {
                Console.WriteLine("Invalid input. Please enter a number.");
            }
        }

        if (guessCount == maxGuesses)
        {
            Console.WriteLine($"You ran out of guesses. The number was {targetNumber}.");
        }

        Console.WriteLine("Thanks for playing!");
        Console.ReadKey();
    }
}
