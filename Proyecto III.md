
**Proyecto III**

El Proyecto III de algoritmos es un programa de editor de texto desarrollado en Python con la biblioteca Tkinter. A continuación, se proporcionará un manual de usuario para el programa:

Manual de Usuario del Editor de Texto

1\. Abrir un Archivo

Para abrir un archivo de texto existente, selecciona "Archivo" en la barra de menú y elige "Abrir". Esto abrirá un cuadro de diálogo que te permite buscar y seleccionar el archivo que deseas abrir. Puedes abrir archivos con extensiones .txt, .py, .cpp, .cs y otros tipos que hayas configurado en el programa.















2\. Guardar un Archivo

Si deseas guardar el archivo actual, selecciona "Archivo" en la barra de menú y elige "Guardar". Si no has guardado previamente el archivo, se te pedirá que especifiques una ubicación y un nombre de archivo.













Si deseas guardar el archivo actual con un nombre diferente, selecciona "Archivo" y elige "Guardar Como...". Esto abrirá un cuadro de diálogo que te permitirá especificar una ubicación y un nombre de archivo nuevo.



























3\. Deshacer y Rehacer

El editor de texto admite las funciones de "Deshacer" y "Rehacer". Puedes deshacer cambios realizados en el texto seleccionando "Editar" en la barra de menú y eligiendo "Deshacer" o "Rehacer".













4\. Configuración de Fuente

Puedes cambiar la fuente y el tamaño de fuente en el editor de texto seleccionando "Configuración" en la barra de menú y eligiendo "Configuración". En la ventana de configuración, selecciona una fuente de la lista desplegable "Fuente" y un tamaño de fuente de la lista desplegable "Tamaño de fuente". Luego, haz clic en "Aplicar" para guardar los cambios.









5\. Ayuda

En la barra de menú, selecciona "Ayuda" para acceder a varias opciones:

"Acerca de" muestra información sobre la aplicación. 

"Integrantes" muestra información sobre los desarrolladores del programa.

6\. Cierre del Programa

Para cerrar el programa, simplemente cierra la ventana principal del editor de texto.







Abajo se encontrará el código fuente utilizado en Python:

import tkinter as tk

from tkinter import filedialog, messagebox, font, ttk

\# Función para abrir un archivo y cargar su contenido en el área de texto

def abrir\_archivo():

`    `ruta\_archivo = filedialog.askopenfilename(

`      `filetypes=[

`    `("Todos los archivos", "\*.\*"),

`    `("Archivos de texto", "\*.txt"),

`    `("Archivos Python", "\*.py"),

`    `("Archivos C++", "\*.cpp"),

`    `("Archivos C#", "\*.cs"),

`    `# Añadir más tipos de archivo según sea necesario

]

`    `)

`    `if not ruta\_archivo:

`        `return

`    `txt\_edit.delete(1.0, tk.END)

`    `with open(ruta\_archivo, "r", encoding="utf-8") as archivo\_entrada:

`        `texto = archivo\_entrada.read()

`        `txt\_edit.insert(tk.END, texto)

`    `ventana.title(f"Editor de Texto - {ruta\_archivo}")

`    `archivo\_actual.set(ruta\_archivo)

\# Función para guardar el contenido actual del área de texto en el archivo actual

def guardar\_archivo():

`    `if not archivo\_actual.get():

`        `guardar\_como\_archivo()

`    `else:

`        `with open(archivo\_actual.get(), "w", encoding="utf-8") as archivo\_salida:

`            `texto = txt\_edit.get(1.0, tk.END)

`            `archivo\_salida.write(texto)

`        `messagebox.showinfo("Éxito", "Archivo guardado con éxito")

\# Función para guardar el contenido actual del área de texto en un nuevo archivo

def guardar\_como\_archivo():

`    `ruta\_archivo = filedialog.asksaveasfilename(

`        `defaultextension="txt",

`        `filetypes=[("Archivos de texto", "\*.txt"), ("Todos los archivos", "\*.\*")]

`    `)

`    `if not ruta\_archivo:

`        `return

`    `with open(ruta\_archivo, "w", encoding="utf-8") as archivo\_salida:

`        `texto = txt\_edit.get(1.0, tk.END)

`        `archivo\_salida.write(texto)

`    `ventana.title(f"Editor de Texto - {ruta\_archivo}")

`    `archivo\_actual.set(ruta\_archivo)

`    `messagebox.showinfo("Éxito", "Archivo guardado como nuevo archivo")

\# Función para mostrar información sobre la aplicación

def mostrar\_informacion():

`    `messagebox.showinfo("Acerca de", "Editor para formatos(.txt, .cpp, .cs, .py)\n\nProyecto Final\nV1.0")

\# Función para mostrar el manual de usuario

import webbrowser

def mostrar\_manual():

`    `url\_manual = "https://www.ejemplo.com/manual"  # la URL real del manual C': 

`    `webbrowser.open(url\_manual)

\# Función para mostrar información de los integrantes

def mostrar\_integrantes():

`    `messagebox.showinfo("Integrantes", "Nombre: Dalila Nineth Zacarías de León\nCarné: 7690-22-18678")

\# Función para abrir la ventana de configuración

def abrir\_ventana\_configuracion():

`    `configuracion = tk.Toplevel(ventana)

`    `configuracion.title("Configuración")

`    `label\_fuente = tk.Label(configuracion, text="Fuente:")

`    `label\_fuente.grid(row=0, column=0, padx=10, pady=10)

`    `var\_fuente = tk.StringVar(configuracion)

`    `combo\_fuente = ttk.Combobox(configuracion, textvariable=var\_fuente, values=sorted(list(font.families())), state="readonly")

`    `combo\_fuente.grid(row=0, column=1, padx=10, pady=10)

`    `combo\_fuente.set("Arial")  # Default value

`    `label\_tamano = tk.Label(configuracion, text="Tamaño de fuente:")

`    `label\_tamano.grid(row=1, column=0, padx=10, pady=10)

`    `var\_tamano = tk.IntVar(configuracion)

`    `combo\_tamano = ttk.Combobox(configuracion, textvariable=var\_tamano, values=list(range(8, 33, 2)), state="readonly")

`    `combo\_tamano.grid(row=1, column=1, padx=10, pady=10)

`    `combo\_tamano.set(12)  # Default value

`    `def aplicar\_configuracion():

`        `txt\_edit.config(font=(var\_fuente.get(), var\_tamano.get()))

`    `boton\_aplicar = tk.Button(configuracion, text="Aplicar", command=aplicar\_configuracion)

`    `boton\_aplicar.grid(row=2, column=0, columnspan=2, pady=10)

ventana = tk.Tk()

ventana.title("Editor de Texto")

archivo\_actual = tk.StringVar(value="")

txt\_edit = tk.Text(ventana, undo=True)

txt\_edit.grid(row=0, column=0, sticky="nsew")

menu\_bar = tk.Menu(ventana)

ventana.config(menu=menu\_bar)

file\_menu = tk.Menu(menu\_bar, tearoff=0)

file\_menu.add\_command(label="Abrir", command=abrir\_archivo)

file\_menu.add\_command(label="Guardar", command=guardar\_archivo)

file\_menu.add\_command(label="Guardar Como...", command=guardar\_como\_archivo)

menu\_bar.add\_cascade(label="Archivo", menu=file\_menu)

edit\_menu = tk.Menu(menu\_bar, tearoff=0)

edit\_menu.add\_command(label="Deshacer", command=lambda: txt\_edit.edit\_undo())

edit\_menu.add\_command(label="Rehacer", command=lambda: txt\_edit.edit\_redo())

menu\_bar.add\_cascade(label="Editar", menu=edit\_menu)

config\_menu = tk.Menu(menu\_bar, tearoff=0)

config\_menu.add\_command(label="Configuración", command=abrir\_ventana\_configuracion)

menu\_bar.add\_cascade(label="Configuración", menu=config\_menu)

help\_menu = tk.Menu(menu\_bar, tearoff=0)

help\_menu.add\_command(label="Acerca de", command=mostrar\_informacion)

help\_menu.add\_command(label="Manual", command=mostrar\_manual)

help\_menu.add\_command(label="Integrantes", command=mostrar\_integrantes)

menu\_bar.add\_cascade(label="Ayuda", menu=help\_menu)

ventana.grid\_rowconfigure(0, weight=1)

ventana.grid\_columnconfigure(0, weight=1)

ventana.mainloop()





