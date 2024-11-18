# Kotlin y Android

##### 👤 Autor: Ana Valladares González

### 1. **Ciclo de Vida de una Actividad en Android**
   - **¿Qué es el ciclo de vida?** Imagina que la actividad de tu app es como una persona. A lo largo del día (o de su vida), pasa por diferentes momentos: nacimiento, crecimiento, descanso, muerte. Android maneja algo parecido para que la app no use recursos innecesarios.
   - **Estados Básicos**:
     - `onCreate()`: Aquí nace la actividad, donde se configuran las cosas iniciales como el diseño de la pantalla.
     - `onStart()`: La actividad ya está visible; imagina que ya “despertó”.
     - `onResume()`: Ahora la actividad está activa y el usuario puede interactuar con ella.
     - `onPause()`: El usuario se va a otra pantalla, pero la actividad aún existe.
     - `onStop()`: Ya no está visible, pero aún existe en el fondo.
     - `onDestroy()`: La actividad se elimina por completo y se libera toda la memoria.
   - **Por qué importa**: Nos ayuda a saber cuándo guardar datos importantes, por ejemplo, si el usuario cierra la app o gira el teléfono.

### 2. **Logcat**
   - **¿Qué es?** Es como una hoja de notas que te muestra qué está pasando en tu app mientras la ejecutas. Si algo falla, Logcat te muestra el error y dónde sucedió.
   - **Niveles de Log (Mensajes)**:
     - `Log.d("Etiqueta", "Mensaje")`: Mensajes de depuración.
     - `Log.e("Etiqueta", "Mensaje")`: Errores.
     - `Log.i("Etiqueta", "Mensaje")`: Información.
   - **Por qué es útil**: Te permite ver qué hace tu app en cada momento y detectar problemas cuando algo no funciona.

### 3. **Jetpack Compose**

Jetpack Compose es una forma de crear interfaces en Android usando código más sencillo y directo. Es un sistema basado en componentes que permite crear y organizar elementos de la interfaz de manera declarativa, sin usar XML.

**¿Por qué usar Jetpack Compose?**
- **Simplifica el código**: No necesitas archivos XML. Todo el diseño está en un solo lugar.
- **Es reactivo**: La interfaz de usuario responde automáticamente a los cambios en los datos.
- **Modular y flexible**: Puedes combinar componentes (`Composables`) de varias maneras para lograr el diseño que quieres.

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
   - **¿Qué son?** Los modificadores se usan para cambiar la apariencia o el comportamiento de los componentes. Por ejemplo, puedes ajustar el tamaño, el color, o agregar márgenes.
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
1. **remember**
   - **¿Qué es `remember`?** Almacena el valor de una variable mientras el `Composable`* esté visible, evitando que se pierda cuando se vuelve a dibujar la pantalla.
  
      > [!NOTE]
      > ***Composable**: Se le pone `@Composable` a los métodos que definen algo visual. (Ejemplo: `@Composable fun formulario() {...}`)

   - **Ejemplo**:
     ```kotlin
     var contador by remember { mutableStateOf(0) } // Inicializa el contador en 0
     Button(onClick = { contador++ }) { // Incrementa el contador cuando se hace click en el botón
         Text("Contador: $contador")
     }
     ```

1. **State** y **MutableState**
   - **¿Qué es `State`?** Es una forma de decirle a `Compose` que algo cambió, y que debe actualizar la pantalla para reflejar ese cambio.
   - **¿Qué es `MutableState`?** Es un tipo de `State` que se puede cambiar. Es como una variable que `Compose` sabe que puede cambiar y debe actualizar la pantalla si lo hace.
   - **Diferencia entre `State` y `MutableState`**: `State` es inmutable (no se puede cambiar), mientras que `MutableState` es mutable.
    
   - **Ejemplo completo**:
     ```kotlin
     @Composable
     fun Contador() {
         var contador by remember { mutableStateOf(0) }
         Column {
             Text("Contador actual: $contador")
             Button(onClick = { contador++ }) {
                 Text("Incrementar")
             }
         }
     }
     ```

#### **Eventos en Jetpack Compose**
1. **onClick** en botones
   - **Uso básico**: Definimos una función o acción que sucede cuando el usuario hace clic en el botón.
   - **Ejemplo**:
     ```kotlin
      Button(onClick = { /* acción al hacer clic */ }) {
          Text("Pulsar aquí")
      }
      ```
    - **Ejemplo con contador**:
    - ```kotlin
      var contador by remember { mutableStateOf(0) }
      Button(onClick = { contador++ }) {
          Text("Contador: $contador")
      }
      ```
### **LaunchedEffect y Corutinas**
- **¿Qué es `LaunchedEffect`?** Es un bloque de código que ejecuta una tarea cuando el `Composable` aparece en la pantalla. Sirve para operaciones asíncronas, como cargar datos de una API.
- **Ejemplo**:
  ```kotlin
  @Composable
  fun PantallaConCarga() {
      LaunchedEffect(Unit) {
          // Aquí podríamos cargar datos de una API
          delay(2000)
          println("Datos cargados")
      }
      Text("Cargando...")
  }
  ```
- **Corutinas en ViewModel**: En el ViewModel puedes lanzar corutinas para manejar tareas de fondo (como cargar datos de internet) sin bloquear la app.

### **Arquitectura MVVM con Jetpack Compose**
1. **Model (Datos)**: Donde se definen los datos que utiliza la app, como objetos y listas.
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

4. **Interacción entre ViewModel y UI**:
   - **Observabilidad**: La UI observa los cambios en el ViewModel y se actualiza automáticamente.
   - **LaunchedEffect con ViewModel**: Puedes usar `LaunchedEffect` para iniciar la carga de datos en el ViewModel.

---

## Repaso

### 4. **remember y State en Jetpack Compose**
   - **¿Qué es `remember`?** Imagina que tienes una variable que quieres que conserve su valor mientras usas la app. `remember` es como una memoria a corto plazo que te ayuda a guardar valores mientras la pantalla no se actualice o cambie.
   - **Estado (`State`)**: Es una forma de decirle a `Compose` que algo cambió, y que debe actualizar la pantalla para reflejar ese cambio. Por ejemplo, si pulsas un botón y quieres que cambie el texto, usarías un `State` para actualizarlo automáticamente.

### 5. **onClick (Eventos de Click)**
   - **¿Qué es?** `onClick` es lo que sucede cuando tocas un botón o un elemento. Es una función que especifica qué debe hacer la app cuando ocurre un clic.
   - **Ejemplo**: `Button(onClick = { texto = "Hola!" }) { Text("Presiona aquí") }` cambia el texto en pantalla cuando haces clic en el botón.

### 6. **Arquitectura MVVM (Model-View-ViewModel)**
   - **¿Qué significa MVVM?** Es una forma de organizar el código para que esté dividido en partes, lo que hace que sea más fácil de leer y mantener.
     - **Model (Datos)**: Donde se guardan los datos que maneja tu app, como listas, objetos y constantes.
     - **ViewModel (Lógica)**: Es el "jefe" que toma los datos y decide qué mostrar en la pantalla y cómo.
     - **View (UI)**: Es lo que ves en la pantalla, como botones, texto, y otras cosas de `Compose`.
   - **Cómo se comunican**:
     - La pantalla (UI) observa los cambios en el ViewModel y se actualiza sola cuando hay un cambio.

### 7. **Corutinas y Efectos en Jetpack Compose**
   - **¿Qué es una corutina?** Es una forma de ejecutar tareas de fondo sin bloquear la app. Imagina que tu app necesita esperar a que se cargue una imagen; con corutinas, puedes hacer eso en segundo plano sin que la app se congele.
   - **LaunchedEffect**: Te permite ejecutar una corutina dentro de un `Composable`. Es útil cuando quieres hacer algo una vez, como cargar datos cuando la pantalla aparece.
   - **Ejemplo de uso**: `LaunchedEffect(Unit) { cargarDatos() }` ejecutará `cargarDatos()` una vez cuando el `Composable` aparezca en pantalla.

### 8. **Ejemplo Práctico de MVVM con Jetpack Compose**
   - **Modelo (Datos)**: Crea un modelo, por ejemplo, una clase `Tarea(val nombre: String, val completado: Boolean)`.
   - **ViewModel (Lógica)**: Añade una lista de tareas en el ViewModel y funciones para añadir o marcar tareas como completas.
   - **UI (Interfaz)**: Crea un diseño que muestre la lista de tareas y botones para interactuar con ellas. La pantalla observa el ViewModel y se actualiza sola.
