# Hangman Game in Python

import random

# List of words to guess
words = ['apple', 'banana', 'cherry', 'date', 'elderberry']

# Choose a random word from the list
word = random.choice(words)

# Create a list to store the guessed letters
guessed = ['_'] * len(word)

# Create a set to store the incorrect guesses
incorrect_guesses = set()

# The number of lives the player has
lives = 6

print("Welcome to Hangman!")
print("You have", lives, "lives.")

while lives > 0:
    # Print the current state of the word
    print(' '.join(guessed))

    # Ask the user for a guess
    guess = input("Guess a letter: ")

    # Check if the guess is in the word
    if guess in word:
        # Reveal the correctly guessed letters
        for i in range(len(word)):
            if word[i] == guess:
                guessed[i] = guess
    else:
        # Increment the number of incorrect guesses
        incorrect_guesses.add(guess)
        lives -= 1
        print("Incorrect! You have", lives, "lives left.")

    # Check if the word has been fully guessed
    if '_' not in guessed:
        print(' '.join(guessed))
        print("Congratulations! You won!")
        break

if lives == 0:
    print("Game over! The word was", word)
