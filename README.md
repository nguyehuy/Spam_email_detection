# Spam_email_detection
  This is my project to detect spam email
 
# Goal
  Many email services today provide spam filters that are able to classify emails
  into spam and non-spam email with high accuracy. In this project, I built your own spam filter.

	
## 1.Data
   Data contains 2 folder: Spam email and Non-spam email. Every folder contains serverals raw email.
 
 
## 2. Read_file(readfile.py):
   Read the content of the file give the url 

## 2.Preprocessing Emails (processemail.py):
   Take a look at a sample data:
   
		
		> Anyone knows how much it costs to host a web portal ?
		>
		Well, it depends on how many visitors youre expecting. This can be
		anywhere from less than 10 bucks a month to a couple of $100. You
		should checkout http://www.rackspace.com/ or perhaps Amazon EC2 if
		youre running something big..
		To unsubscribe yourself from this mailing list, send an email to:
		groupname-unsubscribe@egroups.com
		
		
   As you cas see, every email contains similar types of entities (numbers, other URLs, or other email addresses)
   and the specific entities (the specific URL or specific dollar amount) will be different in almost every email. So, this specific        entities are not necessary to classify, we need to change and remove them.
    
   In file processemail.py, I have implemented the folowing steps to preprocess email:
    
   * Remove header:
	
      Every email has a header, we need to remove the header
	     
   * Lower-casing:
	
      The email is conveted into lower case, so thar the captialization is ignored
	     
   * Stripping HTML tags:
	
      Removing the HTML tags in emai
	     
   * Normalizing email :
	
      All URLs are replace with the text 'httpaddr'
	     
      All email addresses are replace with the text 'emailaddr'
	     
      All numbers are replace with the text 'number'
	     
      All '$' are replace with the text 'dollar'
	     
   * Stemming Word:
	
      Reduce the word to their stemmed form. For example, "discount", "discounts", "discounted" and "discounting" 
	     
      are all replaced with "discount"
	     
   * Strip Punctuation:
	
      Remove all non-words (punctuation). All white spaces (tabs, spaces, newlines) have been 
	     
      trimmed to a single space character
	     
   * Remove stopwords: 
	
      Remove all the stopwords ('a', 'an', 'is', 'we', 'they'..) becasue it is not neccesary
	     
## 3. Get Vocabulary List (getvocabularylist.py):
   After processing the email, I have the list of words of every email. In this step, I will choose the vocabulary need to be used in my classifier and which one want to leave out
   In file getvocabularylist.py , I read all the contetn of the spam emails and choose 20000 words which are have the most occurrent. After that, I used these words to vectorize the data. 
   You can see this list in the file VocabularyList.txt
## 4. Vetorize the data (vetorize.py):
   In the file vetorize.py, I implemented he feature extraction that converts each email into a vector in 20000 dimensons. That is, xi=1 if the i-th word is in the email and xi = 0 if the i-th word is not present in the email
## 5. Training data (model.py):
	I wrote file model.py to train the data after we are done above steps. In this steps,first, I used Kfold library to randomly validate trainning data to 
	determine which algorithsm (svm, RandomForestClassifier, DecisionTreeClassifier, LogisticRegression) is the best. After that, I found LogisticRegression is the best algorithsm
	(you can uncomment the code to see that)
	Then, I used the GridSearch to find out the best parameter for my model
## 6.Main (main.py)
	In the main.py, I called all the class that I aready created to run my project. After that, I tested the accuracy. I got 0.994 accuracy in the test set with the parameter:
	L='l2' and C=100
## 7. Vocabulary (VocabularyList.txt):
	This file contains all the vocabularies that I have got in step 3.
	
# Contact Infomation 
  * Name:  Huy Nguyen
  * Email: ng.huy0708@gmail.com
  * Phone number: 046 547 1125
