import tkinter as tk

def on_button_click(value):
    current_text = entry.get()
    if value == "C":
        entry.delete(0, tk.END)
    elif value == "=":
        try:
            result = str(eval(current_text))
            entry.delete(0, tk.END)
            entry.insert(tk.END, result)
        except:
            entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    else:
        entry.insert(tk.END, value)

root = tk.Tk()
root.title("Hesap Makinesi")

entry = tk.Entry(root, width=16, font=("Arial", 24), bd=8, insertwidth=4, justify="right")
entry.grid(row=0, column=0, columnspan=4)

buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    '0', 'C', '=', '+'
]

row = 1
col = 0

for button in buttons:
    tk.Button(root, text=button, padx=20, pady=20, font=("Arial", 18),
              command=lambda value=button: on_button_click(value)).grid(row=row, column=col)
    col += 1
    if col > 3:
        col = 0
        row += 1

root.mainloop()
