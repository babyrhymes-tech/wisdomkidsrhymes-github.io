import pygame
import sys

# Initialize pygame
pygame.init()
pygame.mixer.init()

# Screen setup
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("Rainbow Rhymes & Colors")

# Colors of the rainbow
rainbow_colors = [
    ("Red", (255, 0, 0)),
    ("Orange", (255, 165, 0)),
    ("Yellow", (255, 255, 0)),
    ("Green", (0, 128, 0)),
    ("Blue", (0, 0, 255)),
    ("Indigo", (75, 0, 130)),
    ("Violet", (148, 0, 211))
]

# Font setup
font = pygame.font.SysFont("Comic Sans MS", 40)

# Rhymes for each color
rhymes = {
    "Red": "Red is the color of an apple so sweet,\nA rainbow treat that can't be beat!",
    "Orange": "Orange is bright like the setting sun,\nLearning colors is so much fun!",
    "Yellow": "Yellow shines like the morning light,\nIt makes the rainbow big and bright!",
    "Green": "Green is the grass where we love to play,\nIt makes us happy every day!",
    "Blue": "Blue is the sky so wide and high,\nIt paints the rainbow in the sky!",
    "Indigo": "Indigo deep like the ocean's hue,\nA special color just for you!",
    "Violet": "Violet blooms in flowers fair,\nA rainbow color beyond compare!"
}

# Sound files (replace with your actual audio file paths)
sounds = {
    "Red": "sounds/red_song.wav",
    "Orange": "sounds/orange_song.wav",
    "Yellow": "sounds/yellow_song.wav",
    "Green": "sounds/green_song.wav",
    "Blue": "sounds/blue_song.wav",
    "Indigo": "sounds/indigo_song.wav",
    "Violet": "sounds/violet_song.wav"
}

# Function to play rhyme sound
def play_rhyme(color_name):
    pygame.mixer.music.stop()
    pygame.mixer.music.load(sounds[color_name])
    pygame.mixer.music.play()

# Main loop
current_index = 0
clock = pygame.time.Clock()

# Play first rhyme at start
play_rhyme(rainbow_colors[current_index][0])

while True:
    screen.fill((255, 255, 255))

    # Get current color
    color_name, color_value = rainbow_colors[current_index]

    # Draw rectangle of the color
    pygame.draw.rect(screen, color_value, (200, 100, 400, 200))

    # Display color name
    text_surface = font.render(color_name, True, (0, 0, 0))
    screen.blit(text_surface, (350, 320))

    # Display rhyme
    rhyme_lines = rhymes[color_name].split("\n")
    for i, line in enumerate(rhyme_lines):
        rhyme_surface = font.render(line, True, (0, 0, 0))
        screen.blit(rhyme_surface, (100, 400 + i * 50))

    # Event handling
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_RIGHT:
                current_index = (current_index + 1) % len(rainbow_colors)
                play_rhyme(rainbow_colors[current_index][0])
            elif event.key == pygame.K_LEFT:
                current_index = (current_index - 1) % len(rainbow_colors)
                play_rhyme(rainbow_colors[current_index][0])

    pygame.display.flip()
    clock.tick(30)
