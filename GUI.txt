import sys
import os
import tkinter as tk
from tkinter import filedialog
from tkinter import *
from PIL import  ImageTk,Image,ImageSequence
import cv2
import glob
import PIL.Image,PIL.ImageTk


def openDirectory():
    os.system('python ImageViewer.py')
def start_capture():
    os.system('python Gesture.py')

def start1_capture():
    os.system('python Drawing.py')






#Create Window object
app=Tk()
canvas=Canvas(app,width=640,height=480)
image=ImageTk.PhotoImage(Image.open("//home//riya//Pictures//images.jpg"))
canvas.create_image(0,0,anchor=NW,image=image)


start_btn=Button(app,text='Capture Image',bg='white',fg='black',width=12,command=start_capture)
start_btn_window=canvas.create_window(80,240,anchor=NW,window=start_btn)

start1_btn=Button(app,text='Drawing ',bg='white',fg='black',width=12,command=start1_capture)
start1_btn_window=canvas.create_window(246,240,anchor=NW,window=start1_btn)

open1_btn=Button(app,text='Photo Studio',bg='white',fg='black',width=12,command=openDirectory)
open1_btn_window=canvas.create_window(412,240,anchor=NW,window=open1_btn)

app.title('Sixth Sense')
canvas.pack()

app.mainloop()



