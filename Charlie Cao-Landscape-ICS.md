# Charlie Cao's Landscape-Assignment-ICS3U

import pygame
from pygame.locals import K_ESCAPE , QUIT , MOUSEBUTTONDOWN , KEYDOWN

pygame.init()

WIDHT = 640
HEIGHT = 480
SIZE = (WIDHT , HEIGHT)
place_x = 180
place_y = 60
radius =30
screen = pygame.display.set_mode(SIZE)
clock = pygame.time.Clock()

def draw_cloud(place_x, place_y, radius):

    pygame.draw.circle(screen, (255, 255, 255), (place_x, place_y), radius)
    pygame.draw.circle(screen, (255, 255, 255), (place_x + 14, place_y + 2), radius)
    pygame.draw.circle(screen, (255, 255, 255), (place_x + 19, place_y - 21), radius)
    pygame.draw.circle(screen, (255, 255, 255), (place_x + 52, place_y - 4), radius)

def draw_sun(place_x, place_y, radius): 
    pygame.draw.circle(screen, (255,255,0), (place_x, place_y),radius)

def draw_tower():
    pygame.draw.polygon(screen,(255,128,0), ((635,285), (415,285), (525,200)))
    pygame.draw.rect(screen, (138,71,38), (430,360,200,150))
    pygame.draw.rect(screen, (238,154,0), (475,285,30,75))
    pygame.draw.rect(screen, (238,154,0), (560,285,30,75))
    pygame.draw.rect(screen, (238,154,0), (515,285,30,75))

def draw_car():
    pygame.draw.rect(screen,(0,255,127),(100,335,150,100))
    pygame.draw.rect(screen,(0,255,127),(225,385,100,50))
    pygame.draw.rect(screen,(0,255,127),(30,385,100,50))
    pygame.draw.rect(screen,(72,118,255),(110,340,60,40))
    pygame.draw.rect(screen,(72,118,255),(180,340,60,40))
    pygame.draw.rect(screen,(0,0,0),(235,435,60,50))
    pygame.draw.rect(screen,(0,0,0),(70,435,60,50))

running = True
while running:
    
    for event in pygame.event.get():
        if event.type == KEYDOWN:
            if event.key == K_ESCAPE:
                running = False
        elif event.type == QUIT:
            running = False
    
    screen.fill((51,161,201))

    draw_cloud(place_x, place_y + 50, radius)
    draw_cloud(place_x + 180, place_y + 20, radius)
    draw_cloud(place_x + 300, place_y + 50, radius)
    draw_cloud(place_x + 400, place_y + 10, radius)
    draw_cloud(place_x - 110, place_y + 10, radius)
    draw_sun(place_x + 100, place_y , radius)
    draw_tower()
    draw_car()
    
    if place_x >= 0 or place_y >= 0:
     place_x += 2
    
    if place_x >= WIDHT or place_y >= HEIGHT:
     place_x = 180  
     place_y = 60
    
    pygame.display.flip()
    clock.tick(30)

pygame.quit()
