Download Link: https://assignmentchef.com/product/solved-spell-checking-program-using-hash-tables
<br>
5/5 - (1 vote)

ObjectiveThe objective of this assignment is to implement a spell checking program using hash tables and separate chaining.Your ProgramGeneral Overview: Most spell checkers use hashing to determine if a given word in a document is correct (that’s why they can check your spelling as you type).



The Dictionary: First, you must set up a dictionary in which to look up words. When your program starts, use either JFileChooser or JOptionPane.showInputDialog or a Scanner object to allow the user to specify the dictionary file to load. (The dictionary file is words.txt, which can be found in the Content Browser on D2L with this assignment in an Assignment 3 folder under Assignments.) Read in the dictionary file. There is one word per line. Insert each word in the dictionary into a Table ADT.

Implement the Table ADT as follows:

•    Use a hash table of size 94321 (a prime number that gives a load factor of about 0.5).

•    Use separate chaining (in which each table slot is a (singly) linked list of nodes) to resolve collisions. Node words may be inserted at the front of the appropriate linked list.

•    Use the polynomial hashing algorithm discussed in class to hash each word — use Horner’s method to compute the polynomial hash code and take the result of each operation mod the table size to avoid integer overflow. In Horner’s method, use a = 13 when evaluating your polynomial p(a).

Checking the spelling in a file: After you have read in the dictionary file and stored them in a table, you must check the spelling of all words in another file, a document file.

Again, use either JFileChooser or JOptionPane.showInputDialog or a Scanner object to allow the user to specify the document file to load. The file book.txt is provided for testing. This file contains multiple words per line. You are encourage to test against other document files.

For each word in the document file, perform a Table search to see if the word is in the dictionary. If a word isn’t present in the Table, then it is a spelling error (that is, a mis-spelled word). It should be pointed out that words.txt is not a very complete dictionary and so some words that are spelled correctly will be flagged as erroneous.

Once your program has process the document file, indicate the spelling errors by printing each mis-spelled word once. With each word, include the line numbers on which the word appears (in the order in which you found them). Note that a word can be mis-spelled multiple times on a single line. So an mis-spelled word might generate the following line in the output:

Invalid word “Michiko” found on lines 1 59 21 21

To keep track of mis-spelled words and on which lines they occur, use another hash table, known as the mis-spelled word table, to keep track of the mis-spelled words (and where they were found in the document): • This hash table should have size 2797.

•    An mis-spelled word will only be added to the mis-spelled word table if the word is not already in the mis-spelled word table. Thus, you must do a search for the word, and only add the word to the mis-spelled word table if it is not found.

•    Each element of the mis-spelled word table will contain two things: a word and a queue of the line numbers on which this mis-spelled word was found in the document file. The queue of line numbers is an ordinary queue: line numbers are enqueued at the end of the queue. You may implement this as a linked list (of your choice).

•    If a mis-spelled word is already in the table, simply add the new line number to the end of queue of line numbers for that word.

After the document file is completely processed, traverse the mis-spelled word table. For each mis-spelled word found in the table, print out both the word and the numbers of all lines on which it appeared (removing the line numbers one-by-one from the line number queue). Note that the output will likely be in alphabetic order, which is perfectly okay.

Suggestions•    The document file that you will read has punctuation that must be handled. You must ensure that no word is seen as error because it had punctuation attached to it. Note that an apostrophe is a valid part of a word and should not be considered punctuation. Punctuations other than apostrophe will split a word into two. Eg) Input abc-def becomes two words abc and def.

Suggestion: If StringinLine is an input line from the document file, then the command nLine.trim().split( “[^a-zA-Z’]+” ) splits the line into tokens using one or more characters that are NOT letters or an apostrophe as the splitting pattern (“^” means “not”). Try this on some sample strings to see what it does.

•    Hashing “A” and “a” produces different values, but you would not expect them to be different words in a dictionary. To manage this difference, convert all text to all lower case when processing (this comment also applies to the dictionary words). This conversion simplifies things and makes the spell checker more reliable.

Suggestion: The helpful String method toLowerCase() will do the job for you and a good idea to do this as soon as an input is read in.

•    You must organize you program into appropriate classes. You should have a class representing your hash table, a class representing a the data to be stored in the hash table, a class representing a queue, a class representing the data to be stored in your queue, and a main application class. You may have other classes if you need them.

•    Do not have more than one hash table class. There should be one hash table class, that can be used for both the dictionary words and the mis-spelled words (of course you’ll need two hash table objects). The key is to make the class that holds your hash table data data flexible enough to handle both situations.

•    Your data structures (hash tables, queues, etc.) should NOT contain any program logic specific for solving this program. Instead, they just should implement the standard features as discussed in class.

•    Test your program using a small dictionary and document file first. Using small files along with small hash table sizes (say size=5) will allow you to quickly check if your code is working or not. A small dictionary file test-dict.txt is provided, along with a small document file test-file.txt.

Sample output: Your output should take the following form (note that this is not the output for the given data files):

There are a total of 10 invalid words:

Invalid “cant” found on lines 1

Invalid “pewter” found on lines 1

Invalid “turbine” found on lines 1

Invalid word “Michiko” found on lines 1 59 21 21

Invalid word “fortune” found on lines 1

Invalid word “fashionable” found on lines 3 5 9 11 11 13

Invalid word “Popcorn” found on lines 5 90 104

Invalid word “10” found on lines 7 139

Invalid word “sensei” found on lines 7 139