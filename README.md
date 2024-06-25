import tkinter as tk
import random

class RockPaperScissors:
    def __init__(self):
        self.root = tk.Tk()
        self.root.title("Rock Paper Scissors Game")
        self.root.geometry("500x500")

        self.player_score = tk.IntVar()
        self.computer_score = tk.IntVar()

        self.player_choice = tk.StringVar()
        self.computer_choice = tk.StringVar()
        self.result = tk.StringVar()

        self.player_score.set(0)
        self.computer_score.set(0)

        self.create_widgets()

    def create_widgets(self):
        tk.Label(self.root, text="Rock Paper Scissors", font="normal 20 bold", fg="blue").pack(pady=20)

        frame = tk.Frame(self.root)
        frame.pack()

        tk.Label(frame, text="Player", font=10).pack(side=tk.LEFT)
        tk.Label(frame, text="VS", font="normal 10 bold").pack(side=tk.LEFT)
        tk.Label(frame, text="Computer", font=10).pack(side=tk.LEFT)

        frame1 = tk.Frame(self.root)
        frame1.pack()

        tk.Button(frame1, text="Rock", font=10, width=7, command=lambda: self.play("rock")).pack(side=tk.LEFT, padx=10)
        tk.Button(frame1, text="Paper", font=10, width=7, command=lambda: self.play("paper")).pack(side=tk.LEFT, padx=10)
        tk.Button(frame1, text="Scissors", font=10, width=7, command=lambda: self.play("scissors")).pack(side=tk.LEFT, padx=10)

        frame3 = tk.Frame(self.root)
        frame3.pack(pady=20)

        tk.Label(frame3, text="Player Score:", font="normal 10 bold", bg="white", width=15, borderwidth=2, relief="solid").pack(side=tk.LEFT, padx=10)
        tk.Label(frame3, textvariable=self.player_score, font="normal 10 bold", bg="white", width=5, borderwidth=2, relief="solid").pack(side=tk.LEFT, padx=10)

        tk.Label(frame3, text="Computer Score:", font="normal 10 bold", bg="white", width=15, borderwidth=2, relief="solid").pack(side=tk.LEFT, padx=10)
        tk.Label(frame3, textvariable=self.computer_score, font="normal 10 bold", bg="white", width=5, borderwidth=2, relief="solid").pack(side=tk.LEFT, padx=10)

        tk.Label(self.root, textvariable=self.result, font="normal 20 bold", bg="white", width=30, borderwidth=2, relief="solid").pack(pady=20)

        frame4 = tk.Frame(self.root)
        frame4.pack(pady=20)

        tk.Button(frame4, text="Reset Game", font=10, fg="red", bg="blue", command=self.reset_game).pack(side=tk.LEFT, padx=10)
        tk.Button(frame4, text="Exit", font=10, fg="red", bg="blue", command=self.root.destroy).pack(side=tk.LEFT, padx=10)

    def play(self, player_choice):
        self.player_choice.set(player_choice)
        computer_choice = random.choice(["rock", "paper", "scissors"])
        self.computer_choice.set(computer_choice)

        if player_choice == computer_choice:
            self.result.set("Match Draw")
        elif (player_choice == "rock" and computer_choice == "scissors") or \
             (player_choice == "scissors" and computer_choice == "paper") or \
             (player_choice == "paper" and computer_choice == "rock"):
            self.result.set("Player Win")
            self.player_score.set(self.player_score.get() + 1)
        else:
            self.result.set("Computer Win")
            self.computer_score.set(self.computer_score.get() + 1)

    def reset_game(self):
        self.player_choice.set("")
        self.computer_choice.set("")
        self.result.set("")
        self.player_score.set(0)
        self.computer_score.set(0)

    def run(self):
        self.root.mainloop()

if __name__ == "__main__":
    game = RockPaperScissors()
    game.run()
# RockPaperScissorsGame
