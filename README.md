# Fine-Tune-to-translation
## Introduction:
The goal of this project is to solve a machine translation problem from German to English by fine-tuning a pre-trained model. The pre-trained model has already learned the basic patterns and structures of both languages, but we want to improve its performance by fine-tuning it on a specific task.
## Our model
The basic model we decided to fine-tune in our project is T5-Base. 
## Link to our model 
https://technionmail-my.sharepoint.com/personal/ofir_haim_campus_technion_ac_il/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fofir%5Fhaim%5Fcampus%5Ftechnion%5Fac%5Fil%2FDocuments%2Fsaved&ga=1
## Fine Tuning
The first step was to add a prefix to the sentences in German. The prefix we used is “translate German to English: ”. We added this prefix at the beginning of each sentence. This basic model got sufficient results already. However, to improve even more, the next step was to use the root and modifiers in the unlabeled file. Before each sentence in the paragraph in German, we inserted the string: ‘[Root: ‘root’, Modifiers: ‘modifiers’]’, with ‘root’, ‘modifiers’ being the root and modifiers in the corresponding paragraph in English. For our model to learn how to use the roots and modifiers properly, we had to train it with the roots and modifiers as well, although we did not have the roots and modifiers for the training set. We used Spacy’s trained model for dependency parsing on each English paragraph to find its roots and modifiers and added it to the German paragraphs in the same way mentioned above.
Another approach we used was to enlarge our dataset (from the approved files). We extracted the sentences from HW1 files (train, test, and competition files). Since the T5 model is already trained on the inverse task of translating English to German, we simply added the prefix “translate English to German: ” to find the sentences in German, which we added to the dataset as the source language. We trained the model using a hugging-face trainer and a pretrained tokenizer of the chosen model.
## Accuracy in Validation
Overall, our model got a maximal BLEU score of 38 on the validation file. 
