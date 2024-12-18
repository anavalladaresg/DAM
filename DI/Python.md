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

#### 2.1. Tuplas

Una tupla es una colección ordenada e inmutable de elementos.

```python
tupla = ("manzana", "plátano", "cereza")
```

Metodos de las tuplas:

```python
tupla.count("manzana") # Devuelve el número de veces que aparece "manzana" en la tupla
tupla.index("plátano") # Devuelve la posición de "plátano" en la tupla
tupla.append("naranja") # Añade "naranja" al final de la tupla
tupla.remove("cereza") # Elimina "cereza" de la tupla
tupla.pop() # Elimina el último elemento de la tupla
tupla.clear() # Elimina todos los elementos de la tupla
tupla = tuple(("manzana", "plátano", "cereza")) # Crea una tupla
tupla = tuple.sorted(tupla) # Ordena la tupla
```


---

### 3. Estructuras de control <a name="id5"></a>

#### 3.1. If

Ejecuta un bloque de código si una condición es verdadera.

```python
a = 33
b = 200
if b > a:
  print("b es mayor que a")
```

#### 3.2. Elif

Ejecuta un bloque de código si la primera condición es verdadera, y si no lo es, prueba la siguiente condición.

```python
a = 33
b = 33
if b > a:
  print("b es mayor que a")
elif a == b:
  print("a y b son iguales")
```

#### 3.3. Else

Ejecuta un bloque de código si ninguna de las condiciones anteriores es verdadera.

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

#### 3.4. For

Itera sobre una secuencia de elementos.

```python
frutas = ["manzana", "plátano", "cereza"]
for x in frutas:
  print(x)
```

#### 3.5. While

Ejecuta un bloque de código mientras una condición sea verdadera.

```python
i = 1

while i < 6:
  print(i)
  i += 1
```

#### 3.6. Break

Detiene la ejecución del bucle aunque la condición sea verdadera.

```python
i = 1

while i < 6:
  print(i)
  if i == 3:
    break
  i += 1
```

#### 3.7. Continue

Detiene la iteración actual y continúa con la siguiente.

```python
i = 0

while i < 6:
  i += 1
  if i == 3:
    continue
  print(i)
```

#### 3.8. Range

Genera una secuencia de números.

```python
for x in range(6):
  print(x)
```

---

### 4. Funciones <a name="id6"></a>

Una función es un bloque de código que solo se ejecuta cuando se llama.

> [!NOTE]
Para que salga todo lo que queremos en la ventana, lo ultimo que debemos poner es `ventana.show()`, si no, estaría ejecutando la ventana antes de añadirle los elementos.

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

Crea una ventana con un título.

```python
app = QApplication(sys.argv) # Crea una instancia de la aplicación

ventana = QWidget() # Crea una ventana
ventana.setWindowTitle('Hello World!') # Establece el título de la ventana
ventana.show() # Muestra la ventana

sys.exit(app.exec_()) # Cierra la aplicación
```

#### 8.2. QLabel

Crea una etiqueta con un texto.

```python
etiqueta = QLabel('Hello World!', ventana) # Crea una etiqueta
etiqueta.setStyleSheet('font-size: 30px; font-weight: bold;')
etiqueta.move(50, 50) # Mueve la etiqueta a la posición (50, 50)
# etiqueta.setAlignment(Qt.AlignCenter) # Centra el texto de la etiqueta
etiqueta.show() # Muestra la etiqueta
```

#### 8.3. QPushButton

Crea un botón con un texto.

```python
boton = QPushButton('Click me!', ventana) # Crea un botón
boton.move(50, 100) # Mueve el botón a la posición (50, 50)
boton.show() # Muestra el botón
```

#### 8.4. QLineEdit

Crea una caja de texto.

```python
caja = QLineEdit(ventana) # Crea una caja de texto
caja.move(50, 150) # Mueve la caja de texto a la posición (50, 150)
caja.show() # Muestra la caja de texto
```

#### 8.5. QCheckBox

Crea una casilla de verificación.

```python
casilla = QCheckBox('Check me!', ventana) # Crea una casilla de verificación
casilla.move(50, 200) # Mueve la casilla de verificación a la posición (50, 200)
casilla.show() # Muestra la casilla de verificación
```

#### 8.6. QRadioButton

Crea un botón de radio.

```python
radio = QRadioButton('Select me!', ventana) # Crea un botón de radio
radio.move(50, 250) # Mueve el botón de radio a la posición (50, 250)
radio.show() # Muestra el botón de radio
```

#### 8.7. QComboBox

Crea un cuadro combinado.

```python
combo = QComboBox(ventana) # Crea un cuadro combinado
combo.addItem('Option 1') # Añade una opción al cuadro combinado
combo.addItem('Option 2') # Añade otra opción al cuadro combinado
combo.move(50, 300) # Mueve el cuadro combinado a la posición (50, 300)
combo.show() # Muestra el cuadro combinado
```

#### 8.8. QSlider

Crea un deslizador.

```python
deslizador = QSlider(Qt.Horizontal, ventana) # Crea un deslizador horizontal
deslizador.move(50, 350) # Mueve el deslizador a la posición (50, 350)
deslizador.show() # Muestra el deslizador
```

#### 8.9. QProgressBar

Crea una barra de progreso.

```python
barra = QProgressBar(ventana) # Crea una barra de progreso
barra.move(50, 400) # Mueve la barra de progreso a la posición (50, 400)
barra.show() # Muestra la barra de progreso
```

#### 8.10. QSpinBox

Crea una caja numérica.

```python
caja_numerica = QSpinBox(ventana) # Crea una caja numérica
caja_numerica.move(50, 450) # Mueve la caja numérica a la posición (50, 450)
caja_numerica.show() # Muestra la caja numérica
```

#### 8.11. QDateEdit

Crea un editor de fechas.

```python
fecha = QDateEdit(ventana) # Crea un editor de fechas
fecha.move(50, 500) # Mueve el editor de fechas a la posición (50, 500)
fecha.show() # Muestra el editor de fechas
```

#### 8.12. QTimeEdit

Crea un editor de horas.

```python
hora = QTimeEdit(ventana) # Crea un editor de horas
hora.move(50, 550) # Mueve el editor de horas a la posición (50, 550)
hora.show() # Muestra el editor de horas
```

#### 8.13. QDateTimeEdit

Crea un editor de fechas y horas.

```python
fecha_hora = QDateTimeEdit(ventana) # Crea un editor de fechas y horas
fecha_hora.move(50, 600) # Mueve el editor de fechas y horas a la posición (50, 600)
fecha_hora.show() # Muestra el editor de fechas y horas
```

#### 8.14. QPlainTextEdit

Crea un editor de texto plano.

```python
texto = QPlainTextEdit(ventana) # Crea un editor de texto plano
texto.move(50, 650) # Mueve el editor de texto plano a la posición (50, 650)
# texto.setEchoMode(QLineEdit.Password) # Oculta el texto de la contraseña (se muestra como asteriscos)
texto.show() # Muestra el editor de texto plano
```

#### 8.15. QTextEdit (se pueden añadir imágenes, hipervínculos, etc.)

Crea un editor de texto enriquecido.

```python
texto_rico = QTextEdit(ventana) # Crea un editor de texto enriquecido
texto_rico.move(50, 700) # Mueve el editor de texto enriquecido a la posición (50, 700)
texto_rico.show() # Muestra el editor de texto enriquecido
```

#### 8.16. QTableWidget & QTableWidgetItem

Crea una tabla con elementos.

```python
tabla = QTableWidget(ventana) # Crea una tabla
tabla.move(50, 750) # Mueve la tabla a la posición (50, 750)
tabla.setColumnCount(2) # Establece el número de columnas de la tabla
tabla.setRowCount(2) # Establece el número de filas de la tabla
tabla.setItem(0, 0, QTableWidgetItem('Hello')) # Añade un elemento a la tabla
tabla.setItem(0, 1, QTableWidgetItem('World')) # Añade otro elemento a la tabla
tabla.show() # Muestra la tabla
```

#### 8.17. QItemDataRole

Crea un elemento de la tabla con un tooltip (información adicional) y un icono.

```python
item = QTableWidgetItem('Hello') # Crea un elemento de la tabla
item.setData(Qt.ToolTipRole, 'This is a tooltip') # Establece un tooltip para el elemento
item.setData(Qt.DecorationRole, QIcon('icon.png')) # Establece un icono para el elemento
```

#### 8.18. QAbstractListModel

Crea un modelo de lista.

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

#### 8.19. QGroupBox

Crea un grupo de elementos.

```python
login_frame = QGroupBox("Login") # Crea un grupo de elementos
login_frame.setStyleSheet('font-size: 10px; font-weight: bold;') # Establece el estilo del grupo de elementos
login_layout = QVBoxLayout() # Crea un diseño vertical
login_frame.setLayout(login_layout) # Establece el diseño del grupo de elementos
```

#### 8.20. QGridLayout

Crea un diseño de cuadrícula.

```python
layout = QGridLayout() # Crea un diseño de cuadrícula

layout.addWidget(<item1>, 0, 0) # Añade un botón en la posición (0, 0)
layout.addWidget(<item2>, 0, 1) # Añade otro botón en la posición (0, 1)
layout.addWidget(<item3>, 1, 0) # Añade otro botón en la posición (1, 0)

ventana.setLayout(layout) # Establece el diseño de la ventana
```

---

### 9. Funcionalidades de botones <a name="id14"></a>

```python
ventana = QWidget() # Crea una ventana
ventana.setWindowTitle('Hello World!') # Establece el título de la ventana
boton = QPushButton('Click me!', ventana) # Crea un botón, ventana es la ventana en la que se mostrará el botón
ventana.show() # Muestra la ventana
sys.exit(app.exec_()) # Cierra la aplicación
```

#### 9.1. Click

Muestra un mensaje en la consola cuando se hace clic en el botón.

```python
def on_click():
  print('Button clicked!')

boton.clicked.connect(on_click)

```

#### 9.2. Cambiar texto

Cambiar el texto del botón cuando se hace clic en él.

```python
def on_click():
  boton.setText('Clicked!')

boton.clicked.connect(on_click)
```

#### 9.3. Cambiar color

Cambiar el color de fondo del botón cuando se hace clic en él.

```python
def on_click():
  boton.setStyleSheet('background-color: red')

boton.clicked.connect(on_click)
```

#### 9.4. Cambiar tamaño

Cambiar el tamaño del botón cuando se hace clic en él.

```python
def on_click():
  boton.resize(100, 100)

boton.clicked.connect(on_click)
```

#### 9.5. Cambiar posición

Cambiar la posición del botón cuando se hace clic en él.

```python
def on_click():
  boton.move(100, 100)

boton.clicked.connect(on_click)
```

#### 9.6. Ocultar

Oculta el botón cuando se hace clic en él.

```python
def on_click():
  boton.hide()

boton.clicked.connect(on_click)
```

#### 9.7. Mostrar

Muestra el botón cuando se hace clic en él.

```python
def on_click():
  boton.show()

boton.clicked.connect(on_click)

```

#### 9.8. Deshabilitar

Deshabilita el botón cuando se hace clic en él.

```python
def on_click():
  boton.setEnabled(False)

boton.clicked.connect(on_click)
```

#### 9.9. Habilitar

Habilita el botón cuando se hace clic en él.

```python
def on_click():
  boton.setEnabled(True)

boton.clicked.connect(on_click)
```

#### 9.10. Cerrar ventana

Cierra la ventana cuando se hace clic en el botón.

```python
def on_click():
  ventana.close()

boton.clicked.connect(on_click)
```