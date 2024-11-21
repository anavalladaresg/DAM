# Python

##### 👤 Autor: Ana Valladares González
##### 📅  Fecha: 15 de octubre de 2021

---

### 📚 Índice
1. [Introducción](#id1)
2. [Variables](#id2)
3. [Estructuras de control](#id5)
4. [Funciones](#id6)
5. [Excepciones](#id8)
6. [Entrada y salida](#id9)
7.  [Programación orientada a objetos](#id12)
8.  [QT](#id13)
9.  [Funcionalidades de botones](#id14)
10. []

---

### 1. Introducción <a name="id1"></a>

Python es un lenguaje de programación interpretado cuya filosofía hace hincapié en una sintaxis que favorezca un código legible. Se trata de un lenguaje de programación multiparadigma, ya que soporta orientación a objetos, programación imperativa y, en menor medida, programación funcional. Es un lenguaje interpretado, dinámico y multiplataforma.

---

### 2. Variables <a name="id2"></a>

En Python no se necesita establecer el tipo de variable antes de asignarle un valor.

```python
x = 5
y = "Hello, World!"
```

---

### 3. Estructuras de control <a name="id5"></a>

#### 3.1. If

```python
a = 33
b = 200
if b > a:
  print("b es mayor que a")
```

#### 3.2. Elif

```python
a = 33
b = 33
if b > a:
  print("b es mayor que a")
elif a == b:
  print("a y b son iguales")
```

#### 3.3. Else

```python
a = 200
b = 33
if b > a:
  print("b es mayor que a")
elif a == b:
  print("a y b son iguales")
else:
  print("a es mayor que b")
```

---

### 4. Funciones <a name="id6"></a>

Una función es un bloque de código que solo se ejecuta cuando se llama.

```python
def funcion():
  print("Hello, World!")
```

```python
def funcion(nombre):
  print("Hello, " + nombre)
```

---

### 5. Excepciones <a name="id8"></a>

```python
try:
  print(x)
except NameError:
  print("Variable x is not defined")
except:
  print("Something else went wrong")
```

---

### 6. Entrada y salida <a name="id9"></a>

```python
print("Enter your name:")
x = input()
print("Hello, " + x)
```

---

### 7. Programación orientada a objetos <a name="id12"></a>

Utiliza objetos y clases para organizar la información de manera más eficiente. Se define una clase cuando se quiere crear un objeto.

> [!IMPORTANT]
`Self` es como `this` en java, solo que en Python es obligatorio y se pasa como primer argumento en todos los métodos de la clase, para que el objeto pueda acceder a los atributos y métodos de la clase.

```python
class Coche:
  def __init__(self, marca, modelo):
    self.marca = marca
    self.modelo = modelo

  def presentar(self):
    print("Hola, soy un " + self.marca + " " + self.modelo)
```

---

### 8. QT <a name="id13"></a>

QT es una biblioteca multiplataforma para el desarrollo de interfaces gráficas de usuario. 

#### 8.1. QWidget

```python
app = QApplication(sys.argv) # Crea una instancia de la aplicación

ventana = QWidget() # Crea una ventana
ventana.setWindowTitle('Hello World!') # Establece el título de la ventana
ventana.show() # Muestra la ventana

sys.exit(app.exec_()) # Cierra la aplicación
```

#### 8.2. QLabel

```python
etiqueta = QLabel('Hello World!', ventana) # Crea una etiqueta
etiqueta.move(50, 50) # Mueve la etiqueta a la posición (50, 50)
etiqueta.show() # Muestra la etiqueta
```

#### 8.3. QPushButton

```python
boton = QPushButton('Click me!', ventana) # Crea un botón
boton.move(50, 100) # Mueve el botón a la posición (50, 50)
boton.show() # Muestra el botón
```

#### 8.4. QLineEdit

```python
caja = QLineEdit(ventana) # Crea una caja de texto
caja.move(50, 150) # Mueve la caja de texto a la posición (50, 150)
caja.show() # Muestra la caja de texto
```

#### 8.5. QCheckBox

```python
casilla = QCheckBox('Check me!', ventana) # Crea una casilla de verificación
casilla.move(50, 200) # Mueve la casilla de verificación a la posición (50, 200)
casilla.show() # Muestra la casilla de verificación
```

#### 8.6. QRadioButton

```python
radio = QRadioButton('Select me!', ventana) # Crea un botón de radio
radio.move(50, 250) # Mueve el botón de radio a la posición (50, 250)
radio.show() # Muestra el botón de radio
```

#### 8.7. QComboBox

```python
combo = QComboBox(ventana) # Crea un cuadro combinado
combo.addItem('Option 1') # Añade una opción al cuadro combinado
combo.addItem('Option 2') # Añade otra opción al cuadro combinado
combo.move(50, 300) # Mueve el cuadro combinado a la posición (50, 300)
combo.show() # Muestra el cuadro combinado
```

#### 8.8. QSlider

```python
deslizador = QSlider(Qt.Horizontal, ventana) # Crea un deslizador horizontal
deslizador.move(50, 350) # Mueve el deslizador a la posición (50, 350)
deslizador.show() # Muestra el deslizador
```

#### 8.9. QProgressBar

[//]: # (Este es un comentario en Markdown)

```python
barra = QProgressBar(ventana) # Crea una barra de progreso
barra.move(50, 400) # Mueve la barra de progreso a la posición (50, 400)
barra.show() # Muestra la barra de progreso
```

#### 8.10. QSpinBox

```python
caja_numerica = QSpinBox(ventana) # Crea una caja numérica
caja_numerica.move(50, 450) # Mueve la caja numérica a la posición (50, 450)
caja_numerica.show() # Muestra la caja numérica
```

#### 8.11. QDateEdit

```python
fecha = QDateEdit(ventana) # Crea un editor de fechas
fecha.move(50, 500) # Mueve el editor de fechas a la posición (50, 500)
fecha.show() # Muestra el editor de fechas
```

#### 8.12. QTimeEdit

```python
hora = QTimeEdit(ventana) # Crea un editor de horas
hora.move(50, 550) # Mueve el editor de horas a la posición (50, 550)
hora.show() # Muestra el editor de horas
```

#### 8.13. QDateTimeEdit

```python
fecha_hora = QDateTimeEdit(ventana) # Crea un editor de fechas y horas
fecha_hora.move(50, 600) # Mueve el editor de fechas y horas a la posición (50, 600)
fecha_hora.show() # Muestra el editor de fechas y horas
```

#### 8.14. QPlainTextEdit

```python
texto = QPlainTextEdit(ventana) # Crea un editor de texto plano
texto.move(50, 650) # Mueve el editor de texto plano a la posición (50, 650)
texto.show() # Muestra el editor de texto plano
```

#### 8.15. QTextEdit (se pueden añadir imágenes, hipervínculos, etc.)

```python
texto_rico = QTextEdit(ventana) # Crea un editor de texto enriquecido
texto_rico.move(50, 700) # Mueve el editor de texto enriquecido a la posición (50, 700)
texto_rico.show() # Muestra el editor de texto enriquecido
```

#### 8.16. QTableWidget & QTableWidgetItem

```python
tabla = QTableWidget(ventana) # Crea una tabla
tabla.move(50, 750) # Mueve la tabla a la posición (50, 750)
tabla.setColumnCount(2) # Establece el número de columnas de la tabla
tabla.setRowCount(2) # Establece el número de filas de la tabla
tabla.setItem(0, 0, QTableWidgetItem('Hello')) # Añade un elemento a la tabla
tabla.setItem(0, 1, QTableWidgetItem('World')) # Añade otro elemento a la tabla
tabla.show() # Muestra la tabla
```
[//]: # (↓ ESTO NO SÉ COMO VA ↓) 

#### 8.17. QItemDataRole

```python
item = QTableWidgetItem('Hello') # Crea un elemento de la tabla
item.setData(Qt.ToolTipRole, 'This is a tooltip') # Establece un tooltip para el elemento
item.setData(Qt.DecorationRole, QIcon('icon.png')) # Establece un icono para el elemento
```

#### 8.18. QAbstractListModel

```python
class MyModel(QAbstractListModel):
  def __init__(self, data): # Constructor de la clase
    super().__init__() # Llama al constructor de la clase base
    self._data = data # Inicializa el atributo _data con el valor pasado como argumento

  def numFilas(self, parent): # Devuelve el número de filas de la lista
    return len(self._data) # Devuelve la longitud de la lista

  def data(self, index, role): # Devuelve los datos de la lista
    if role == Qt.DisplayRole: # Si el rol es DisplayRole
      return self._data[index.row()] # Devuelve el elemento de la lista en la posición index.row() [posición de la fila]
```

[//]: # (↑ ESTO NO SÉ COMO VA ↑) 

---

### 9. Funcionalidades de botones <a name="id14"></a>

#### 9.1. Click

```python
def on_click():
  print('Button clicked!')

boton.clicked.connect(on_click)

```

#### 9.2. Cambiar texto

```python
def on_click():
  boton.setText('Clicked!')

boton.clicked.connect(on_click)
```

#### 9.3. Cambiar color

```python
def on_click():
  boton.setStyleSheet('background-color: red')

boton.clicked.connect(on_click)
```

#### 9.4. Cambiar tamaño

```python
def on_click():
  boton.resize(100, 100)

boton.clicked.connect(on_click)
```

#### 9.5. Cambiar posición

```python
def on_click():
  boton.move(100, 100)

boton.clicked.connect(on_click)
```

#### 9.6. Ocultar

```python
def on_click():
  boton.hide()

boton.clicked.connect(on_click)
```

#### 9.7. Mostrar

```python
def on_click():
  boton.show()

boton.clicked.connect(on_click)

```

#### 9.8. Deshabilitar

```python
def on_click():
  boton.setEnabled(False)

boton.clicked.connect(on_click)
```

#### 9.9. Habilitar

```python
def on_click():
  boton.setEnabled(True)

boton.clicked.connect(on_click)
```

#### 9.10. Cerrar ventana

```python
def on_click():
  ventana.close()

boton.clicked.connect(on_click)
```

