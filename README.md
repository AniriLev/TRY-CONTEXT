# TRY-CONTEXT
    # TRY CONTEXT
    #### Video Demo:  <https://youtu.be/q8CJ-nEKclg>
    #### Description:
    This project is designed for learners who want to improve their English.

    As an English teacher, the most frequent question I am asked is “What is the most comfortable way to learn vocabulary?”. But I am an English learner myself as well, and I understand the struggle of those who don’t possess a high level of the language. And it so happened that I do know how to improve vocabulary without monotonous hours of memorizing words. And the secret is "CONTEXT". Words should be alive; they should have some purpose, and the purpose is the information they deliver, so there is no better way than the context. Carrying this weight of knowledge, I decided to build a program to help learners. It takes new words and creates a sentence in order to make words "alive" by showing how to use them. But showing the context is not enough to remember the words — one must understand them. So the program satisfies this need as well. Based on the sentence it has built, the program creates a question for the user to answer and checks its correctness.

    In a nutshell, the idea of the project is to prompt a user for words of different types (e.g. nouns, verbs, etc.), create a sentence and a question based on the sentence, and check the user’s answer.

    Now let me explain how the program works.

    1.  After starting the program, a user sees greetings as well as a self-introduction:
    "Hi! I know the best way to learn new words, and it is CONTEXT. So try me and check how well you can understand your newly learned words! I will make one sentence and one question, and your goal is to analyze the sentence and answer the question to check if you understood the CONTEXT. Let's start!"
    This part is done by the main function.

    2.  Then the program prompts the user for 2 words of each type: nouns, transitive verbs, intransitive verbs, adjectives, places, and times. However, if the user provides fewer than 2 words or does not provide words at all, then the program handles this too by putting default words: "cat" and "fish" for nouns, "eat" for transitive verbs, "sleep" for intransitive verbs, "cute" for adjectives, "at home" for places, and "on Monday" for times. If the user enters more than 2 words, then the program randomly chooses the necessary number of words for sentence building. After that, a dictionary with word types and input word lists is made.

    3.  After all words are gathered, the program randomly chooses a sentence structure and the words that are necessary for this structure. It then puts them in a list that carries mini-lists with words and their word types in the order they should appear in the sentence, based on the randomly chosen form. This part is done by the function "generate_sentence".

    4.  When the sentence is gathered, it’s only left to apply grammar rules to it. This is done by the function "check_sentence". This function puts the article "the" in front of nouns or adjectives with nouns, but not pronouns. It also handles possessions and subject-verb relations. After all the checks, the program prints the final sentence.

    5.  The next step is a question, and it is built by a function named "generate_questions". The function takes the sentence that has been made and, with the help of the library spaCy, makes a dictionary with the role of each word and the word in the sentence. After that, the function chooses a random question form and builds the list as in the function "generate_sentence". The same function then handles subject-verb relations.

    6.  After the question is printed, it is time for the program to check the user’s answer. This is done by the function "check_answers". This function takes the sentence, the question, and the dictionary of words and their types. Then the function prompts the user for an answer and compares it with previously prepared correct answers or with the original sentence if the answer does not look like either of the prepared ones. If the user’s answer does not match the prepared ones, then the function compares the answer with the original sentence using the function "SequenceMatcher" from the built-in library "difflib". The logic of this correctness assessment is based on how close the answer is to the original sentence.

    If the user’s answer is correct (or similarity is greater than 0.3 for usual sentences and 0.1 for sentences with "Who"), then the program prints congratulations. If the user’s answer is not correct, then the program asks the user to try 3 more times. If the user does not give a correct answer after 3 attempts, then the program prints the correct answer and some cheers.

    In reality, I did not have to use "difflib" to check the answer; I could have used spaCy again, but I wanted to try a different approach.

    7.  The next step was testing.
    I tested "generate_sentence" and "check_sentence" just by comparing correct outputs with those of the function. But I tested "generate_questions" with "random.seed" to test each type of output. And the function "check_answers" I tested with "monkeypatch" to check desired input.
