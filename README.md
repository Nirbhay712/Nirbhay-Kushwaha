import turtle
import random
import time
import threading
import pygame

# ================= MUSIC =================
def play_music():
    pygame.mixer.init()
    pygame.mixer.music.load("nirbhay.py/b.py/happy-birthday-254480.mp3")
    pygame.mixer.music.set_volume(1.0)
    pygame.mixer.music.play()  # loop

threading.Thread(target=play_music, daemon=True).start()

# ================= SCREEN =================
screen = turtle.Screen()
screen.setup(900, 700)
screen.bgcolor("white")
screen.title("Happy Birthday 💖")

# ================= TEXT =================
title = turtle.Turtle()
title.hideturtle()
title.penup()
title.color("gold")
title.goto(-260, 260)
title.write("🎉 HAPPY BIRTHDAY 🎉", font=("Arial", 30, "bold"))

# ================= GIFT BOX =================
def gift_open():
    g = turtle.Turtle()
    g.speed(6)
    g.color("red")
    g.penup()
    g.goto(-80, -220)
    g.pendown()

    # Box
    g.begin_fill()
    for _ in range(4):
        g.forward(160)
        g.left(90)
    g.end_fill()

    # Ribbon
    g.color("yellow")
    g.width(6)
    g.penup()
    g.goto(0, -220)
    g.setheading(90)
    g.pendown()
    g.forward(160)

    # Open lid animation
    g.penup()
    g.goto(-80, -60)
    g.color("orange")
    g.setheading(30)
    g.pendown()
    for _ in range(20):
        g.forward(6)
        time.sleep(0.02)

    g.hideturtle()

gift_open()

# ================= FIREWORKS =================
fw = turtle.Turtle()
fw.hideturtle()
fw.speed(0)

def fireworks():
    fw.penup()
    fw.goto(random.randint(-300, 300), random.randint(-50, 250))
    fw.pendown()
    fw.color(random.choice(["red","yellow","cyan","magenta","orange","white"]))
    for _ in range(36):
        fw.forward(120)
        fw.backward(120)
        fw.right(10)

# ================= HEART FIREWORK =================
def heart_firework():
    fw.penup()
    fw.goto(random.randint(-200, 200), random.randint(50, 250))
    fw.setheading(0)
    fw.pendown()
    fw.color("red")
    fw.begin_fill()

    fw.left(140)
    fw.forward(40)
    for _ in range(200):
        fw.right(1)
        fw.forward(1)
    fw.left(120)
    for _ in range(200):
        fw.right(1)
        fw.forward(1)
    fw.forward(40)

    fw.end_fill()
    fw.setheading(0)

# ================= MAIN LOOP =================
while True:
    fireworks()
    time.sleep(0.2)
    fw.clear()

    heart_firework()
    time.sleep(0.5)
    fw.clear()
