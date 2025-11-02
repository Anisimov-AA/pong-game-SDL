Classic two-player Pong in C using SDL2 for real-time rendering and physics simulation

<div align="center">
  <img src="img/pong.jpg" alt="Pong Game" width="600"/>
</div>

## Setup

**Requirements:** C compiler (GCC), SDL2

1. install SDL2 (Ubuntu)
```bash
sudo apt update && sudo apt install libsdl2-dev
```

2. compile
```bash
gcc pong.c -o pong -lSDL2
```

3. run
```bash
./pong
```

## Usage

**Controls:**
- **Player 1** (Left paddle): `W` = up, `S` = down
- **Player 2** (Right paddle): `↑` = up, `↓` = down

**Gameplay:**
1. Launch → ball starts moving in random direction
2. Use paddles to bounce ball back to opponent
3. Ball resets to center when it exits screen (no scoring yet)
4. Close window or press ESC to exit

## Architecture
```
pong.c
├── Structs
│   ├── Paddle    # position (x,y,w,h) + velocity
│   └── Ball      # position (x,y,w,h) + velocity (vx,vy)
├── Physics
│   ├── move_paddle()           # updates paddle Y based on velocity
│   ├── move_ball()             # updates ball position + wall collision
│   ├── ball_paddle_collision() # AABB collision detection + bounce
│   └── reset_ball_position()   # center ball with random velocity
└── Game Loop
    ├── keyHandler()  # processes W/S/↑/↓ input
    └── main()        # render loop (clear → draw → present)
```
