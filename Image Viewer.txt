from tkinter import *
from tkinter import filedialog as fd
from tkinter import messagebox as ms
import PIL
from PIL import ImageTk, Image


class application:
    def __init__(self, master):
        self.master = master
        self.c_size = (554, 554)
        self.setup_gui(self.c_size)
        self.img = True

    def setup_gui(self, s):
        Label(self.master, text='Image Viewer', pady=5, bg='white', font=('', 22)).pack()
        self.canvas = Canvas(root, width=554, height=554,bd='10',relief='ridge')

        self.image=ImageTk.PhotoImage(Image.open("//home//riya//Pictures//Memory.jpg"))

        self.wt=self.canvas.create_image(30,30,anchor=NW,image=self.image)

        self.canvas.pack()

        f = Frame(self.master, bg='white', padx=10, pady=10)
        Button(f, text='Open New Image', bd=2, fg='white', bg='black', font=('', 15), command=self.make_image).pack(
            side=LEFT)
        f.pack()

        self.status = Label(self.master, text='Current Image: None', bg='gray', font=('', 15), relief='sunken', bd=2,
                            fg='black', anchor=W)
        self.status.pack(side=BOTTOM, fill=X)

    def make_image(self):
        try:
            File = fd.askopenfilename()
            self.pilImage = Image.open(File)
            re = self.pilImage.resize((700, 500), Image.ANTIALIAS)
            self.img = ImageTk.PhotoImage(re)
            self.canvas.delete(ALL)
            self.canvas.create_image(self.c_size[0] / 2 + 10, self.c_size[1] / 2 + 10, anchor=CENTER, image=self.img)
            self.status['text'] = 'Current Image:' + File
        except:
            ms.showerror('Error', 'File type is unsupported.')


root = Tk()
root.title('Image Viewer')
root.resizable(0, 0)

application(root)

root.mainloop()



