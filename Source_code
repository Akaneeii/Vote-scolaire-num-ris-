import tkinter as tk
from tkinter import ttk
import winsound
import time
import datetime
import atexit


window = tk.Tk()
window.title("Logiciel de vote d'IND")
window.geometry("1080x700")

label_text = "Développé par la TS1 et Safietou Diop."
label = ttk.Label(window, text=label_text, font=('Times', 14, 'normal', 'italic'), foreground="black")
label.grid(row=3, column=1)



window.attributes('-fullscreen', True)
window.attributes('-topmost', True)
window.bind('<Control-Alt-KeyPress-a>', lambda event: window.quit())

results_visible = False




def terminer(event):
    output_var.set(f"Mouhamed: {var2.get()},"
                   f" Larissa: {var3.get()},"
                   f" Kenza: {var1.get()},"
                   f" Ndieme: {var4.get()},"
                   f" Awa: {var5.get()},"
                   f" Vote Blanc: {vote_blanc.get()}")
    
def toggle_results(event):
    global results_visible
    results_visible = not results_visible
    output_var.set("") if not results_visible else None

def btn_func(var):
    v = var.get()
    var.set(v+1)
    winsound.Beep(700,500)
    kbutton["state"] = "disabled"
    mbutton["state"] = "disabled"
    lbutton["state"] = "disabled"
    nbutton["state"] = "disabled"
    abutton["state"] = "disabled"
    vbutton["state"] = "disabled"

def enable(event):
    kbutton["state"] = "enable"
    mbutton["state"] = "enable"
    lbutton["state"] = "enable"
    nbutton["state"] = "enable"
    abutton["state"] = "enable"
    vbutton["state"] = "enable"

def winner(event):
    votes = {
        "Kenza": var1.get(),
        "Mouhamed": var2.get(),
        "Larissa": var3.get(),
        "Ndieme": var4.get(),
        "Awa": var5.get(),
        "Vote Blanc": vote_blanc.get()
    }
    gagnant = max(votes, key=votes.get)
    print(f"Le président élu est : {gagnant} avec {votes[gagnant]} voix.")



ksimg = tk.PhotoImage(file='image/kenza_bann.png') 
mgimg = tk.PhotoImage(file='image/mg_bann.png')
lsimg = tk.PhotoImage(file='image/larissa_bann.png')
nmimg = tk.PhotoImage(file='image/ndieme_bann.png')
acimg = tk.PhotoImage(file='image/Awa.png')
vimg = tk.PhotoImage(file='image/vote blanc.png')


btn_frame = ttk.Frame(window)
output_frame = ttk.Frame(window)


vote_blanc = tk.IntVar()
var1 = tk.IntVar()
var2 = tk.IntVar()
var3 = tk.IntVar()
var4 = tk.IntVar()
var5 = tk.IntVar()
output_var = tk.StringVar()


kbutton = ttk.Button(btn_frame,
                     text="KENZA",
                     takefocus=False,
                     image=ksimg,
                     command=lambda: btn_func(var1))
mbutton = ttk.Button(btn_frame,
                     text="Mouhamed",
                     takefocus=False,
                     image=mgimg,
                     command=lambda: btn_func(var2))
lbutton = ttk.Button(btn_frame,
                     text="Larissa",
                     takefocus=False,
                     image=lsimg,
                     command=lambda: btn_func(var3))
nbutton = ttk.Button(btn_frame, text="Ndieme",
                     takefocus=False,
                     image=nmimg,
                     command=lambda: btn_func(var4))

abutton = ttk.Button(btn_frame, text="Awa",
                     takefocus=False,
                     image=acimg,
                     command=lambda: btn_func(var5))

vbutton = ttk.Button(btn_frame, text="Vote Blanc",
                     takefocus=False,
                     image=vimg,
                     command=lambda: btn_func(vote_blanc))


window.bind("<Control-Alt-KeyPress-i>", terminer)
window.bind("<Alt-KeyPress-e>", enable)
window.bind("<Alt-KeyPress-s>", winner)
window.bind("<Control-Alt-space>", toggle_results)
#window.bind("<Alt-KeyPress-s>", nul)

timestamp = datetime.datetime.now().strftime('%Y%m%d%H%M%S')
filename = f'output_{timestamp}.txt'
def create_text_file():
    try:
        with open(filename, 'w') as file:
            file.write(f'Kenza = {var1.get()}\n')
            file.write(f'Mouhamed = {var2.get()}\n')
            file.write(f'Larissa = {var3.get()}\n')
            file.write(f'Ndieme = {var4.get()}\n')
            file.write(f'Awa = {var5.get()}\n')
            file.write(f'Vote Blanc = {vote_blanc.get()}\n')
    except Exception as e:
        print(f"Error writing to file: {e}")

atexit.register(create_text_file)

def on_close():
    pass 

window.protocol("WM_DELETE_WINDOW", on_close)


output1 = ttk.Label(output_frame, text=0, textvariable=var1)
output2 = ttk.Label(output_frame, text=0, textvariable=var2)
output3 = ttk.Label(output_frame, text=0, textvariable=var3)
output4 = ttk.Label(output_frame, text=0, textvariable=var4)
output5 = ttk.Label(output_frame, text=0, textvariable=var5)

output = ttk.Label(output_frame, text="Resultat:", textvariable=output_var, font="Arial 20 bold")
voteblanc_label = ttk.Label(output_frame, textvariable=vote_blanc)



window.columnconfigure(0, weight=1)
window.columnconfigure(1, weight=1)
window.columnconfigure(2, weight=1)
window.rowconfigure(0, weight=1)
window.rowconfigure(1, weight=1)
window.rowconfigure(2, weight=1)


btn_frame.grid(row=0, column=0, columnspan=3, rowspan=3)
output_frame.grid(row=0, column=0, columnspan=3)

kbutton.grid(row=0, column=0)
lbutton.grid(row=0, column=2)
vbutton.grid(row=0, column=1)
mbutton.grid(row=2, column=0)
nbutton.grid(row=2, column=1)
abutton.grid(row=2, column=2)


output.grid(row=0, column=3)


window.mainloop()
