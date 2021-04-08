# PYTHON---BOUNCING-BALL-PING-PONG-
#BOUNCING BALL
import pygame
import sys

pygame.init()
SCREEN_WIDTH=800
SCREEN_HEIGHT=600
BLACK=(0,0,0)
GREEN=(0,225,0)
fps=600
ballradius = 20
ballx= ballradius
bally = ballradius
speed =[1,1]


def animate_ball():
    global ballx,bally
    ballx += speed[0]
    bally += speed[1]
    check_boundary()

def check_boundary():
    if ballx + ballradius > SCREEN_WIDTH or ballx - ballradius <0:
        speed[0] *= -1
    if bally + ballradius > SCREEN_HEIGHT or bally - ballradius <0:
        speed[1] *= -1

def gameloop():
    screen = pygame.display.set_mode([SCREEN_WIDTH,SCREEN_HEIGHT])
    pygame.display.set_caption("BOUNCING BALL")
    clock = pygame.time.Clock()
    while True:

        for event in pygame.event.get():
            if event.type==pygame.QUIT:

               sys.exit()


        screen.fill(BLACK)
        pygame.draw.circle(screen,GREEN,(ballx,bally),ballradius)
        animate_ball()
        pygame.display.update()
        clock.tick(fps)

gameloop() 
