# e.g.-metal-nightmare-
horrorgame
import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up the game window
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Metal Nightmare")

# Define colors
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)

# Game loop
running = True
while running:
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Clear the screen
    screen.fill(BLACK)

    # Update the display
    pygame.display.flip()

# Clean up
pygame.quit()
sys.exit()
# Player class
class Player(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((32, 32))
        self.image.fill(WHITE)
        self.rect = self.image.get_rect()
        self.rect.center = (screen_width // 2, screen_height // 2)
        self.speed = 5

    def update(self):
        # Handle player movement
        keys = pygame.key.get_pressed()
        if keys[pygame.K_LEFT]:
            self.rect.x -= self.speed
        if keys[pygame.K_RIGHT]:
            self.rect.x += self.speed
        if keys[pygame.K_UP]:
            self.rect.y -= self.speed
        if keys[pygame.K_DOWN]:
            self.rect.y += self.speed

# Enemy class
class Enemy(pygame.sprite.Sprite):
    def __init__(self, x, y):
        super().__init__()
        self.image = pygame.Surface((32, 32))
        self.image.fill((255, 0, 0))  # Red color for enemies
        self.rect = self.image.get_rect()
        self.rect.topleft = (x, y)
        self.speed = 3

    def update(self):
        # Enemy movement logic
        pass  # Placeholder for now

# Main game function
def main():
    # Create player
    player = Player()
    all_sprites = pygame.sprite.Group()
    all_sprites.add(player)

    # Game loop
    running = True
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False

        # Update sprites
        all_sprites.update()

        # Clear the screen
        screen.fill(BLACK)

        # Draw sprites
        all_sprites.draw(screen)

        # Update the display
        pygame.display.flip()

    # Clean up
    pygame.quit()
    sys.exit()

if __name__ == "__main__":
    main()
