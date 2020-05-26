# BinaryEncoder
Change words and sentences into binary!

    #imports
    import simplegui

    #varriables
    user_word = ""
    binary_word = ""
    word_message = ""

    #helper functions
    def binary_encode(message):							#changes the message to binary
        global binary_word, word_message
        for char in message:							#for loops that changes characters to binary
            binaryCode = bin(ord(char))					#change character into binary 
            binaryCode = str(binaryCode)
            binary_word = binary_word + binaryCode + " "
        while "b" in binary_word:						#removes b from the string
            a = binary_word.find("b")
            binary_word = binary_word[:a] + binary_word[a+1:]
        print("binary_word: ", binary_word)
        word_message = "Your encoded text is: "

    #event handlers
    def draw(canvas):									 #draw handler
        canvas.draw_text("Welcome to Binary Encoder!", (65,75), 50, "white")
        canvas.draw_text("Enter your word and click encode to find the binary version.", (100,120), 20, "#c095c4")
        canvas.draw_text(word_message, (50,200), 15, "#9aa4a6")
        canvas.draw_text(binary_word, (50,215), 10, "#9aa4a6")

    def input_word_handler(word_input):					 #event handler for the word input
        global user_word
        user_word = word_input
        print("user_word: ", user_word)

    def button_encode_handler():
        binary_encode(user_word)

    #create the frame
    frame = simplegui.create_frame('Binary Encoder', 700, 300)

    #set and create the handlers
    frame.set_canvas_background("#131b8f")					 #sets the background color of the canvas
    frame.set_draw_handler(draw)						 #sets the draw handler
    frame.add_input("Word",input_word_handler,100)
    frame.add_button ("Encode", button_encode_handler)

    #start frame
    frame.start()
