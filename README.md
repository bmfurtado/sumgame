# Sum Shuffle

A neon arcade puck-merging game for iPhone: **glide · collide · combine**.

**Play it here: <https://bmfurtado.github.io/sumgame/>**

Aim with either gesture — drag upward to point where you want to shoot, or drag downward to pull back like a pool cue (the shot fires opposite your pull) — then release to launch numbered pucks up the board. Pucks glide and bounce off walls and each other; when two pucks of equal value collide hard enough, they fuse into one puck worth their sum (1+1=2, 2+2=4, …). Build the single TARGET number (shown in the top panel and watermarked on the board with its recipe) to score points. A preview shows the next target so you can plan ahead, and pucks one merge away from the target pulse in its color.

The dashed launch line is a one-way barrier: pucks pass it on the way up but can never come back behind it, and shots that stall before reaching it are cleared away. Merged pucks keep some follow-through momentum, so a well-aimed shot can chain several merges in one go. The value you launch is drawn from all powers of 2 up to the biggest puck on the board, with higher values increasingly rare.

Two modes:

- **Timed** — 90 seconds on the clock; every completed target scores points and adds bonus seconds scaled to its difficulty. Best score is saved. The ❚❚ button at the top pauses the round (it also auto-pauses if the app goes to the background).
- **Zen** — no timer, no score. Just build targets at your own pace (the HUD counts how many); the MENU button in the top-right returns to the title screen.

Sound can be toggled from the title screen or the pause screen; the setting persists between sessions.

## Running locally

Everything is in a single [index.html](index.html) (physics via the Matter.js CDN, all sprites drawn on canvas, all sounds synthesized with WebAudio — no build step, no other assets). Serve the folder with any static file server, e.g.:

```
npx http-server -p 8123
```

Then browse to `http://<your-machine>:8123/` — from an iPhone on the same network for the intended experience. Add to Home Screen for fullscreen play.

## Tuning

Gameplay constants live at the top of the script in `index.html`: round length (`START_TIME`), bonus seconds per completed target (`OBJ_TIME`), points per target (`OBJ_POINTS`), the minimum collision speed for merging (`MERGE_SPEED`), glide friction (`FRICTION_AIR`), merge follow-through (`MERGE_CARRY`), launch value odds (`LAUNCH_DECAY`), and launch power range.

## License

[GPLv2](LICENSE)
