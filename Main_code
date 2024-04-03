import pygame
import sys
from pygame.locals import *

pygame.init()
pygame.mixer.init()

# Set up the window
WINDOW_WIDTH = 800
WINDOW_HEIGHT = 600
window_surface = pygame.display.set_mode((WINDOW_WIDTH, WINDOW_HEIGHT), 0, 32)
pygame.display.set_caption('Bouncing Ball')
background = pygame.image.load(r"sky_background.png")
# Set up colors
WHITE = (255,255,255)
red = (255,0,0)
yellow = (139, 128, 0)
orange =  (255, 165, 0) 
# Set up the ball
BALL_RADIUS = 20
ball_color = orange
ball_x = WINDOW_WIDTH // 2
ball_y = WINDOW_HEIGHT // 2
ball_speed_x = 5
ball_speed_y = 5
rect_color = red
effects = pygame.mixer.Sound(r"C:\Users\Rahul\Desktop\blip-131856.mp3")
score = 0

# Set up rectangles
rect_1 = pygame.Rect(0, 0, 30, 30)
rect_2 = pygame.Rect(770, 0, 30, 30)
rect_3 = pygame.Rect(0, 570, 30, 30)
rect_4 = pygame.Rect(770, 570, 30, 30)
rectangles = [rect_1, rect_2, rect_3, rect_4]

# Main game loop
running = True
while running:
    # Event handling
    for event in pygame.event.get():
        if event.type == QUIT:
            running = False
        elif event.type == KEYDOWN:
            if event.key == K_UP:
                ball_speed_y = -5
            elif event.key == K_DOWN:
                ball_speed_y = 5
            elif event.key == K_LEFT:
                ball_speed_x = -5
            elif event.key == K_RIGHT:
                ball_speed_x = 5

    # Move the ball
    ball_x += ball_speed_x
    ball_y += ball_speed_y

    # Bounce the ball off the walls
    if ball_x < 0 or ball_x > WINDOW_WIDTH - 2 * BALL_RADIUS:
        ball_speed_x = -ball_speed_x
    if ball_y < 0 or ball_y > WINDOW_HEIGHT - 2 * BALL_RADIUS:
        ball_speed_y = -ball_speed_y

    # Check collision with rectangles
    for rect in rectangles:
        if rect.colliderect((ball_x - BALL_RADIUS, ball_y - BALL_RADIUS, 2 * BALL_RADIUS, 2 * BALL_RADIUS)):
            # Reverse the ball's direction
            ball_speed_x = -ball_speed_x
            ball_speed_y = -ball_speed_y

            # Increment the score
            score += 1
            effects.play()

            
    # Draw rectangles
    for rect in rectangles:
        pygame.draw.rect(window_surface, rect_color, rect)

    # Draw the ball
    pygame.draw.circle(window_surface, (0, 0, 0), (ball_x, ball_y), BALL_RADIUS + 2)
    pygame.draw.circle(window_surface, ball_color, (ball_x, ball_y), BALL_RADIUS)
    # Draw the score
    font = pygame.font.Font(r"C:\Users\Rahul\Desktop\Metropolis-Medium.ttf", 36)
    text = f"Score: {score}"
    text_surface = font.render(text, True, WHITE)
    window_surface.blit(text_surface, (323, 10))

    # Update the display
    pygame.display.update()
    window_surface.blit(background, (0, 0))
    # Control the frame rate
    pygame.time.Clock().tick(30)

pygame.quit()
sys.exit()
