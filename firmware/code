# Vibe coding some firmware because python is boring 🤑
# this code isn't fully finished yet, i'll finish it during build season. 
import keypad
import touchio
from adafruit_midi.control_change import ControlChange
from microcontroller import pin
import digitalio
import board
import time

from kmk.extensions.media_keys import MediaKeys
from kmk.extensions.rgb import RGB, AnimationModes
from kmk.keys import KC
from kmk.kmk_keyboard import KMKKeyboard
from kmk.modules.encoder import EncoderHandler
from kmk.modules.midi import MidiKeys
from kmk.modules.potentiometer import PotentiometerHandler
from kmk.scanners import Scanner
from kmk.scanners.keypad import KeysScanner

record_pin=pin.GPIO10,
stop_pin=pin.GPIO11,
delete_pin=pin.GPIO12
#these is the code to check is the record/ stop/ delete switches are pressed or not.
record_switch =digitalio.DigitalInOut(record_pin) # record switch
record_switch.direction =digitalio.Direction.INPUT
record_switch.pull =digitalio.Pull.UP
stop_switch= digitalio.DigitalInOut(stop_pin) # stop switch
stop_switch.direction =digitalio.Direction.INPUT
stop_switch.pull =digitalio.Pull.UP
delete_switch =digitalio.DigitalInOut(delete_pin) # delete switch
delete_switch.direction =digitalio.Direction.INPUT
delete_switch.pull =digitalio.Pull.UP
# KMK doesn't have a scanner for touch pads, so here's a tiny one.
# Don't touch the pads while the board boots - they calibrate on startup!
class TouchScanner(Scanner):
    def __init__(self, pins):
        self.pads = [touchio.TouchIn(p) for p in pins]
        self.pressed = [False] * len(pins)

        # track if pin was on or off,


        self.recorded_sequence = [
        ]

    @property
    def key_count(self):
        return len(self.pads)
    def scan_for_changes(self):
        recording_active= not self.record_switch.value
        pause_active= not self.pause_switch.value
        delete_active= not self.delete_switch.value


        for i, pad in enumerate(self.pads):
            touched = pad.value
            if touched != self.pressed[i]:
                self.pressed[i] = touched

                #records note
                if touched and recording_active:
                    self.recorded_sequence.append(i)
                if ... 
                  for note in self.recorded_sequence:
                    midi.send(NoteOn(note, 127))
                    time.sleep(0.5) 
                    midi.send(NoteOff(note, 0))

                return keypad.Event(i + self.offset, touched)


keyboard = KMKKeyboard()
# These have to be created before we use KC.MIDI_NOTE / KC.VOLU below
midi = MidiKeys()
media_keys = MediaKeys()

keyboard.matrix = [
    # Touch pads 1-7 (keys 0-6)
    TouchScanner([pin.GPIO1, pin.GPIO2, pin.GPIO3, pin.GPIO4, pin.GPIO5, pin.GPIO6, pin.GPIO7]),
    # Switches SW1-SW3 (keys 7-9)
     #switchpins =[ pin.GPIO10, pin.GPIO11, pin.GPIO12]
]

# Touch pads play a C major scale, switches play drum sounds
keyboard.keymap = [[
    KC.MIDI_NOTE(60), KC.MIDI_NOTE(62), KC.MIDI_NOTE(64), KC.MIDI_NOTE(65),
    KC.MIDI_NOTE(67), KC.MIDI_NOTE(69), KC.MIDI_NOTE(71),
   # KC.MIDI_NOTE(36), KC.MIDI_NOTE(38), KC.MIDI_NOTE(42),  # kick, snare, hi-hat
]]
# Rotary encoder controls your computer's volume
encoder = EncoderHandler()
encoder.pins = ((pin.GPIO8, pin.GPIO9, None),)  # A = TX, B = RX, no button
encoder.map = [((KC.VOLD, KC.VOLU, KC.NO),)]
for i in rnage time chekc to die fff
# Sliders send MIDI CC 1 (mod wheel) and CC 7 (volume)
#sliders = PotentiometerHandler()
#sliders.pins = (
#    (pin.GPIO2, lambda state: midi.send(ControlChange(1, state.position))),
#    (pin.GPIO1, lambda state: midi.send(ControlChange(7, state.position))),
#)
#,sliders
keyboard.modules = [midi, encoder]
keyboard.extensions = [
    media_keys,
    RGB(pixel_pin=pin.GPIO13, num_pixels=3, val_default=80, animation_mode=AnimationModes.RAINBOW),
] 

if __name__ == '__main__':
    keyboard.go()
