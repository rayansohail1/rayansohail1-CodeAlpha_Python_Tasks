import random

# List of words to choose from
words = ['python', 'javascript', 'ruby', 'java', 'csharp', 'php', 'swift']

# Select a random word from the list
word = random.choice(words)

# Create a list of underscores for the word
guesses = ['_'] * len(word)

# Set the maximum number of incorrect guesses allowed
max_incorrect_guesses = 6

# Keep track of the number of incorrect guesses
incorrect_guesses = 0

# Keep track of the letters already guessed
letters_guessed = []

while True:
    # Print the current state of the game
    print(' '.join(guesses))
    print(f'Incorrect guesses: {incorrect_guesses}/{max_incorrect_guesses}')
    print(f'Letters guessed: {", ".join(letters_guessed)}')

    # Check if the player has won
    if ''.join(guesses) == word:
        print(f'Congratulations! You guessed the word "{word}"!')
        break

    # Check if the player has lost
    if incorrect_guesses >= max_incorrect_guesses:
        print(f'Sorry, you ran out of guesses. The word was "{word}".')
        break

    # Get the player's guess
    guess = input('Guess a letter: ').lower()

    # Check if the guess is valid
    if len(guess) != 1 or not guess.isalpha():
        print('Please enter a single letter.')
        continue

    # Check if the letter has already been guessed
    if guess in letters_guessed:
        print('You already guessed that letter. Try again.')
        continue

    # Add the letter to the list of guessed letters
    letters_guessed.append(guess)

    # Check if the letter is in the word
    if guess in word:
        # Update the guesses list with the correct letter(s)
        for i in range(len(word)):
            if word[i] == guess:
                guesses[i] = guess
    else:
        # Increment the number of incorrect guesses
        incorrect_guesses += 1
