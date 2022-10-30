# Alien-Invasion

In this chapter, you’ll set up Pygame, and then create a rocket ship that moves right and left and fires bullets in response to player input. In the next two chapters, you’ll create a fleet of aliens to destroy, and then continue to refine the game by setting limits on the number of ships you can use and adding a scoreboard.

In Alien Invasion, the player controls a rocket ship that appears at the bottom center of the screen. The player can move the ship right and left using the arrow keys and shoot bullets using the spacebar. When the game begins, a fleet of aliens fills the sky and moves across and down the screen. The player shoots and destroys the aliens. If the player shoots all the aliens, a new fleet appears that moves faster than the previous fleet. If any alien hits the player’s ship or reaches the bottom of the screen, the player loses a ship. If the player loses three ships, the game ends.

For the first development phase, we’ll make a ship that can move right and left and fires bullets when the player presses the spacebar. After setting up this behavior, we can create the aliens and refine the gameplay.

# display.set_mode()

The object we assigned to self.screen is called a surface. A surface in Pygame is a part of the screen where a game element can be displayed. Each element in the game, like an alien or a ship, is its own surface. The surface returned by display.set_mode() represents the entire game window. When we activate the game’s animation loop, this surface will be redrawn on every pass through the loop, so it can be updated with any changes triggered by user input.

# bg_color

The color value (230, 230,230) mixes equal amounts of red, blue, and green, which produces a light gray background color.

# adding ship image

You can use almost any type of image file in your game, but it’s easiest when you use a bitmap (.bmp) file because Pygame loads bitmaps by default. Pay particular attention to the background color in your chosen image. Try to find a file with a transparent or solid background that you can replace with any background color using an image editor. Your games will look best if the image’s background color matches your game’s background color. Alternatively, you can match your game’s background to the image’s background.

# NOTE

In Pygame, the origin (0, 0) is at the top-left corner of the screen, and coordinates increase as you go down and to the right. On a 1200 by 800 screen, the origin is at the top-left corner, and the bottom-right corner has the coordinates (1200, 800). These coordinates refer to the game window, not the physical screen. When you’re centering a game element, work with the center, centerx, or centery attributes of a rect. When you’re working at an edge of the screen, work with the top, bottom, left, or right attributes. There are also attributes that combine these properties, such as midbottom, midtop, midleft, and midright.
Depending on the screen width you’ve chosen, the alignment of the first row of aliens might look slightly different on your system.

# Moving Ship Both Left and Right

In __init__(), we add a self.moving_left flag. In update(), we use two separate if blocks rather than an elif to allow the ship’s rect.x value to be increased and then decreased when both arrow keys are held down. This results in the ship standing still. If we used elif for motion to the left, the right arrow key would always have priority. Doing it this way makes the movements more accurate when switching from right to left when the player might momentarily hold down both keys.