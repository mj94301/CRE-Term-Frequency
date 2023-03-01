# CRE-Term-Frequency
Using a pre-defined list of terms, we evaluate hundreds of employee reviews from Glassdoor to see what corporate real estate + facilities topics are on their minds.

ReadMe Notes

28 Feb 2023 - original


Use case scenario: 

Managers in the corporate real estate organization at a large company want to know the extent to which facilities-related topics are on the minds of employees when the employees talk about the company, e.g., on Glassdoor.

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
   use a txt file instead of a csv file
   store the results in a new csv file
   omit stop words
   use nltk to remove numbers as well
   what if the text data includes 2-word phrases we want to count as 1?
