# quiz-1

import tkinter as tk
from tkinter import messagebox

window = tk.Tk()
window.title("Tic Tac Toe")

player = "X"
buttons = 

def click(i):
    global player

    if buttons[i]["text"] == "":
        buttons[i]["text"] = player

        # Check winner
        wins = [
            [0,1,2],[3,4,5],[6,7,8],
            [0,3,6],[1,4,7],[2,5,8],
            [0,4,8],[2,4,6]
        ]

        for w in wins:
            if buttons[w[0]]["text"] == buttons[w[1]]["text"] == buttons[w[2]]["text"] != "":
                messagebox.showinfo("Winner", player + " wins!")
                reset()
                return

        # Check draw
        if all(b["text"] != "" for b in buttons):
            messagebox.showinfo("Draw", "It's a draw!")
            reset()
            return

        # Switch player
        player = "O" if player == "X" else "X"

def reset():
    global player
    player = "X"
    for b in buttons:
        b"text" = ""

for i in range(9):
    btn = tk.Button(window, text="", font=("Arial", 40),
                    width=5, height=2,
                    command=lambda i=i: click(i))
    btn.grid(row=i//3, column=i%3)
    buttons.append(btn)

window.mainloop()
