# Udacity-
# Adventure Game  


import time
import random

# Function to print messages with delay
def print_message(message):
    print(message)
    time.sleep(1)

# Function to start the game
def start_game():
    print_message("Welcome to the Adventure Game!")
    print_message("You find yourself in a mysterious forest.")
    main_game_loop()

# Function to handle the main game loop
def main_game_loop():
    total_score = 0
    while True:
        action = get_player_action()
        outcome, score_change = process_action(action)
        total_score += score_change
        print_message(outcome)
        print_message(f"Your current score is: {total_score}")
        if is_game_over(total_score):
            break
    end_game(total_score)

# Function to get the player's action
def get_player_action():
    print_message("What would you like to do?")
    print("1. Explore the forest")
    print("2. Rest by the campfire")
    print("3. Hunt for food")
    while True:
        choice = input("Enter the number of your choice: ")
        if choice in ['1', '2', '3']:
            return choice
        else:
            print_message("Invalid input, please try again.")

# Function to process the player's action
def process_action(action):
    if action == '1':
        outcomes = ["You find a hidden treasure!", "You encounter a wild animal!"]
        score_changes = [10, -5]
    elif action == '2':
        outcomes = ["You have a peaceful rest.", "A thief steals some of your supplies!"]
        score_changes = [5, -10]
    elif action == '3':
        outcomes = ["You successfully hunt a deer.", "You get lost in the forest."]
        score_changes = [15, -20]
    index = random.randint(0, 1)
    return outcomes[index], score_changes[index]

# Function to check if the game is over
def is_game_over(score):
    return score >= 50 or score <= -50

# Function to end the game
def end_game(score):
    if score >= 50:
        print_message("Congratulations! You've won the game!")
    else:
        print_message("Game Over! Better luck next time.")
    restart_game()

# Function to restart the game
def restart_game():
    while True:
        choice = input("Would you like to play again? (yes/no): ").lower()
        if choice == 'yes':
            start_game()
        elif choice == 'no':
            print_message("Thank you for playing!")
            break
        else:
            print_message("Invalid input, please try again.")

# Start the game
start_game()
