import random
from midiutil.MidiFile import MIDIFile

# Δημιουργία MIDI αρχείου
mf = MIDIFile(1)
track = 0
time = 0
mf.addTrackName(track, time, "My New Composition")
mf.addTempo(track, time, 120)

# Προσθήκη καναλιού και ορισμός οργάνου
channel = 0
volume = 100
mf.addProgramChange(track, channel, time, 0)

# Δημιουργία ρυθμού
for i in range(16):
    pitch = random.randint(40, 80)
    duration = random.choice([0.25, 0.5, 0.75, 1])
    mf.addNote(track, channel, pitch, time, duration, volume)
    time += 0.25

# Αποθήκευση αρχείου
with open("my_composition.mid", "wb") as outf:
    mf.writeFile(outf)
