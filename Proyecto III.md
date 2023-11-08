
 # Proyecto III 
 # Editor de Texto en Python con interfaz grafica 
 
El Proyecto III de algoritmos es un programa de editor de texto desarrollado en Python con la biblioteca Tkinter. 
A continuación, se proporcionará un manual de usuario para el programa:

**Manual de Usuario del Editor de Texto**

- **Abrir un Archivo**:

Para abrir un archivo de texto existente, selecciona "Archivo" en la barra de menú y elige "Abrir". 
Esto abrirá un cuadro de diálogo que te permite buscar y seleccionar el archivo que deseas abrir. 
Puedes abrir archivos con extensiones .txt, .py, .cpp, .cs y otros tipos que hayas configurado en el programa.

[![captura.png](https://i.postimg.cc/Dy2Tq3Tt/captura.png)](https://postimg.cc/Btwk0ytg)


- **Guardar un Archivo**:

Si deseas guardar el archivo actual, selecciona "Archivo" en la barra de menú y elige "Guardar". 
Si no has guardado previamente el archivo, se te pedirá que especifiques una ubicación y un nombre de archivo.
Si deseas guardar el archivo actual con un nombre diferente, selecciona "Archivo" y elige "Guardar Como...". Esto abrirá un cuadro de diálogo que te permitirá especificar una ubicación y un nombre de archivo nuevo.

[![guardar-como.png](https://i.postimg.cc/NjqRNDNq/guardar-como.png)](https://postimg.cc/kBsVGQ3f)

[![image.png](https://i.postimg.cc/9F8Q0Q7x/image.png)](https://postimg.cc/WhZvfjSr)

[![image.png](https://i.postimg.cc/sx0Cj1N7/image.png)](https://postimg.cc/CnDQJMYx)

[![guardado.png](https://i.postimg.cc/s2PmPqyN/guardado.png)](https://postimg.cc/JynjMTsN)

- **Deshacer y Rehacer**:

El editor de texto admite las funciones de "Deshacer" y "Rehacer". Puedes deshacer cambios realizados en el texto seleccionando "Editar" en la barra de menú y eligiendo "Deshacer" o "Rehacer".

[![image.png](https://i.postimg.cc/s2zqRpgb/image.png)](https://postimg.cc/18WJGV6K)

- **Configuración de Fuente**:

Puedes cambiar la fuente y el tamaño de fuente en el editor de texto seleccionando "Configuración" en la barra de menú y eligiendo "Configuración". En la ventana de configuración, selecciona una fuente de la lista desplegable "Fuente" y un tamaño de fuente de la lista desplegable "Tamaño de fuente". Luego, haz clic en "Aplicar" para guardar los cambios.

[![image.png](https://i.postimg.cc/WbJHF9DQ/image.png)](https://postimg.cc/tYp58NN5)

[![image.png](https://i.postimg.cc/BnT7NXBp/image.png)](https://postimg.cc/SnKGxQ5Y)

- **Ayuda**:

En la barra de menú, selecciona "Ayuda" para acceder a varias opciones:
-"Acerca de" muestra información sobre la aplicación. 

[![image.png](https://i.postimg.cc/K4XQD2KC/image.png)](https://postimg.cc/T59rTBJc)

-""Manual" te llevará a un enlace externo a un manual de usuario
[![image.png](https://i.postimg.cc/BnmYRRRP/image.png)](https://postimg.cc/XrykC1jn)

[![image.png](https://i.postimg.cc/8kwZ72PK/image.png)](https://postimg.cc/Sj265t9C)

-"Integrantes" muestra información sobre los desarrolladores del programa.

[![image.png](https://i.postimg.cc/wxWkqD0n/image.png)](https://postimg.cc/V5Ct40yF)

- **Cierre del Programa**:
Para cerrar el programa, simplemente cierra la ventana principal del editor de texto.

[![image.png](https://i.postimg.cc/Y0jYGybZ/image.png)](https://postimg.cc/1VhfbMxr)

# Codigo Fuente Python

```
import tkinter as tk
from tkinter import filedialog, messagebox, font, ttk

# Función para abrir un archivo y cargar su contenido en el área de texto
def abrir_archivo():
    ruta_archivo = filedialog.askopenfilename(
      filetypes=[
    ("Todos los archivos", "*.*"),
    ("Archivos de texto", "*.txt"),
    ("Archivos Python", "*.py"),
    ("Archivos C++", "*.cpp"),
    ("Archivos C#", "*.cs"),
    # Añadir más tipos de archivo según sea necesario
]

    )
    if not ruta_archivo:
        return
    txt_edit.delete(1.0, tk.END)
    with open(ruta_archivo, "r", encoding="utf-8") as archivo_entrada:
        texto = archivo_entrada.read()
        txt_edit.insert(tk.END, texto)
    ventana.title(f"Editor de Texto - {ruta_archivo}")
    archivo_actual.set(ruta_archivo)

# Función para guardar el contenido actual del área de texto en el archivo actual
def guardar_archivo():
    if not archivo_actual.get():
        guardar_como_archivo()
    else:
        with open(archivo_actual.get(), "w", encoding="utf-8") as archivo_salida:
            texto = txt_edit.get(1.0, tk.END)
            archivo_salida.write(texto)
        messagebox.showinfo("Éxito", "Archivo guardado con éxito")

# Función para guardar el contenido actual del área de texto en un nuevo archivo
def guardar_como_archivo():
    ruta_archivo = filedialog.asksaveasfilename(
        defaultextension="txt",
        filetypes=[("Archivos de texto", "*.txt"), ("Todos los archivos", "*.*")]
    )
    if not ruta_archivo:
        return
    with open(ruta_archivo, "w", encoding="utf-8") as archivo_salida:
        texto = txt_edit.get(1.0, tk.END)
        archivo_salida.write(texto)
    ventana.title(f"Editor de Texto - {ruta_archivo}")
    archivo_actual.set(ruta_archivo)
    messagebox.showinfo("Éxito", "Archivo guardado como nuevo archivo")

# Función para mostrar información sobre la aplicación
def mostrar_informacion():
    messagebox.showinfo("Acerca de", "Editor para formatos(.txt, .cpp, .cs, .py)\n\nProyecto Final\nV1.0")

# Función para mostrar el manual de usuario
import webbrowser

def mostrar_manual():
    url_manual = "https://drive.google.com/file/d/18KOgA6PgcqaaKF21UKW0Ro64X-zyhIVZ/view?usp=sharing"  # la URL real del manual C': 
    webbrowser.open(url_manual)

# Función para mostrar información de los integrantes
def mostrar_integrantes():
    messagebox.showinfo("Integrantes", "Nombre: Dalila Nineth Zacarías de León\nCarné: 7690-22-18678")

# Función para abrir la ventana de configuración
def abrir_ventana_configuracion():
    configuracion = tk.Toplevel(ventana)
    configuracion.title("Configuración")

    label_fuente = tk.Label(configuracion, text="Fuente:")
    label_fuente.grid(row=0, column=0, padx=10, pady=10)

    var_fuente = tk.StringVar(configuracion)
    combo_fuente = ttk.Combobox(configuracion, textvariable=var_fuente, values=sorted(list(font.families())), state="readonly")
    combo_fuente.grid(row=0, column=1, padx=10, pady=10)
    combo_fuente.set("Arial")  # Default value

    label_tamano = tk.Label(configuracion, text="Tamaño de fuente:")
    label_tamano.grid(row=1, column=0, padx=10, pady=10)

    var_tamano = tk.IntVar(configuracion)
    combo_tamano = ttk.Combobox(configuracion, textvariable=var_tamano, values=list(range(8, 33, 2)), state="readonly")
    combo_tamano.grid(row=1, column=1, padx=10, pady=10)
    combo_tamano.set(12)  # Default value

    def aplicar_configuracion():
        txt_edit.config(font=(var_fuente.get(), var_tamano.get()))

    boton_aplicar = tk.Button(configuracion, text="Aplicar", command=aplicar_configuracion)
    boton_aplicar.grid(row=2, column=0, columnspan=2, pady=10)

ventana = tk.Tk()
ventana.title("Editor de Texto")

archivo_actual = tk.StringVar(value="")

txt_edit = tk.Text(ventana, undo=True)
txt_edit.grid(row=0, column=0, sticky="nsew")

menu_bar = tk.Menu(ventana)
ventana.config(menu=menu_bar)

file_menu = tk.Menu(menu_bar, tearoff=0)
file_menu.add_command(label="Abrir", command=abrir_archivo)
file_menu.add_command(label="Guardar", command=guardar_archivo)
file_menu.add_command(label="Guardar Como...", command=guardar_como_archivo)
menu_bar.add_cascade(label="Archivo", menu=file_menu)

edit_menu = tk.Menu(menu_bar, tearoff=0)
edit_menu.add_command(label="Deshacer", command=lambda: txt_edit.edit_undo())
edit_menu.add_command(label="Rehacer", command=lambda: txt_edit.edit_redo())
menu_bar.add_cascade(label="Editar", menu=edit_menu)

config_menu = tk.Menu(menu_bar, tearoff=0)
config_menu.add_command(label="Configuración", command=abrir_ventana_configuracion)
menu_bar.add_cascade(label="Configuración", menu=config_menu)

help_menu = tk.Menu(menu_bar, tearoff=0)
help_menu.add_command(label="Acerca de", command=mostrar_informacion)
help_menu.add_command(label="Manual", command=mostrar_manual)
help_menu.add_command(label="Integrantes", command=mostrar_integrantes)
menu_bar.add_cascade(label="Ayuda", menu=help_menu)

ventana.grid_rowconfigure(0, weight=1)
ventana.grid_columnconfigure(0, weight=1)

ventana.mainloop()

```

## Video ejecutando el codigo en Python,

[![Alt text](https://img.youtube.com/vi/zsNqAzm2Uxs/0.jpg)](https://youtu.be/zsNqAzm2Uxs)

Integrantes del Grupo: 
Dalila Nineth Zacarias de Leon --------- 100%




