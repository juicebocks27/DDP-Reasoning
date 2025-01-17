normalize(arrangement)
Definition: Normalizes an arrangement to its lexicographically smallest rotation to handle circular symmetry.
Logic: Generates all rotations of the arrangement and selects the smallest one lexicographically.
seating_positions_from_arrangement(arrangement)
Definition: Converts an arrangement into a dictionary mapping chair positions (1 to 6) to representatives.
Logic: Enumerates the arrangement and creates a dictionary with chair numbers as keys.
who_sits_on_left(seating_positions, person)
Definition: Determines who sits to the left of a specific person in a seating arrangement.
Logic: Finds the position of the person and calculates the left position (cyclically).
who_sits_on_right(seating_positions, person)
Definition: Determines who sits to the right of a specific person in a seating arrangement.
Logic: Finds the position of the person and calculates the right position (cyclically).
