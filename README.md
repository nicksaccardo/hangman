# hangman
#Random word to guess each time
import random

#funtion to welcom the user
def WelcomeScreen():
    #have the user type thier name
    name = input("ENTER YOUR NAME: ")
    #WELCOME USER
    print("HOWDY", name, "LETS PLAY A GAME OF HANGMAN USING BASKETBALL TEAMS")
    print("#######################")
    print("TRY TO GUESS THE WORD IN 6 TRIES OR LESS")
    #call the main-function
    hangman()
    print() #print a blank row






#the start of the main program
def hangman():
    #here we have a list of words
    #random.choice picks a random word from this
    word = random.choice(["knicks", "lakers","raptors","warriors"])
    #WE ONLY WANT USER TO ENTER ALPHABETH LETTERS

    validLetters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'

    #USER WILL ONLY HAVE 8nick
    # GUESSES
    turns = 8
    guessed = '' #THE LETTERS THAT THE USER HAS GUESSED

    #MAKE SURE WE HAVE A WORD
    while len(word) > 0:
        msg = ""
        missed = 0 #WE START THE GAME WITH 0 FAILS OFCOURSE
        #HERE WE USE A FOR LOOP
        #CHECKING IF THE LETTER THAT THE USER GUESSED IS IN OUR RANDOM WORD

        for letter in word:
            if letter in guessed:
                #IF IT IS, THEN PRINT THAT LETTER IN THAT SPOT
                msg = msg + letter
            else:
            #OTHERWISE PRINT A BLANK "_"
                msg = msg + "_" + " "
                missed += 1 #NOW WE NEED TO INCREMENT THAT MISSED BY 1
        if msg == word:
            #IF THE GUESSED ARE THE SAME AS THE RANDOM WORD:
            #OUTPUT THAT THE USER HAS 'WON'
            print(msg)
            print("YOU ARE CORRECT, THE WORD WAS: ", word)
            break #EXIT HERE SINCE THE WORD IS CORRECCT
        #OTHERWISE, ASK AGAIN
        print("GUESSED THE WORD: ", msg)
        #HERE WE ASK THE USER FOR MORE INPUT
        guess = input()

        if guess in validLetters:
            guessed = guessed + guess
        else:
            #IF IT IS NOT, TELL THEM TO TYPE A VALID LETTER
            print("ENTER A VALID LETTER: ")
            #GUESS AGAIN
            guess = input()
            #THIS IS A WAY TO OUTPUT/PRINT THE HANGMAN
        if guess not in word:
            turns = turns - 1
            if turns == 7:
                print("  o")
            if turns == 6:
                print("  o")
                print("  |")
            if turns == 5:
                print("  o")
                print("  |")
                print(" / \ ")
            if turns == 4:
                print("  o")
                print("  |")
                print(" / \ ")
            if turns == 3:
                 print("  o")
                 print("- |")
                 print(" / \ ")
            if turns == 2:
                 print("  o")
                 print("- | -")
                 print(" / \ ")
            if turns == 1:
                 print("YOU HAVE FAILED AS USUAL:", word)
                 break

WelcomeScreen()
