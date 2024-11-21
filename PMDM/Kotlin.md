# Kotlin y Android

##### 👤 Autor: Ana Valladares González

### **Ciclo de Vida de una Actividad en Android**
   - **¿Qué es el ciclo de vida?** Una persona, a lo largo de su vida, pasa por diferentes momentos: nacimiento, crecimiento, descanso, muerte. Android maneja algo parecido para que la app no use recursos innecesarios.
   - **Estados Básicos**:
     - `onCreate()`: Aquí nace la actividad, donde se configuran las cosas iniciales como el diseño de la pantalla.
     - `onStart()`: La actividad ya está visible; imagina que ya “despertó”.
     - `onResume()`: Ahora la actividad está activa y el usuario puede interactuar con ella.
     - `onPause()`: El usuario se va a otra pantalla, pero la actividad aún existe.
     - `onStop()`: Ya no está visible, pero aún existe en el fondo.
     - `onDestroy()`: La actividad se elimina por completo y se libera toda la memoria.

### **Logcat**
   - **¿Qué es?** Si algo falla, Logcat te muestra el mensaje y dónde sucedió.
   - **Ejemplo**:
      ```kotlin
      private val :::TAG = "MiApp"
      Log.d(:::TAG, "La app está funcionando")
      ```

### **Jetpack Compose**
Jetpack Compose es una forma de crear interfaces gráficas en Android.

#### **Componentes Básicos en Jetpack Compose**
1. **Texto (`Text`)**
   - **Descripción**: Muestra texto en la pantalla. Es el componente de texto más básico.
   - **Ejemplo**:
     ```kotlin
     Text(
         text = "Hola Jetpack Compose!",
         fontSize = 24.sp,
         color = Color.Blue
     )
     ```
   - **Propiedades Importantes**:
     - `text`: El contenido del texto.
     - `fontSize`: Tamaño de la fuente.
     - `color`: Color del texto.

2. **Botón (`Button`)**
   - **Descripción**: Un botón que responde a toques y ejecuta una acción específica.
   - **Ejemplo**:
     ```kotlin
     Button(onClick = { /* acción cuando se toca el botón */ }) {
         Text("Pulsar aquí")
     }
     ```
   - **Propiedades Importantes**:
     - `onClick`: Define qué pasa cuando el usuario pulsa el botón.

3. **Modificadores (`Modifier`)**
   - **¿Qué son?** Se usan para cambiar la apariencia o el comportamiento de los componentes.
   - **Ejemplo**:
     ```kotlin
     Text(
         text = "Texto con padding y color de fondo",
         modifier = Modifier
             .padding(16.dp)
             .background(Color.LightGray)
     )
     ```
   - **Algunos Modificadores Útiles**:
     - `padding()`: Añade espacio alrededor del componente.
     - `background()`: Establece el color de fondo.
     - `size()`: Define el tamaño del componente.
     - `clickable()`: Convierte el componente en un elemento que responde a toques.

4. **Posicionamiento de Elementos (Layout)**
   - **Column**: Organiza elementos en una columna (de arriba a abajo).
     ```kotlin
     Column {
         Text("Elemento 1")
         Text("Elemento 2")
     }
     ```
   - **Row**: Coloca elementos en fila (de izquierda a derecha).
     ```kotlin
     Row {
         Text("Elemento A")
         Text("Elemento B")
     }
     ```
   - **Box**: Permite superponer elementos uno sobre otro.
     ```kotlin
     Box {
         Image(painterResource(R.drawable.imagen_fondo)) // No hemos dado imágenes
         Text("Texto encima de la imagen")
     }
     ```


#### **Gestionando el Estado en Jetpack Compose**

##### **Remember**
**¿Qué es `remember`?** Almacena el valor de una variable mientras el `Composable`* esté visible, evitando que se pierda cuando se vuelve a dibujar la pantalla.
  
> [!NOTE]
> ***Composable**: Se le pone `@Composable` a los métodos que definen algo visual. (Ejemplo:   `@Composable fun formulario() {...}`)

- **Ejemplo**:
    ```kotlin
    var contador by remember { mutableStateOf(0) } // Inicializa el contador en 0
    Button(onClick = { contador++ }) { // Incrementa el contador cuando se hace click en el botón
        Text("Contador: $contador")
    }
    ```

##### **State** y **MutableState**
   - **¿Qué es `State`?** Es una forma de decirle a `Compose` que algo cambió, y que debe actualizar la pantalla para reflejar ese cambio.
   - **¿Qué es `MutableState`?** Es un tipo de `State` que se puede cambiar. Es como una variable que `Compose` sabe que puede cambiar y debe actualizar la pantalla si lo hace.
   - **Diferencia entre `State` y `MutableState`**: `State` es inmutable (no se puede cambiar), mientras que `MutableState` es mutable.
    
   - **Ejemplo completo**:
     ```kotlin
     @Composable
     fun Contador() {
         var contador by remember { mutableStateOf(0) } // Inicializa el contador en 0 con mutableStateOf (puede cambiar) y remember (recuerda el valor)
         Column {
             Text("Contador actual: $contador")
             Button(onClick = { contador++ }) {
                 Text("Incrementar")
             }
         }
     }
     ```

#### **Eventos en Jetpack Compose**
**onClick** en botones
   - **Uso básico**: Definimos una función o acción que sucede cuando el usuario hace clic en el botón.
   - **Ejemplo**:
     ```kotlin
      Button(onClick = { /* acción al hacer clic */ }) {
          Text("Pulsar aquí")
      }
      ```

#### **LaunchedEffect y Corutinas**
- **¿Qué es `LaunchedEffect`?** Es un bloque de código que ejecuta una tarea cuando el `Composable` aparece en la pantalla. Sirve para operaciones asíncronas, como cargar datos de una API.
- **¿Qué son las Corutinas?** Son una forma de ejecutar tareas de fondo sin bloquear la app (en el ViewModel). Puedes usarlas para cargar datos de internet, por ejemplo.
- **Ejemplo**:
  ```kotlin
  @Composable
  fun PantallaConCarga() {
      LaunchedEffect(Unit) { // Se ejecuta el bloque de código cuando el Composable aparece en pantalla (Unit es un tipo que representa la ausencia de un valor significativo, similar al void en Java)
          // Aquí podríamos cargar datos de una API
          delay(2000) // Simula una carga de 2 segundos
          println("Datos cargados")
      }
      Text("Cargando...")
  }
  ```

#### **Arquitectura MVVM con Jetpack Compose**
1. **Datos**: Se definen los datos que utiliza la app, como objetos y listas.
   - Ejemplo:
     ```kotlin
     data class Tarea(val nombre: String, val completado: Boolean)
     ```

2. **ViewModel (Lógica)**: Gestiona los datos y la lógica de la app. Define funciones para obtener o actualizar datos.
   - Ejemplo:
     ```kotlin
     class TareasViewModel : ViewModel() {
         private val _tareas = MutableLiveData<List<Tarea>>()
         val tareas: LiveData<List<Tarea>> = _tareas

         fun añadirTarea(tarea: Tarea) {
             _tareas.value = _tareas.value.orEmpty() + tarea
         }
     }
     ```

3. **View (UI)**: Composables que muestran los datos y responden a las interacciones del usuario.
   - Ejemplo:
     ```kotlin
     @Composable
     fun ListaDeTareas(viewModel: TareasViewModel) {
         val tareas by viewModel.tareas.observeAsState(emptyList())
         Column {
             tareas.forEach { tarea ->
                 Text(tarea.nombre)
             }
             Button(onClick = { viewModel.añadirTarea(Tarea("Nueva Tarea", false)) }) {
                 Text("Añadir Tarea")
             }
         }
     }
     ```


4. **Datos**: Un `enum` es un tipo de dato que permite crear un conjunto de valores fijos y relacionados. `Object` se usa para crear una única instancia de una clase, lo que se conoce como un `singleton`, y garantiza que solo haya un objeto de esa clase en toda la aplicación. `Data class` es una clase que solo contiene datos y no tiene lógica, y se usa para almacenar datos de forma estructurada.
   
   - Ejemplo de `enum`:
     ```kotlin
      enum class DiaDeLaSemana {
          LUNES, MARTES, MIERCOLES, JUEVES, VIERNES, SABADO, DOMINGO
      }
     ```

   - Ejemplo de `object` (singleton):
     ```kotlin
      object BaseDeDatos {
          val nombre = "MiBaseDeDatos"
          
          fun conectar() {
              println("Conectado a $nombre")
          }
      }

      fun main() {
          // Usando el singleton
          BaseDeDatos.conectar()  // Imprime: Conectado a MiBaseDeDatos
      }
     ```

     En este ejemplo, BaseDeDatos es un singleton, lo que significa que solo hay una instancia de esa clase, y puedes acceder a sus propiedades y métodos directamente sin necesidad de crear un objeto.

    - Ejemplo de `data class`:
      ```kotlin
        data class Persona(val nombre: String, val edad: Int)
  
        fun main() {
            val persona = Persona("Ana", 25)
            println(persona)  // Imprime: Persona(nombre=Ana, edad=25)
        }
      ```

#### **Patrón Observer**
- **¿Qué es?** Es un patrón de diseño que se usa para notificar a los objetos interesados cuando un objeto cambia de estado. *(Irá en el ViewModel)*
- **Ejemplo**:
  ```kotlin // 
    // Interfaz Observador (el que recibe la notificación)
    interface Observador {
        fun actualizar(mensaje: String)
    }

    // Clase Sujeto (el que cambia de estado y notifica a los observadores)
    class Sujeto {
        private val observadores = mutableListOf<Observador>() // Lista de observadores
        
        fun agregarObservador(observador: Observador) { // Método para agregar observadores a la lista
            observadores.add(observador)
        }

        fun cambiarEstado() { // Método que cambia el estado del sujeto
            notificarObservadores("¡Estado cambiado!") // Notifica a los observadores que el estado ha cambiado
        }

        private fun notificarObservadores(mensaje: String) { // Método para notificar a los observadores
            for (observador in observadores) {
                observador.actualizar(mensaje) // Llama al método actualizar de cada observador
            }
        }
    }

    // Observador 1
    class ObservadorConcreto1 : Observador {
        override fun actualizar(mensaje: String) {
            println("Observador 1 recibió el mensaje: $mensaje")
        }
    }

    // Observador 2
    class ObservadorConcreto2 : Observador {
        override fun actualizar(mensaje: String) { // Método que se llama cuando el sujeto notifica a los observadores
            println("Observador 2 recibió el mensaje: $mensaje") // Imprime el mensaje recibido por el observador
        }
    }

    fun main() {
        val sujeto = Sujeto()
        val observador1 = ObservadorConcreto1()
        val observador2 = ObservadorConcreto2()

        // El sujeto agrega los observadores
        sujeto.agregarObservador(observador1)
        sujeto.agregarObservador(observador2)

        // El sujeto cambia su estado y notifica a los observadores
        sujeto.cambiarEstado()
    }
  ```

   **Diagrama de secuencia entre ViewModel, UI y Datos**:
    ```mermaid
    sequenceDiagram
        participant User
        participant UI
        participant ViewModel
        participant Datos

        User ->> UI: Interactuar con la app
        UI ->> ViewModel: Solicitar datos
        ViewModel ->> Datos: Obtener datos
        Datos -->> ViewModel: Devolver datos
        ViewModel -->> UI: Devolver datos
    ```

    ---

   **Diagrama de estado entre ViewModel, UI y Datos**:
    ```mermaid
    stateDiagram
        [*] --> UI
        UI --> ViewModel: Solicitar datos
        ViewModel --> Datos: Obtener datos
        Datos --> ViewModel: Devolver datos
        ViewModel --> UI: Devolver datos
    ```

---

### **Ejemplito de Kotlin**
```kotlin
// Datos que simulan la base de datos de productos
class Datos {
    private val productos = listOf("Producto A", "Producto B", "Producto C")

    // Devuelve los productos disponibles
    fun obtenerProductos(): List<String> {
        return productos // En este caso no hay validaciones condicionales
    }
}

// ViewModel que gestiona la lógica de la búsqueda de productos
class VM(private val datos: Datos) {
    fun obtenerProductos(): List<String> {
        return datos.obtenerProductos() // No hay lógica condicional aquí, simplemente devuelve la lista
    }
}

// Interfaz de usuario (UI) que interactúa con el ViewModel
class UI(private val vm: VM) {
    fun onBuscarProductos() {
        // Consulta la lista de productos al ViewModel
        val productos = vm.obtenerProductos()

        // Muestra los productos encontrados
        if (productos.isEmpty()) {
            mostrarMensaje("No se encontraron productos.")
        } else {
            mostrarProductos(productos)
        }
    }

    fun mostrarMensaje(mensaje: String) {
        // Muestra un mensaje al usuario
        println(mensaje)
    }

    fun mostrarProductos(productos: List<String>) {
        // Muestra la lista de productos al usuario
        println("Productos disponibles:")
        productos.forEach { println(it) }
    }
}

fun main() {
    val datos = Datos()
    val vm = VM(datos)
    val ui = UI(vm)

    // Simula la búsqueda de productos
    ui.onBuscarProductos() // Muestra la lista de productos
}
```


Enunciado:

Crea un Repositorio privado para realizar las siguientes modificaciones en este codigo, comentando adecuadamente en el código lo realizado y realizando un readme explicativo:

Implementa una cuenta atrás 5...4...3...2...1 [tiene que ser una corutina]
Utiliza los Estados auxiliares para la cuenta atrás
Configura un cuadro de texto para mostrar la cuenta atrás
Cuando el usuario le da al "Start" empieza la cuenta atrás
Si la cuenta atrás llega a uno y el usuario aun no acertó, la app vuelve al estado INICIO
Plantea una mejora
Entrega el enlace al repositorio