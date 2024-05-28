# Snake-Game
Successfully developed a Snake Game using Python programming.

**BreakDown the structure:
 1. Create a snake body
 2. Move the snake
 3. Control the snake
 4. Detect collision with Food
 5. Create a scoreboard
 6. Detect collision with wall
 7. Detect collision with tail **

Creat A Snake Body :

![WhatsApp Image 2024-05-28 at 12 23 09 PM](https://github.com/Ashvini8879/Snake-Game/assets/170402064/9bb00949-9413-4511-9861-498e9bcb53c2)

![WhatsApp Image 2024-05-28 at 12 35 34 PM](https://github.com/Ashvini8879/Snake-Game/assets/170402064/acdc8404-eced-4eb0-9bff-eca6b1a4d552)
____________________________________________________________________________
main.py file:
____________________________________________________________________________

from turtle import Screen

from snake import Snake

import time

screen = Screen()
screen.setup(width=600, height=600)
screen.bgcolor("black")
screen.title("My Snake Game")
screen.tracer(0) # to turn off the animation

snake = Snake()
food = Food()

screen.listen()
screen.onkey(snake.up, "Up")

screen.onkey(snake.down, "Down")

screen.onkey(snake.left, "Left")

screen.onkey(snake.right, "Right")

game_is_on = True
while game_is_on:
    screen.update() #to update the screen to move the snake
    time.sleep(0.1)  #to move snake faster
    snake.move()
screen.exitonclick()
____________________________________________________________________________
snake.py file:
____________________________________________________________________________

from turtle import Turtle
STARTING_POSITIONS = [(0, 0), (-20, 0), (-40, 0)]
MOVE_DISTANCE = 20
UP = 90
DOWN = 270
LEFT = 180
RIGHT = 0

class Snake:

    def __init__(self):
        self.segments = []
        self.create_snake()
        self.head = self.segments[0]
        
    #Creat A Snake Body using class:
    ________________________________
    
    def create_snake(self):
        for position in STARTING_POSITIONS:
            new_segment = Turtle("square")
            new_segment.color("white")
            new_segment.penup()
            new_segment.goto(position)
            self.segments.append(new_segment)
            
    #Move The Snake :
    _________________
    
    def move(self):
        for seg_num in range(len(self.segments) - 1, 0, -1):
            new_x = self.segments[seg_num - 1].xcor()
            new_y = self.segments[seg_num - 1].ycor()
            self.segments[seg_num].goto(new_x, new_y)
        self.head.forward(MOVE_DISTANCE)

    def up(self):
        if self.head.heading() != DOWN:
            self.head.setheading(UP)

    def down(self):
        if self.head.heading() != UP:
            self.head.setheading(DOWN)

    def left(self):
        if self.head.heading() != RIGHT:
            self.head.setheading(LEFT)

    def right(self):
        if self.head.heading() != LEFT:
            self.head.setheading(RIGHT)

   


![image](https://github.com/Ashvini8879/Snake-Game/assets/170402064/ddf97948-7e3b-427d-a059-1b905bb7cb58)
