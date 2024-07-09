# GAME-snake
#ИГРА ЗМЕЙКА


Цель: создать игровое приложение с использованием языка программирования Python и библиотеки Pygame, которые обеспечивают возможности разработки игр на основе объектно-ориентированных принципов, поддержку изображений, анимации, управление основным игровым объектом (Персонажем).



Что нужно сделать:
Создать игровое поле
Создать игровой объект “Змейка”
Создать игровой объект “Яблоко”
Реализовать алгоритм добавления
блоков к змейке в случае поедания
яблока



#Установите Pygame, выполнив команду pip install pygame в командной строке.
#код игры


import random
import pygame

size = 30
half_size = size // 2

res = 750 
res = res // size // 2 * 2 * size + size
FPS = 12

clock = pygame.time.Clock()
screen = pygame.display.set_mode((res, res))
snake_frame_speed = 5
frame_counter = 0 

score = 0 
snake_start_pos = res // 2 - half_size
lenght = 4
dirX, dirY = 0, size
direction = {"w": (0, - size), "s": (0, size), "a": (-size, 0), d":(size, 0)}
snake = [(snake_start_pos, snake_start_pos)]
apple = (random.ranrage(0, res -size, size), random.randrange(0, res - size, size))
   
def apple_gen():
    global apple, score, lenght
    apple = (random.randrange(0, res -size, size), random.randrange(0, res - size, size))
    for snake_num in range(len(snake)):
       if apple[0] == snake[snake_num[0] and apple[1] == snake[snake_num][1]:
            apple_gen <-()
       else:
        apple = (random.randrange(0, res -size, size), random.randrange(0, res - size, size))
        break
    score += 1
    lenght += 1
  

while true:
	frame_counter += 1
        pygame.display.set_caption("Змейка.Счёт:" + str(score))
        for event in pygame.event.get():
        if evenr.type == pygame.QUIT:
            quit()


        screen.fill((0, 0, 0))

        [pygame.draw.rect(screen, (0, 160, 0), (x, y, size, size)) for x, y in snake]
        
         pygame.draw.circle(screen, (260, 0, 0), apple[0] + half_size, apple[1] + half_size), half_size) 

         
	if frame_counter % snake_frame_speed == 0:
        newX = snake[-1][0] + dirX
        newY = snake[-1][1] + dirY
        snake.append((newX, newY))
	snake = snake[-lenght-1:]

	if apple[0] == snake[-1][0] and apple[1] == snake[-1][1]:
	  apple = (random.randrange(0, res -size, size), random.randrange(0, res - size, size))
	  score += 1
	  lenght += 1
        
        key = pygame.key.get_pressed()
        if key[pygame.K_w]:
           if (dirX, dirY) != direction["s"] #направления движения
            dirX, dirY = direction["w"]
        elif key[pygame.K_s]:
           if (dirX, dirY) != direction["w"]
            dirX, dirY = direction["s"]
        elif key[pygame.K_a]:
            dirX, dirY = direction["d"]
            if (dirX, dirY) != direction["a"]
        elif key[pygame.K_d]:
            dirX, dirY = direction["a"]
             if (dirX, dirY) != direction["d"]

	if snake[-1][0] <= -size or snake[-1][0] >= res or snake[-1][1] <= -size or snake[-1][1] >= res:
	    print("You lose!")
	    quit() 
	
       clock.tick(FPS)
       pygame.display.flip()
