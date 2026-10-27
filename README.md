# space-invaders
import pyame,sys
from spaceship import Spaceship
from laser import laser


pygame.init()


SCREEN_WIDTH = 750
SCREEN_HEIGHT = 700


GREY = (29, 29, 27)


screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.disply.set_caption("Python Space Invadors")


clock = pygame.time.Clock()


spaceship = Spaceship(SCREEN_WIDTH, SCREEN_HEIGHT)
spaceship_group = pygame.sprite.GroupSingle()
spaceship_group.add(spaceship)


laser = Laser((100.100))
laser2 = laser((100, 200))
laser_group = pygame.sprite.Group()
laser_group.add(laser, laser2)


while True:
    #Checking for events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()


#updating
spaceship_group.update()


#Drawing
screen.fill(GREY)
spaceship_group.draw(screen)
laser_group.draw(screen)


pygame.display.update()
clock.tick(60)



import pygame


class Spaceship(pygame.sprite.Sprite):
    def__init__(self, positioning):
        super().__init__()
        self.screen width = screen_width
        self.screen.height = screen_height
        self.image = pygame.image.load("Graphics/spaceship.png")
        self.rect = self.image.get_rect(midbottom = (self.screen_width/2, self.screen_height))








import pygame, sys
from spaceship import Spaceship


pygame.init()


SCREEN_WIDTH = 750
SCREEN_HEIGH = 700


GREY = (29, 29, 27)


screen = pygame.display.setmode((SCREEN_WIDTH,SCREEN_HEIGH))
pygame.display.set_caption("Python Space Invaders")


clock = pygame.time.Clock()


spaceship - Spaceship()
spaceship_group = pygame.sprite.GroupSingle()
spaceship_group.add(spaceship)


while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()


    #updating
    spaceship_group.update()
    lasers_group.update()


    #Drawing
    screen.fill(GREY)
    spaceship_group.draw(screen)
    spaceship_group.sprite.lasers_group.draw(screen)


     pygame.display.update()
     clock.tick(60)




import pygame
from laser import Laser


class Spaceship(pygame.sprite.Sprite):
    def_init_(self):
        super()._init_()
        self.screen_width = screen_width
        self.screen_height = screen_height
        self.image = pygame.image.load("Graphics/spaceship.png")
        self.rect = self.image.get_rect(midbottom = (self.screen_width/2, se;f.screen_height))
        self.speed = 6
        self.lasers_group = pygame.sprite.Group()
        self.laser.ready = True
        self.laser_time = 0
        self.laser_delay = 300


    def get_user_imput(self):
        keys = pygame.key.get_pressed()


          if keys[ygame.K_RIGHT]:
            self.rect.x +=self.speed


         if keys[pygame.K_LEFT]:
            self.rect.x -= self.speed


        if keys[pygame.K_SPACE]:
            laser = Laser(self.rect.center, 5, self.screen_height)
            self.lasers_group.add(laser)
 
    def update(self):
        self.get_user_input()
        self.constrain_movement()
        self.lasers_group.update()


    def constrain_movement(self):
        if self.rect.right > self.screen_width:
            self.rect.right = self.screen_width
        if self.rect.left < 0
            self.rect.left = 0
           
        def recharge_laser(self)
        if not self.laser_ready:
            currejt_time = pygame.time.get_ticks()




 import pygame


    class laser(pygame.sprite.Sprite):
     def__init__(self, position, speed. screenheight):
        super().__init__()
        self.image _ pygame.Surface((4,15))
        self.image.fill((243, 216, 63))
        self.rect = self.image.get_rect(center = position)
        self.speed = speed
        self.screen_height = screen_height
         
    def update(self):
        self.rect.y -= self.speed
        if self.rect.y> self.screen_height + 15 or self.rect.y < 0:
         
            print("Killed")   self.killed()
































































import pygame




class Spaceship(pygame.sprite.Sprite):
    def__init__(self, positioning, speed, screen_height):
        super().__init__()
        self.screen width = screen_width
        self.screen.height = screen_height
        self.image = pygame.image.load("Graphics/spaceship.png")
        self.rect = self.image.get_rect(midbottom = (self.screen_width/2, self.screen_height))


def get_user_input(self):
    keys = pygame.key.get_pressed()


    if keys[pygame.K_RIGHT]:
        self.rect.x += self.speed


    if keys[pygame.K_LEFT]:
        self.rect.x -= self.speed


def update(self):
    self.get_user_input()
    self.constrain_movement()


def constrain_movement(self):
    if self. rect.right > self.screen_width:
        self.rect.left = self.screen_width
    if self.rect.left < 0:
        self.rect.left + 0






import pygame


class Laser(pygame.sprite.Sprite):
    def__init__(self):
        super().__init__()
        self.image = pygame.Surface((4.15))
        self.image.fill((243, 216, 63))
        self.rect + self.image.get_rect(center = position)















import pygame
from settings import *
from player import Player
from alien import Alien
from laser import Laser
from obstacle import create_obstacles
pygame.init()
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Space Invaders")
clock = pygame.time.Clock()
font = pygame.font.Font(None, 36)
big_font = pygame.font.Font(None, 72)
player = Player()
player_lasers = pygame.sprite.Group()
alien_lasers = pygame.sprite.Group()
aliens = pygame.sprite.Group()
obstacles = pygame.sprite.Group()
score = 0
game_over = False
def create_alien_wave():
    aliens.empty()
    for row in range(5):
        for column in range(10):
            x = 120 + column * 55
            y = 80 + row * 45
            alien = Alien(x, y, row)
            aliens.add(alien)
def reset_game():
    global score, game_over
    score = 0
    game_over = False
    player.reset()
    player_lasers.empty()
    alien_lasers.empty()
    obstacles.empty()
    obstacles.add(create_obstacles())
    create_alien_wave()
obstacles.add(create_obstacles())
create_alien_wave()
alien_direction = 1
alien_timer = 0
alien_shoot_timer = 0
running = True
while running:
    dt = clock.tick(FPS) / 1000
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE and not game_over:
                player.shoot(player_lasers)
            if event.key == pygame.K_r and game_over:
                reset_game()
            if event.key == pygame.K_ESCAPE:
                running = False
    if not game_over:
        player.update()
        player_lasers.update()
        alien_lasers.update()
        # Move aliens as a formation.
        alien_timer += dt
        if alien_timer >= ALIEN_MOVE_INTERVAL:
            alien_timer = 0
            move_down = False
            for alien in aliens:
                alien.rect.x += ALIEN_MOVE_SPEED * alien_direction
                if (
                    alien.rect.right >= SCREEN_WIDTH - 20
                    or alien.rect.left <= 20
                ):
                    move_down = True
            if move_down:
                alien_direction *= -1
                for alien in aliens:
                    alien.rect.y += ALIEN_DROP_DISTANCE
        # Occasionally let a random alien fire.
        alien_shoot_timer += dt
        if alien_shoot_timer >= ALIEN_SHOOT_INTERVAL and aliens:
            alien_shoot_timer = 0
            shooter = list(aliens)[
                pygame.time.get_ticks() % len(aliens)
            ]
            alien_lasers.add(
                Laser(
                    shooter.rect.centerx,
                    shooter.rect.bottom,
                    1
                )
            )
        # Player laser vs aliens.
        for laser in list(player_lasers):
            hit = pygame.sprite.spritecollideany(
                laser,
                aliens
            )
            if hit:
                laser.kill()
                hit.kill()
                score += 10
        # Laser collisions with obstacles.
        for laser in list(player_lasers) + list(alien_lasers):
            pygame.sprite.spritecollide(
                laser,
                obstacles,
                True
            )
        # Alien lasers hitting player.
        if pygame.sprite.spritecollideany(
            player,
            alien_lasers
        ):
            game_over = True
        # Aliens reaching the player area.
        if any(
            alien.rect.bottom >= player.rect.top
            for alien in aliens
        ):
            game_over = True
        # New wave.
        if not aliens:
            create_alien_wave()
    screen.fill(BACKGROUND)
    obstacles.draw(screen)
    aliens.draw(screen)
    player_lasers.draw(screen)
    alien_lasers.draw(screen)
    screen.blit(
        player.image,
        player.rect
    )
    score_text = font.render(
        f"Score: {score}",
        True,
        TEXT
    )
    screen.blit(
        score_text,
        (20, 15)
    )
    controls = font.render(
        "Arrow keys / A-D to move   SPACE to shoot",
        True,
        TEXT
    )
    screen.blit(
        controls,
        (20, SCREEN_HEIGHT - 35)
    )
    if game_over:
        title = big_font.render(
            "GAME OVER",
            True,
            TEXT
        )
        restart = font.render(
            "Press R to restart or ESC to quit",
            True,
            TEXT
        )
        screen.blit(
            title,
            title.get_rect(
                center=(
                    SCREEN_WIDTH // 2,
                    SCREEN_HEIGHT // 2 - 30
                )
            )
        )
        screen.blit(
            restart,
            restart.get_rect(
                center=(
                    SCREEN_WIDTH // 2,
                    SCREEN_HEIGHT // 2 + 35
                )
            )
        )
    pygame.display.flip()
pygame.quit()




SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
FPS = 60
BACKGROUND = (10, 10, 25)
TEXT = (240, 240, 240)
PLAYER_SPEED = 350
PLAYER_SIZE = (55, 30)
LASER_SPEED = 500
LASER_SIZE = (5, 18)
ALIEN_SIZE = (34, 25)
ALIEN_MOVE_SPEED = 18
ALIEN_MOVE_INTERVAL = 0.35
ALIEN_DROP_DISTANCE = 20
ALIEN_SHOOT_INTERVAL = 1.2
OBSTACLE_SIZE = (90, 35)

import pygame
from settings import *
class Player(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface(
            PLAYER_SIZE,
            pygame.SRCALPHA
        )
        pygame.draw.polygon(
            self.image,
            (80, 220, 120),
            [
                (PLAYER_SIZE[0] // 2, 0),
                (0, PLAYER_SIZE[1]),
                (PLAYER_SIZE[0], PLAYER_SIZE[1]),
            ],
        )
        self.rect = self.image.get_rect(
            midbottom=(
                SCREEN_WIDTH // 2,
                SCREEN_HEIGHT - 60
            )
        )
        self.last_shot = 0
        self.shoot_delay = 0.35
    def reset(self):
        self.rect.midbottom = (
            SCREEN_WIDTH // 2,
            SCREEN_HEIGHT - 60
        )
    def update(self):
        keys = pygame.key.get_pressed()
        direction = 0
        if keys[pygame.K_LEFT] or keys[pygame.K_a]:
            direction -= 1
        if keys[pygame.K_RIGHT] or keys[pygame.K_d]:
            direction += 1
        self.rect.x += int(
            direction * PLAYER_SPEED / FPS
        )
        self.rect.left = max(
            self.rect.left,
            10
        )
        self.rect.right = min(
            self.rect.right,
            SCREEN_WIDTH - 10
        )
        self.last_shot = max(
            0,
            self.last_shot - 1 / FPS
        )
    def shoot(self, group):
        if self.last_shot <= 0:
            group.add(
                Laser(
                    self.rect.centerx,
                    self.rect.top,
                    -1
                )
            )
            self.last_shot = self.shoot_delay
from laser import Laser







import pygame
from settings import *
class Laser(pygame.sprite.Sprite):
    def __init__(self, x, y, direction):
        super().__init__()
        self.image = pygame.Surface(
            LASER_SIZE,
            pygame.SRCALPHA
        )
        pygame.draw.rect(
            self.image,
            (255, 240, 90),
            self.image.get_rect(),
            border_radius=2
        )
        self.rect = self.image.get_rect(
            center=(x, y)
        )
        self.direction = direction
    def update(self):
        self.rect.y += int(
            LASER_SPEED * self.direction / FPS
        )
        if (
            self.rect.bottom < 0
            or self.rect.top > SCREEN_HEIGHT
        ):
            self.kill








import pygame
from settings import *
class Alien(pygame.sprite.Sprite):
    def __init__(self, x, y, row):
        super().__init__()
        self.image = pygame.Surface(
            ALIEN_SIZE,
            pygame.SRCALPHA
        )
        if row == 0:
            color = (240, 90, 90)
        elif row < 3:
            color = (100, 180, 255)
        else:
            color = (190, 120, 240)
        pygame.draw.rect(
            self.image,
            color,
            (
                3,
                5,
                ALIEN_SIZE[0] - 6,
                ALIEN_SIZE[1] - 8
            ),
            border_radius=5
        )
        pygame.draw.circle(
            self.image,
            BACKGROUND,
            (11, 12),
            3
        )
        pygame.draw.circle(
            self.image,
            BACKGROUND,
            (23, 12),
            3
        )
        self.rect = self.image.get_rect(
            topleft=(x, y)
        )


Obstacle import pygame
from settings import *
class Obstacle(pygame.sprite.Sprite):
    def __init__(self, x, y):
        super().__init__()
        self.image = pygame.Surface(
            OBSTACLE_SIZE,
            pygame.SRCALPHA
        )
        pygame.draw.rect(
            self.image,
            (80, 190, 120),
            self.image.get_rect(),
            border_radius=8
        )
        # Cut-outs give the shield a simple arcade shape.
        pygame.draw.rect(
            self.image,
            BACKGROUND,
            (
                20,
                20,
                50,
                15
            )
        )
        self.rect = self.image.get_rect(
            midtop=(x, y)
        )
def create_obstacles():
    group = pygame.sprite.Group()
    positions = [
        SCREEN_WIDTH * 0.18,
        SCREEN_WIDTH * 0.39,
        SCREEN_WIDTH * 0.61,
        SCREEN_WIDTH * 0.82,
    ]
    for x in positions:
        group.add(
            Obstacle(
                int(x),
                SCREEN_HEIGHT - 150
            )
        )
    return group








import pygame
from settings import *
class Alien(pygame.sprite.Sprite):
    def __init__(self, x, y, row):
        super().__init__()
        self.image = pygame.Surface(
            ALIEN_SIZE,
            pygame.SRCALPHA
        )
        if row == 0:
            color = (240, 90, 90)
        elif row < 3:
            color = (100, 180, 255)
        else:
            color = (190, 120, 240)
        pygame.draw.rect(
            self.image,
            color,
            (
                3,
                5,
                ALIEN_SIZE[0] - 6,
                ALIEN_SIZE[1] - 8
            ),
            border_radius=5
        )
        pygame.draw.circle(
            self.image,
            BACKGROUND,
            (11, 12),
            3
        )
        pygame.draw.circle(
            self.image,
            BACKGROUND,
            (23, 12),
            3
        )
        self.rect = self.image.get_rect(
            topleft=(x, y)
        )

