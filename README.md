# word_combination_from_sequence

A phoneme is a sound unit (similar to a character for text). We have an extensive pronunciation dictionary (think millions of words). Below is a snippet:
ABACUS AE B AH K AH S,
BOOK B UH K,
THEIR DH EH R,
THERE DH EH R,
TOMATO T AH M AA T OW,
TOMATO T AH M EY T OW
Given a sequence of phonemes as input (e.g. ["DH", "EH", "R", "DH", "EH", "R"]), find all the combinations of the words that can produce this sequence (e.g. [["THEIR", "THEIR"], ["THEIR", "THERE"], ["THERE", "THEIR"], ["THERE", "THERE"]]). You can preprocess the dictionary into a different data structure if needed.

Solution:

1. Preprocessing the Pronunciation Dictionary
-> The pronunciation dictionary is preprocessed into a defaultdict called to_words, where each key is a tuple of phonemes, and the value is a list of words that have that pronunciation.

-> This allows for O(1) lookups of words based on phoneme sequences.

2. Used DP approach to efficiently find all possible word combinations that match the input phoneme sequence.
-> A list sequences is used to store all possible word combinations for each substring of the phoneme sequence.

-> The algorithm iterates(backwards) from the end of the phoneme sequence to the start.

-> For each start position, it iterates over possible end positions to form candidate phoneme sequences.

-> If a candidate sequence exists in to_words, it combines the matching words with all valid sequences from sequences[end + 1].


The final result is stored in sequences[0], which contains all valid word combinations for the entire phoneme sequence.

Time Complexity:
1. Preprocessing: O(m1 * m2 * m3), where:

m1 = number of words in the dictionary,

m2 = average number of phoneme sequences per word,

m3 = average length of a phoneme sequence.
2. Dynamic Programming: O(n² * W), where:

n = length of the input phoneme sequence,

W = maximum number of matching words for any phoneme sequence.

Space Complexity:
1. Preprocessing: The to_words dictionary requires O(m1 * m2 * m3) space.
2. Dynamic Programming: The sequences list stores all possible word combinations, which can grow exponentially in the worst case.
-> The space complexity is O(S), where S is the total number of valid word combinations.
