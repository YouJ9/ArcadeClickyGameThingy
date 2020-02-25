# ArcadeClickyGameThingy

import arcade
import math
from random import seed
from random import randint

WIDTH = 800
HEIGHT = 600

window = arcade.Window(WIDTH, HEIGHT, "My Arcade Game")
arcade.set_background_color(arcade.color.AMAZON)

circle_x = WIDTH//2
circle_y = HEIGHT//2
circle_radius = 30
txt_x_1 = WIDTH - 450
txt_y_1 = HEIGHT - 100
txt_size = 25
score = 0

@window.event("on_draw")
def game_loop():

    global circle_x
    global circle_y
    global circle_radius

    arcade.start_render()
    arcade.draw_circle_filled(circle_x, circle_y, circle_radius, arcade.color.CREAM)
    arcade.draw_text("Click the circle to gain points", 20, 550, arcade.color.BLACK, 25)
    arcade.draw_text(f"Score: {score}", 630, 550, arcade.color.BLACK, 25)

@window.event
def on_mouse_press(mouse_x, mouse_y, button, modifiers):
    global circle_radius
    global circle_x
    global circle_y
    global circle_radius
    global score
    sideA = max(mouse_x - circle_x, circle_x - mouse_x)
    sideB = max(mouse_y - circle_y, circle_y - mouse_y)
    sideC = (sideA**2 + sideB**2)**0.5
    if (sideC <= circle_radius):
        for _ in range(1):
            circle_x = randint(50, 750)
            circle_y = randint(50, 550)
            circle_radius = randint(30, 50)
    if (sideC <= circle_radius):
        for _ in range(1):
            score += 1
    else:
        score -= 1
    print(f"Your mouse is at x = {mouse_x}, y = {mouse_y}.")

    arcade.draw_text(f"Score: {score}", 730, 550, arcade.color.BLACK, 25)

arcade.run()
