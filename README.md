# Language-background-classifier
Supervised classification system to identify language background of English language learner
## Feature Choices
The features we chose to use are `has_asian_name`, `has_european_name`, `get_type_token_ratio`, `get_lemmatized_percentage`, `get_lexical_density`, `average_verb_length`, `average_noun_length`, `get_readability_score`, `asian_european_ratio` and `get_percentage_punctuations_with_no_spaces_after`.

While looking at the text, we noticed that people would sometimes mention Asian and European cities and names. We chose to make two boolean features, has_asian_text and has_european_text based on whether any of these names show up in the text or not. The assumption is that if Asian names show up in a text, it is more likely to be written by native Asian speakers and if European names show up in a text, it is more likely to be written by native European speakers. We also created asian_european_ratio which calculates the ratio of Asian cities and names to European cities and names in the text.

We also noticed that Asian speakers would commonly forget to add a space after punctuation. In Japanese and Mandarin, there is no space after periods. This makes this mistake more common for native Asian speakers than it is for native European speakers. We created a feature, get_percentage_punctuations_with_no_spaces_after to calculate how often this occurs in a text.
Spanish and French have a lot of words that are similar to English words, such as ‘temperature’ which is ‘temperatura’ in Spanish and ‘température’ in French. The assumption is that these common words tend to be longer words and European speakers would use them more often than Asian language speakers who do not share these common words with English. For this reason, we created two features, average_verb_length and average_noun_length.

Other features we chose to use are get_type_token_ratio, get_lemmatized_percentage, get_lexical_density and get_readability_score. We chose to use the type/token ratio and the lexical density because we thought that speakers of one language category might show more lexical diversity in English text than the other. The lemmatized percentage shows how often the text has the dictionary version of a word (the lemma) versus how often other forms of the word were used. Lastly, we chose the readability_score because we thought that speakers of one language category might write text in a way that is easier to interpret compared to the other language category.

## Results
In the end, we got an accuracy score of 71% on the test set. The model did work as we expected. We had to drop the has_european_name feature. This feature turned out less useful than has_asian_names. This might be because Asian names look very different compared to English ones. They can be written in Korean, Japanese or Mandarin which is very different from English. European names are written in the same alphabet as English and it can be harder to distinguish between Spanish, French and English names. There is some randomness to the model. In one run, we got 77% accuracy on our dev set. 

These are our accuracy scores on the dev set during feature ablation. We can see that the accuracy score is higher once has_european_name is removed.

The decision tree that the model generated is shown below.

## Group Contributions
Every member of our group contributed significantly. We started by discussing which ten features we should use in our model, then we each began working on our own parts. Chao Ding extracted all the relevant text from the HTML files. Shengjie Zhang and Mrinal Grover created five functions each for all of our features, as well as tests. Oksana Necio built and tested a decision tree classifier based on the extracted features, as well as wrote the report.
