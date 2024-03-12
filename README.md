# Alteryx_Enron_data_wkflow

Cybersecurity -
Enron
https://en.wikipedia.org/wiki/Enron
Objective
– To familiarize you with Text Analytic techniques used in fraud investigation
– Using Alteryx for cybersecurity audit procedures

Overview
Enron Corporation was a very large energy, commodities and service company based in Houston, Texas. The company 
became infamous for accounting fraud that was discovered in 2001. As part of the discovery of the fraud, federal 
investigators examined the emails sent by top company employees. They also posted the emails online so others could 
search through them. This email repository has become very popular in understanding how employees use email and to 
perform analysis of real-world data. 
Data
For this case, you will perform select cybersecurity audit procedures on 26,751 emails sent by top Enron Corporation 
employees. The cybersecurity audit procedures you will perform are designed to test if employees are adhering to 
cybersecurity policies that have been (hypothetically) adopted by Enron Corporation. 
The emails included in the data set are real. This email corpus does not include all of the emails released; it has been 
limited in several ways. For example, group emails are excluded and other emails that require advanced data analytics 
procedures are excluded. The email data has been modified to simplify some of the tasks you are asked to perform. 
The file, Cybersecurity_case_studies_Enron.csv (or a variation of), contains the data in a CSV file format. Each email 
is listed on its own line. All students will get individually different files – hence your answers will be different

The cybersecurity audit procedures should be performed using Alteryx software. Alteryx software is a strong candidate for 
this type of analysis because it can be applied easily to future emails by changing the input file. Also, Alteryx allows for 
powerful manipulation that is auditable. Suggest you watch the following videos before you start the assignment: 
1. Getting Started with a Tour of Alteryx Designer
2. Parsing Data Using the Text to Columns Tool
3. Splitting Text into Multiple Columns in Alteryx
4. Basic Blending Join Data Sets on Key Fields
5. Learn Regular Expressions In 20 Minutes
6. Alteryx Regex Tool Demonstration
7. How Does RegEx Tool work in Alteryx | Alteryx Tutorial
8. Introduction to Regular Expressions

► Use “Comment Tool” to label parts of your code which answers each question above (the “Comment Tool” can be 
found under the “Documentation” tab.


► For purposes of this assignment, all RegEx expressions should not be case sensitive. A couple of hints for the first 
parse step
Adapted from Cybersecurity case studies – Enron by Sumantra Sarkar 4
© 2021 Ernst & Young Foundation (US). All Rights Reserved.
SCORE no. 13607-211US_2
– - the regular expression you input is case sensitive ("sam" is different from "Sam")
– - parentheses separate groups
– - \s separates whitespace characters
► Be aware that finding emails that match certain criteria does not indicate the Enron Corporation employee necessarily 
violated the cybersecurity control. You will need to manually review the results that are flagged in your searches and 
use your professional judgment to decide if the email violates the cybersecurity policy (or if additional testing would be 
warranted).[Note: Professional skepticism facilitates the appropriate exercise of professional judgment by the 
auditor, particularly regarding decisions about, for example: The nature, timing and extent of audit procedures to be 
performed - from IIASB]
► To answer the questions, you may need to play around with Alteryx and use more tools. There are many 
resources available including the Alteryx website: https://help.alteryx.com/20223/designer/tools
► Regarding the first regular expression, here are a couple of resources and hints to put you on the right track 
https://help.alteryx.com/20223/designer/regex-tool
► One of the first options on the side is to remove null columns. A quick and easy way to get rid of the null values is 
by removing all null columns using the Data Cleansing tool! After running the data cleanse, you shouldn't have any 
null columns anymore and you can attach your RegEx tool to the data cleanse to start the first parse.
Detailed instructions:
1. Import your data. Note that in your data configuration, you will need to modify the field length from 254 characters to 
100,000 (a conservative estimate) to capture the full amount of the data. [Screenshot 1: Take your first screenshot 
after importing your data file to start the process. Refer to screenshot sample file]
Next, prepare the file for analysis. Do the following:
a. Split the header information from the body of the message. The header data is all data that comes before the 
subject line in an email. That is, the header contains the message ID, the email of the message sender and the 
email address of the message receiver. The body of the message contains the subject line and all information 
until the end of the email. Label the email header “EmailHeader” and the body of the message “EmailBody.” The 
screenshot below shows what the output should look like. All screenshots show only a few rows and not 
necessarily all answers. To split the header information from the body of the message, use the RegEx tool. You 
may want to view YouTube Video before starting the assignment – documentation available at this link
A few hints might be helpful:
► Make sure to increase the field length when you import the data or the data will be truncated during the 
import. 
► For your regular expression, use a “non-greedy” operator with a quantifier. Non-greedy operators stop 
searching once they find the first match for the term in searching from the beginning of the string to the end of 
the string, whereas greedy operators search from the end of the string to the beginning of the string until they 
find the matching term. You need to do this because some emails contain the word “Subject:” multiple times 
(e.g., forwarded emails often include this). To make a quantifier non-greedy add the ? after the quantifier. For 
example, “+?” makes the + quantifier non-greedy.

b. From the message header, extract the Message-ID. Extract just the digits from the header. For example, a 
Message-ID might look like the following: <25828831.1075855376669.JavaMail.evans@thyme>. You should 
extract just 25828831.1075855376669 as the Message-ID. Label the extracted data as “MessageID.” The 
screenshot below shows you what the output should look like.
c. From the message header, extract the date. The date information will appear like “Sun, 2 Dec 2001 18:45:38 -
0800 (PST).” Label this data “EmailDate.” The screenshot below shows you what the output should look like.
d. From the message header, extract the email address of the person who sent the email. Label this data 
“EmailFrom.” The screenshot below shows you what the output should look like.
As a hint, some of the emails have been altered in the data set. For this problem, if you return a result that looks 
like “legal <.taylor@enron.com>” as part of your response that is OK. You do not have to parse out the “legal <.” 
portion of the email.
e. From the message header, extract the email address of the person who received the email (again, with another 
RegEx tool). Label this data “EmailTo.” The screenshot below shows you what the output should look like.
[Screenshot 2 here. Refer to screenshot sample file]
2. To gain an understanding of the employees’ emailing behavior, output each of the following items. For this problem, 
output the requested item using a Browse activity. As a hint, you will need to parse the “EmailDate” field that you 
extracted in problem 1.c. into the following fields “DateDay” (which shows just the three-letter code for day), 
“DateMonthYear” (which shows the three-letter month and four-digit year) and “DateHour” (which shows the two-digit 
hour). The screenshot below shows what the output from this step would look like (the screenshot does not show all 
columns or rows of the data).
Use the RegEx tool to input a regular expression that parses the date into day, month, and hour. [Screenshot 3:
Take your next screenshot here at the RegEx tool, showing the Regular Expression used. Refer to screenshot sample 
file.)

a. Output the number of emails that are sent each month for each year. Sort the table so that the month and year 
that have the most emails are listed at the top. The screenshot below shows you what the output should look like.
[Screenshot 4: Take your next screenshot here of how you summarized the data by month and year. Refer to 
screenshot sample file.]
b. Output the number of emails that are sent each day of the week. You do not have to worry about different time 
zones for this analysis. You can use the hour of the day for the time zone the employees are in (i.e., you can 
combine hours without considering the time zone). Sort the table so that the day of the week that has the most 
emails is listed at the top. The screenshot below shows you what the output should look like.
c. Output the number of emails that are sent each hour of the day. Sort the table so that the hour of the day is 
shown in ascending order. The screenshot below shows you what the output should look like.
[Screenshot 5: Take your next screenshot after step 2c, showing all tools used in step 2. Refer to screenshot sample 
file.]

3. Company policy says that employees should not send sensitive information via email, unless the email is encrypted. 
Test to see if the following sensitive information was sent in the body of an unencrypted email (note that all emails in 
the file are unencrypted): Social Security number (SSN), employer identification number (EIN) and individual taxpayer 
identification number (ITIN). You are only required to search for those numbers that follow the patterns shown 
following. 
Be aware that the RegEx “Match” function in Alteryx requires a match of the entire string and not just part of the string. 
Thus, your expressions will need to match the entire body of the email when searching for these numbers (as a hint, 
include a “.*” at the beginning and end of each search string).
a. SSN: “###-##-####” (search should include the dashes)
[Screenshot 6: Take your next screenshot here at the RegEx tool, showing the Regular Expression you used. 
Refer to screenshot sample file.]
After the RegEx tool, use a filter tool to filter for emails that have a TRUE match.
[Screenshot 7: Take your next screenshot here at the filter tool, showing what was filtered. Refer to screenshot 
sample file.]
b. EIN: “##-#######” (search should include the dashes)
Use the RegEx tool to look for EIN matches. After the RegEx tool, use a filter tool to filter for emails that have a 
TRUE match
c. ITIN: “9##-##-####” (search should include the 9 to begin and the dashes)
Use the RegEx tool to look for ITIN matches. After the RegEx tool, use a filter tool to filter for emails that have a 
TRUE match
Combine your results with a UNION tool [Screenshot 8: Take your next screenshot at the union tool. Refer to screenshot 
sample file] from all three searches into a single list, select the fields below and display the output using a Browse activity. 
Display the following: 
1. Message-ID
2. Email address of the person who sent the email
3. Email address of the person who received the email
4. What information was improperly sent (email body)
[Screenshot 9: Take your next screenshot at the select tool, showing the fields you have selected. Refer to 
screenshot sample file.]
4. Company policy forbids sharing usernames and passwords. In the past, some employees sent usernames and 
passwords to others via email. Search the email corpus for any email that may list usernames and passwords. To 
simplify this, you should only search for emails that include “username:” followed by “password:” where any text can 
be included between those two words. Also, you should assume the word immediately following “username:” is the 
username and the word immediately following “password:” is the password. 
Use the RegEx tool to separate the usernames and passwords from the emails. [Screenshot 10: Take your next 
screenshot here after using the RegEx tool. Refer to screenshot sample file.]
Then use the filter tool to filter out the emails that do not contain any usernames or passwords in the emails. 
[Screenshot 11: Take your next screenshot here after using the filter tool. Refer to screenshot sample file.]
Select the fields below and display the output using a Browse activity and display only the following: 
a. Message-ID
Adapted from Cybersecurity case studies – Enron by Sumantra Sarkar 8
© 2021 Ernst & Young Foundation (US). All Rights Reserved.
SCORE no. 13607-211US_2
b. Email address of the person who sent the email
c. Email address of the person who received the email
d. Username
e. Password for those emails that do not have a null username 
The screenshot below shows you what the output should look like.
5. Company policy prohibits senior-level employees from interviewing with company competitors. All of the employees 
for which you have emails are required to adhere to this policy. Test to see if any employees are discussing 
interviewing with competing firms.
a. To perform this test, you should identify competitors. To identify competitors, search the email addresses of 
receivers for any of the following domain names (the domain name is the part of the email address after the @ 
symbol): “williams.com,” “dynegy.com,” “duke-energy.com,” “entergykoch.com,” “entergy.com,” 
“constellation.com,” “constellationmgt.com” or “estutenws11.energy.williams.com,” Among the emails sent to 
competitors, search for any emails that contain any of the following words: “resume,” “interview” or “application.” 
Use the RegEx tool to separate the email domain from the email field. [Screenshot 12: Take your next 
screenshot here after using the RegEx tool. Refer to screenshot sample file.]
Next, use the RegEx tool to match email domains to competitor email domains. [Screenshot 13: Take your next 
screenshot here after using the RegEx tool. Refer to screenshot sample file.]
Filter for emails that match competitor email domains.
Use another RegEx tool to identify emails (with competitors) that contains the words: “resume”, “interview”, or 
“application”. [Screenshot 14: Take your next screenshot here after using the RegEx tool. Refer to screenshot 
sample file.]
Filter for emails that contain the words: “resume”, “interview”, or “application”
Output your results using a Browse activity and display:
1. Message-ID
2. Email address of the person who sent the email
3. Email address of the person who received the email
4. The full text of the email 
[Screenshot 15: Take your final screenshot at the select tool, showing the fields you have selected. Refer to 
screenshot sample file.]
The screenshot below shows you what the output should look like.

Questions:
(For questions that require explanations, the explanation should have at least 3 sentences to support your argument)
1. Identify the top 5 email IDs who have sent the most emails.
a. Prepare a histogram with those top 5 email senders in a descending order where x-axis is person’s email name/id
and the y-axis is number of emails sent. (10 points)
i. Hint 1: Start where the results of the tool include columns for email and dates. 
ii. Hint 2: Use the “Histogram Tool” and connect a “Browse Tool” to it to view results.
b. Please describe the process of how you arrived at this answer. Please include screenshots. (4 points)
2. Company policy says that employees should not send sensitive information via email, unless the email is encrypted. 
Each email available is unencrypted. Review each email that potentially violates this policy and draw conclusions about 
whether the email is a violation of the policy. 
a. Which one seems most problematic? Why? (6 points)
b. Can you draw any inferences about what is happening from some of these scenarios? (3 points)
c. If the company were considering internal control changes for the future, what could it do to prevent these 
situations? (3 points)
3. Company policy forbids sharing usernames and passwords. In the past, some employees sent usernames and 
passwords to others via email. Review each email and draw conclusions about whether the email is a violation of the 
policy. 
a. Please identify who are they? (3.5 points)
b. What should the company should do moving forward? Why? (3.5 points)
4. Company policy prohibits senior-level employees from interviewing with company competitors. Read all of the emails 
and decide whether the employee violated company policy. 
c. How many employees applied to, are trying to get an interview with, or sent resumes to Enron’s competitors? (5 
points)
d. How would you improve your search string to better match emails showing evidence of a violation of the 
company’s policy, without flagging emails that did not violate the policy (you don’t have to improve the string, but 
brainstorm ways that would improve the string)? Why? (5 points)
5. Often, employees think of unique searches that reveal interesting and useful information. Write down a question that 
you would like to test and then answer it. Explain why you want to test your question and the findings from your testing. (7 
points)
6. Why is it important and necessary to keep a database of emails sent and received? What do you think would happen 
if this cybersecurity procedure was not put in place? Why? (5 points)
