# CRE-Term-Frequency
Using a pre-defined list of terms, we evaluate hundreds of employee reviews from Glassdoor to see what corporate real estate + facilities topics are on their minds.

ReadMe Notes

28 Feb 2023 - original


Use case scenario: 

Managers in the corporate real estate (CRE) organization at a large company want to know the extent to which facilities-related topics are on the minds of employees when the employees talk about the company, e.g., on Glassdoor.

In this case, we use as the source text several hundred comments made on Glassdoor about the company Cisco Systems.  The comments (employee reviews) were captured via RSS feed over a period of some months.

By reviewing employee reviews across several companies, we developed a list of CRE-related terms that employees use in their general comments.  The idea is to know what employees say about their workplace when they are making general comments, as opposed to what they would say in response to a survey about their workplace.


Files:

1.  Glassdoor_Comments.txt is the source file of the reviews captured from Glassdoor using an RSS feed for Cisco Systems only.

2.  CRE_Named_Entities.txt is the file with the list of terms related to how employees see the results of decisions made by the company's corporate real estate organization, e.g., about amenities, facilities features, location, and programs.

3.  CRE Term Frequency Counter.py is the python script for completing the count.  This script, when run, creates an output file called Output_count_of_CRE_terms.csv.  This python script was written by the Chat GPT AI (chat.openai.com).  The original instruction, responses, and updated instructions are listed below.

4.  Output_count_of_CRE_terms.csv is the output created by the script.

5.  CRE Terms Frequency Overview.twbx is a Tableau file that visualizes the results of the count.

6.  CRE Terms Category Source.xlsx is a file that categorizes the individual terms under one of 5 types of decisions that are typically made by CRE departments:  Facility Features, Location, Programs, Services / Amenities, Technology



Instructions and Responses from Chat GPT AI used to write the Python code.

Original Instruction:  write a python script to calculate and store word frequencies from a csv file

Updates to instructions made to make the script fit the overall vision:

   Instruction Update #1:  use a txt file instead of a csv file
   
       Sure! Here's an updated version of the Python script that reads in a plain text file and calculates the frequency of each word in it, storing the results in a dictionary...Replace myfile.txt with the path to your text file. The script opens the file using the open() function, reads the contents of the file using the read() method, and splits the text into words using the split() method. It then loops through each word in the text, converts it to lowercase, removes any punctuation, and adds it to a dictionary. If the word is already in the dictionary, it increments its count, otherwise it adds it with a count of 1. Finally, it prints out the word frequencies.
   
    Instruction Update #2:  store the results in a new csv file  
    
   Chat GPT Response:  Sure! Here's an updated version of the Python script that reads in a plain text file, calculates the frequency of each word in it, and stores the results in a new CSV file..Replace myfile.txt with the path to your text file, and word_freq.csv with the desired name and path for the new CSV file. The script opens the text file, reads the contents of the file, splits the text into words, and calculates the frequency of each word using the same logic as before.

Then, the script opens a new CSV file using the csv.writer module, writes a header row with the column names 'word' and 'frequency', and then loops through the dictionary and writes each word and its frequency to a new row in the CSV file. Finally, it closes the file.
      
   Instruction Update #3:  omit stop words
   
   Chat GPT Response:  Sure! Here's an updated version of the Python script that reads in a plain text file, calculates the frequency of each non-stop word in it, and stores the results in a new CSV file...This version of the script first loads the stop words using the nltk.corpus module. Then, it opens the text file, reads the contents of the file, splits the text into words, and calculates the frequency of each non-stop word by checking whether the word is in the stop words set.

To remove punctuation from each word, we use the string.punctuation constant and the translate() method. We also check whether the word is an empty string, to avoid adding empty rows to the dictionary.

Finally, the script opens a new CSV file using the csv.writer module, writes a header row with the column names 'word' and 'frequency', and then loops through the dictionary and writes each word and its frequency to a new row in the CSV file.
   
   Instruction Update #4:  use nltk to remove numbers as well
   
   Chat GPT Response:  Sure! Here's an updated version of the Python script that uses NLTK to remove stopwords and numbers, calculates the frequency of each remaining word in the text file, and stores the results in a new CSV file...This version of the script uses NLTK to tokenize the text into words and tag each word with its part of speech (POS). We then use a WordNet lemmatizer to reduce each word to its base form based on its POS tag.

To remove numbers, we add a check for word.isnumeric() in the conditional that adds each word to the dictionary.

Note that we also modified the POS handling to treat any non-adjective, non-noun, non-verb word as a noun, to ensure that the lemmatizer works as expected.

Finally, the script opens a new CSV file using the csv.writer module, writes a header row with the column names 'word' and 'frequency', and then loops through the dictionary and writes each word and its frequency to a new row in the CSV file.
   
   Instruction Update #5:  what if the text data includes 2-word phrases we want to count as 1?
   
   Chat GPT Response:  If the text data includes 2-word phrases that you want to count as a single word, you can modify the script to treat each 2-word phrase as a single token. One way to do this is to use the ngrams() function from the nltk library to extract all 2-grams (i.e., consecutive pairs of words) from the text, and then join each 2-gram into a single token.

Here's an updated version of the Python script that handles 2-word phrases as a single token...In this version of the script, we use the wordpunct_tokenize() function from nltk to tokenize the text into words and punctuation marks, and then use ngrams() to extract all 2-grams from the text. We then join each 2-gram into a single token using ' '.join(gram), and concatenate the resulting list of tokens with the list of individual words.

The rest of the script is the same as before, with the exception of the tokenization step. Note that this approach assumes that all 2-grams in the text should be treated as single tokens. If there are specific pairs of words that should not be joined (e.g., "New York" should be counted as two separate words), you will need to modify the code accordingly.
   
   
