Simple Wikipedia Bot:

A basic command-line python bot that fetches summaries from wikipedia using the 'wikipedia' library.

----

Features:
1. Accepts user input for any topic
2. Fetches summary using wikipedia api

   

Requirements:
Install 'Wikipedia' Library using :
bash or cmd:
      pip install wikipedia


import wikipedia

print("Bot: Hello! Ask me anything (type 'exit' to quit).\n")

while True:
    user_input = input("You: ")
    if user_input.lower() == "exit":
        print("Bot: Goodbye!")
        break

    try:
        # Search and get summary
        summary = wikipedia.summary(user_input, sentences=2)
        print("Bot:", summary)
    except wikipedia.exceptions.DisambiguationError as e:
        print("Bot: Your question is too broad. Try asking about one of these:")
        print(", ".join(e.options[:5]))
    except wikipedia.exceptions.PageError:
        print("Bot: I couldn't find anything related to that. Try rephrasing.")
    except Exception as e:
        print("Bot: Something went wrong:", str(e))

