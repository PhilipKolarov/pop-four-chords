# pop-four-chords
This code will produce a pop chord progression upon receiving a tonic (first) chord
def next_chord_function(current_chord_index, next_chord_index, next_chord, note_list, a, b, c):
    if current_chord_index > a:
        next_chord_index = int(current_chord_index) - b
        next_chord = note_list[next_chord_index]
    else:
        next_chord_index = int(current_chord_index) + c
        next_chord = note_list[next_chord_index]
    return next_chord_index, next_chord


print("Insert a chord. If minor, write 'm' after the letter. We'll return the four pop chords!")
tonic_chord = input()
minor_condition = False
tonic_chord_index = 0
note_list = ['A', 'A#', 'B', 'C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#']

if len(tonic_chord) == 1 or len(tonic_chord) == 2 and tonic_chord[1] == '#':
    tonic_chord_index = note_list.index(tonic_chord)
elif tonic_chord[1] == 'm':
    minor_condition = True
    tonic_chord_index = note_list.index(tonic_chord[0])
elif tonic_chord[2] == 'm':
    minor_condition = True
    note = tonic_chord[0] + tonic_chord[1]
    tonic_chord_index = note_list.index(note)

second_chord = ''
third_chord = ''
forth_chord = ''
second_chord_index = 0
third_chord_index = 0
forth_chord_index = 0

if minor_condition == False:
    if tonic_chord_index > 4:
        second_chord_index = tonic_chord_index - 5
        second_chord = note_list[second_chord_index]
    else:
        second_chord_index = tonic_chord_index + 7
        second_chord = note_list[second_chord_index]
    if second_chord_index > 9:
        third_chord_index = second_chord_index - 10
        third_chord = note_list[third_chord_index]
    else:
        third_chord_index = second_chord_index + 2
        third_chord = note_list[third_chord_index]
    third_chord_note = third_chord
    third_chord = third_chord_note + 'm'
    if third_chord_index > 3:
        forth_chord_index = third_chord_index - 4
        forth_chord = note_list[forth_chord_index]
    else:
        forth_chord_index = third_chord_index + 8
        forth_chord = note_list[forth_chord_index]

else:
    second_chord_index, second_chord = next_chord_function(tonic_chord_index, second_chord_index, second_chord, note_list, 3, 4, 8)
    third_chord_index, third_chord = next_chord_function(second_chord_index, third_chord_index, third_chord, note_list, 4, 5 ,7)
    forth_chord_index, forth_chord = next_chord_function(third_chord_index, forth_chord_index, forth_chord, note_list, 4, 5, 7)

print(tonic_chord)
print(second_chord)
print(third_chord)
print(forth_chord)
