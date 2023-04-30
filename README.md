from pygame import *
from random import randint
window = display.set_mode((1000,1000))
display.set_caption("Стуклер вс мутантс")
class GameSprite(sprite.Sprite):
    def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
        super().__init__()
        self.image = transform.scale(image.load(player_image), (size_x, size_y))
        self.speed = player_speed
        self.rect = self.image.get_rect()
        self.rect.x = player_x
        self.rect.y = player_y
    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))

class Player(GameSprite):
    def update(self):
        keys = key.get_pressed()
        
    def fire(self):
            bullet = Bullet("bullet.png", self.rect.centerx, self.rect.top , 10, 10, 10)
            bullets.add(bullet)

class Bullet(GameSprite):
    def update(self):
        self.rect.x -= self.speed
        if self.rect.x < 0 :
            self.kill()
