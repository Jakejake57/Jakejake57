import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up screen dimensions
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Surfing Game")

# Colors
WHITE = (255, 255, 255)
BLUE = (0, 0, 255)

# Surfer properties
surfer_width, surfer_height = 50, 50
surfer_x, surfer_y = WIDTH // 2, HEIGHT - surfer_height - 20
surfer_speed = 5

# Main game loop
clock = pygame.time.Clock()
running = True

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Move the surfer
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        surfer_x -= surfer_speed
    if keys[pygame.K_RIGHT]:
        surfer_x += surfer_speed

    # Draw the surfer
    screen.fill(WHITE)
    pygame.draw.rect(screen, BLUE, (surfer_x, surfer_y, surfer_width, surfer_height))

    pygame.display.flip()
    clock.tick(60)  # Limit frame rate to 60 FPS

pygame.quit()
sys.exit()
