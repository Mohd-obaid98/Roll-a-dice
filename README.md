# Roll-a-dice
# This is my first project after learning python. This is like a game to roll a dice and get any random number until 1 player wins the game who first reaches 50 points. 
import random
def roll():
    min_value = 1
    max_value = 6
    roll = random.randint(min_value, max_value)
    return roll

while True:
    player = input("Enter the number of players (1-4): ")
    if player.isdigit():
        player = int(player)
        if 1 <= player <= 4:
            break
        else:
            print("must be between 2-4 players.")


max_score = 50
player_scores = [0 for _ in range(player)]

while max(player_scores) < max_score:

    for player_idx in range(player):
        print("\nPlayer number", player_idx + 1, "your turn has just started")
        print("Your total score is:", player_scores[player_idx], "\n")
        current_score = 0
        
        while True:
            should_roll = input ("Would you like to roll (y)?")
            if should_roll != "y":
                break
                
            value = roll()
            if value == 1:
                print("You have rolled 1, turn done!")
                break
            else:
                current_score += value
                print("You have rolled a:", value)
                
            print("Your score is:", current_score)
            
        player_scores[player_idx] += current_score
        print("Your total scores is:", player_scores[player_idx])

max_score = max(player_scores)
winning_idx = player_scores.index(max_score)
print("The winner is Player number", winning_idx + 1, "with a score of", max_score)
