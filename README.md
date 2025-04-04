# 5.1 Форма авторизации
import tkinter as tk
from tkinter import ttk

def run_login_form():
    root = tk.Tk()
    root.geometry("200x300")
    root.title("Форма авторизации")

    tk.Label(root, text="Логин").pack(pady=5)
    login_entry = tk.Entry(root)
    login_entry.pack()

    tk.Label(root, text="Пароль").pack(pady=5)
    password_entry = tk.Entry(root, show="*")
    password_entry.pack()

    remember_var = tk.BooleanVar()
    remember_cb = tk.Checkbutton(root, text="Запомнить пароль", variable=remember_var)
    remember_cb.pack(pady=10)

    tk.Button(root, text="Авторизоваться").pack(pady=10)

    root.mainloop()

# 5.2 Форма регистрации
def run_register_form():
    root = tk.Tk()
    root.title("Форма регистрации")
    root.configure(bg="#e0f7fa")

    tk.Label(root, text="Логин", bg="#e0f7fa").pack(pady=5)
    tk.Entry(root).pack()

    tk.Label(root, text="Пароль", bg="#e0f7fa").pack(pady=5)
    tk.Entry(root, show="*").pack()

    tk.Label(root, text="О себе", bg="#e0f7fa").pack(pady=5)
    tk.Text(root, height=3, width=30).pack()

    tk.Label(root, text="Пол", bg="#e0f7fa").pack(pady=5)
    gender_var = tk.StringVar()
    tk.Radiobutton(root, text="Мужской", variable=gender_var, value="М", bg="#e0f7fa").pack()
    tk.Radiobutton(root, text="Женский", variable=gender_var, value="Ж", bg="#e0f7fa").pack()

    tk.Label(root, text="Материк", bg="#e0f7fa").pack(pady=5)
    continent_cb = ttk.Combobox(root, values=["Евразия", "Африка", "Северная Америка", "Южная Америка", "Австралия"])
    continent_cb.pack()

    tk.Button(root, text="Зарегистрироваться", bg="#a7ffeb").pack(pady=10)

    root.mainloop()

# 5.3 Ассоциированные переменные
def run_binding_widgets():
    root = tk.Tk()
    root.title("Ассоциированные переменные")

    str_var = tk.StringVar()
    int_var = tk.IntVar()
    bool_var = tk.BooleanVar()

    tk.Entry(root, textvariable=str_var).pack()
    tk.Checkbutton(root, text="Флажок", variable=bool_var).pack()
    tk.Radiobutton(root, text="Радио 1", variable=int_var, value=1).pack()
    tk.Radiobutton(root, text="Радио 2", variable=int_var, value=2).pack()

    result_label = tk.Label(root, text="")
    result_label.pack(pady=10)

    def update_label():
        result_label.config(text=f"{str_var.get()}, {bool_var.get()}, {int_var.get()}")

    tk.Button(root, text="Показать значения", command=update_label).pack()

    root.mainloop()

# 5.4 Меню с цветом и размером
def run_menu_app():
    root = tk.Tk()
    root.geometry("400x300")
    root.title("Меню")

    def change_color(color):
        root.configure(bg=color)

    def change_size(size):
        root.geometry(size)

    menu = tk.Menu(root)
    root.config(menu=menu)

    color_menu = tk.Menu(menu, tearoff=0)
    menu.add_cascade(label="Color", menu=color_menu)
    color_menu.add_command(label="Red", command=lambda: change_color("red"), accelerator="Ctrl+R")
    color_menu.add_command(label="Green", command=lambda: change_color("green"), accelerator="Ctrl+G")
    color_menu.add_command(label="Blue", command=lambda: change_color("blue"), accelerator="Ctrl+B")

    size_menu = tk.Menu(menu, tearoff=0)
    menu.add_cascade(label="Size", menu=size_menu)
    size_menu.add_command(label="500x500", command=lambda: change_size("500x500"), accelerator="Ctrl+1")
    size_menu.add_command(label="700x400", command=lambda: change_size("700x400"), accelerator="Ctrl+2")

    root.bind_all("<Control-r>", lambda e: change_color("red"))
    root.bind_all("<Control-g>", lambda e: change_color("green"))
    root.bind_all("<Control-b>", lambda e: change_color("blue"))
    root.bind_all("<Control-1>", lambda e: change_size("500x500"))
    root.bind_all("<Control-2>", lambda e: change_size("700x400"))

    root.mainloop()

# run_login_form()
# run_register_form()
# run_binding_widgets()
# run_menu_app()
