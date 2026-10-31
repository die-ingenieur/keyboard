# keyboard
<img src="blob:chrome-untrusted://media-app/8dbbb3a4-83e2-4fad-9d44-a6619d1b2e82" alt="Screenshot 2026-10-25 23.42.25.png"/><img width="266" height="256" alt="image" src="https://github.com/user-attachments/assets/0b1ecc17-d5be-43c1-9218-529fd5aad4bb" />

I was very curious to make a keyboard where you could record notes and play them back cycling through different instruments which was my inspiration for this project.

It works like the midi-keyboard (the starter for half-life) but you can record notes.
<img width="557" height="506" alt="image" src="https://github.com/user-attachments/assets/b28e03c4-41ee-4729-a952-33380c74a529" />
## parts
- I used pads to be able to produce the sounds
- used a rotary encoder to choose different instruments
- switches to record , play and pause
- a esp-32 S3 Zero as the microcontroller

## how it works
- the code simply stores the notes in a matrix allowing you replay the entire matrix to a device that can play the notes.
- you will need the software to recognise the board as a midi device.

Schematic bellow :
<img width="485" height="431" alt="image" src="https://github.com/user-attachments/assets/ea6fac76-b2de-4a3b-b872-189397a9caf4" />

