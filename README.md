# problem_solve-1.-X_O-game-
#This project was having some bugs. I downloaded it from GitHub, and the developer wrote that it was missing a lot, so I took it and #fixed it until it was ready to use.


board = ["0", "1", "2", "3", "4", "5", "6", "7", "8"]
playing_now = "X"

def draw():
    print()
    print(board[0], "|", board[1], "|", board[2])
    print("--+---+--")
    print(board[3], "|", board[4], "|", board[5])
    print("--+---+--")
    print(board[6], "|", board[7], "|", board[8])
    print()

def switch():
    global playing_now
    if playing_now == "X":
        playing_now = "O"
    else:
        playing_now = "X"

def quit():
    quit()

def check_win():
    if board[0] == board[1] == board[2] or board[3] == board[4] == board[5] or board[6] == board[7] == board[8]:
        return True
    elif board[0] == board[3] == board[6] or board[1] == board[4] == board[7] or board[2] == board[5] == board[8]:
        return True
    elif board[0] == board[4] == board[8] or board[2] == board[4] == board[6]:
        return True
    else:
        return False
    
    
    

def play():
    while True:
        draw()
        move = input("Player " + playing_now + ", choose a position (1-9): ")
        if not move.isdigit():
            print("❌ The number is not correct")
            continue

        move = int(move)
        if move < 1 or move > 9:
            print("❌ The number must be from 1 to 9.")
            continue

        if board[move] == "X" or board[move] == "O": 
            print("❌ The place is busy, try number")
            continue

        board[move] = playing_now  
        if check_win():  
            draw()
            print("✅ play", playing_now, "Win!")
            break

        switch()

play()
