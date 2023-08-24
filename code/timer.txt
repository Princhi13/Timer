import keyboard
import time
import os
import pyaudio
import wave
import sys
import pyperclip
import colorama
from colorama import Fore, Back, Style
colorama.init()

def audio():
    CHUNK = 1024
    wf = wave.open("audio.wav", 'rb')
    p = pyaudio.PyAudio()
    stream = p.open(format=p.get_format_from_width(wf.getsampwidth()),
                    channels=wf.getnchannels(),
                    rate=wf.getframerate(),
                    output=True)
    data = wf.readframes(CHUNK)
    while data != '':
        stream.write(data)
        data = wf.readframes(CHUNK)
    stream.stop_stream()
    stream.close()

print('Часы')
hour = input()
hour = int(hour)
print('Минуты')
min = input()
min = int(min)
print('Секунды')
sec = input()
sec = int(sec)

hour = str(hour)
min = str(min)
sec = str(sec)

os.system('cls')

print('ТАЙМЕР ВКЛЮЧЕН')

hour = int(hour)
min = int(min)
sec = int(sec)

hour = hour * 60 * 60
min = min * 60

totaltime = hour + min + sec

time.sleep(totaltime)
os.system('cls')
print('ТАЙМЕР ВЫКЛЮЧЕН')
audio()