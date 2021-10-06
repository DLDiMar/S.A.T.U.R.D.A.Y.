"""
#Virtual Assistant: S.A.T.U.R.D.A.Y.

Personal Assistant who collects data, reports time, day,
weather, and other commands

Rough Initial proof of concept

**Utilizes Wolfram Alpha, Wikipedia **

"""


import wolframalpha
import PySimpleGUI as simpleGUI
import wikipedia
import pyttsx3


client = wolfram.client("(insert keycode here)")


simpleGUI.theme('DarkPurple')
layout =[[simpleGUI.Text('Enter a command'), simpleGUI.InputText()],[simpleGUI.Button('Ok'), simpleGUI.Button('Cancel')]]
window = simpleGUI.Window('PyDa', layout)

engine = pyttsx3.init()

while True:
    event, values = window.read()
    if event in (None, 'Cancel'):
        break
    try:
        wiki_res = wikipedia.summary(values[0], sentences=2)
        wolfram_res = next(client.query(values[0]).results).text
        engine.say(wolfram_res)
        simpleGUI.PopupNonBlocking("Wolfram Result: "+wolfram_res,"Wikipedia Result: " + wiki_res)
    except wikipedia.exceptions.DisambiguationError:
        wolfram_res = next(client.query(values[0]).results).text
        engine.say(wolfram_res)
        simpleGUI.PopupNonBlocking(wolfram_res)
    except wikipedia.exceptions.PageError:
        wolfram_res = next(client.query(values[0]).results).text
        engine.say(wolfram_res)
        simpleGUI.PopupNonBlocking(wolfram_res)
    except:
        wiki_res = wikipedia.summary(values[0], sentences=2)
        engine.say(wiki_res)
        simpleGUI.PopupNonBlocking(wiki_res)

    engine.runAndWait()

    print (values[0])

window.close()
