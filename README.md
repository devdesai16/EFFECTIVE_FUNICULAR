# EFFECTIVE_FUNICULAR
#I am sharing with you all my first application in python3 which is a word dictionary
import json
from difflib import get_close_matches



data = json.load(open("data.json"))



def translate(w):
    w = w.lower()
     

    if w in data:

        return data[w]

    elif w.title() in data:
        return data[w.title()]
    elif w.upper() in data:
        return data[w.upper()]
        
        
        

    elif len(get_close_matches(w,data.keys())) > 0:
        yn =  input("Did you mean %s instead Enter Y for  yes N for no : " % get_close_matches(w,data.keys())[0])
        if yn == "Y":
            return data[get_close_matches(w,data.keys())[0]]
        elif yn == "N":
            return "Plzz check the word,Its not correct"
        else:
            return "The word you entered is invalid"    
        



    else:
        return "Plzz check the word,Its not correct"
    

word = input("Enter word : ")

output = translate(word)
if type(output) == list:
    for items in output:
        print(items)
else:
    print(output)

    
