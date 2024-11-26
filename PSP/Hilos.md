# Programación de Procesos

##### 👤 Autor: Ana Valladares González

### **java.lang.Runtime**

Se encarga de ejecutar los procesos de Java. Se puede obtener una instancia de esta clase mediante el método `getRuntime()`, y se puede ejecutar un proceso mediante el método `exec()`. 

```java
try {
    // Ejecuta el bloc de notas
    Runtime.getRuntime().exec("notepad.exe");

    // Ejecuta el bloc de notas, indicando que prueba.txt es el archivo que se va a abrir o crear
    Runtime.getRuntime().exec("notepad.exe prueba.txt");

    // Ejecuta el bloc de notas, utilizando un array de Strings
    String[] procesoAEjecutar = {"notepad.exe", "prueba.txt"};
    Runtime.getRuntime().exec(procesoAEjecutar);
} catch (IOException e) {
    System.out.println("Error: " + e.getMessage());
}
```

### **java.lang.ProcessBuilder**

Se encarga de manejar los atributos de los procesos. Se puede obtener una instancia de esta clase mediante el constructor `ProcessBuilder(String... command)`, y se puede ejecutar un proceso mediante el método `start()`. 

```java
ProcessBuilder pBloc = new ProcessBuilder("notepad.exe", "prueba.txt");
Process p = pBloc.start();
```

#### **Métodos de la clase ProcessBuilder**

- `start()`: Inicia el proceso.
- `command()`: Devuelve el comando que se utilizó para ejecutar el proceso.
- `directory()`: Devuelve el directorio de trabajo del proceso.
- `environment()`: Devuelve el entorno del proceso.
- `redirectInput()`: Redirige la entrada del proceso.
- `redirectOutput()`: Redirige la salida del proceso.
- `inheritIO()`: Hereda la entrada, salida y error del proceso.

### **java.lang.Process**

Se encarga de manejar los procesos. Se puede obtener una instancia de esta clase mediante el método `exec()`, y se puede obtener la salida del proceso mediante el método `getInputStream()`. 

```java
Process proceso = Runtime.getRuntime().exec("notepad.exe");
InputStream entrada = proceso.getInputStream();
int i;
while ((i = entrada.read()) != -1) {
    System.out.print((char) i);
}
```

#### **Métodos de la clase Process**

- `int exitValue()`: Devuelve el valor de salida del proceso.
- `boolean isAlive()`: Devuelve si el proceso está vivo.
- `int waitFor()`: Espera a que el proceso termine.
- `boolean waitFor(long timeout, TimeUnit unit)`: Espera a que el proceso termine durante un tiempo determinado.
- `void Destroy()`: Destruye el proceso.
- `Process destroyForcibly()`: Destruye el proceso de forma forzosa.

### **java.lang.Thread**

Se encarga de manejar los hilos de ejecución. Se puede obtener una instancia de esta clase mediante el constructor `Thread()`, y se puede ejecutar un hilo mediante el método `start()`. 

```java
Thread hilo = new Thread();
hilo.start();
```

#### **Métodos de la clase Thread**

- `void run()`: Método que se ejecuta cuando se inicia el hilo.
- `void start()`: Inicia el hilo.
- `void sleep(long milisegundos)`: Hace que el hilo duerma durante un tiempo determinado.
    ```java
    Thread hilo = new Thread();
    hilo.start(); // Inicia el hilo
    hilo.sleep(1000); // Hace que el hilo duerma durante 1 segundo
    System.out.println("Hilo terminado");
    ```
- `void join()`: Espera a que el hilo termine.

    ```java
    Thread hilo = new Thread();
    hilo.start(); // Inicia el hilo
    hilo.join(); // Espera a que el hilo termine antes de continuar con el programa
    System.out.println("Hilo terminado");
    ```
- `void interrupt()`: Interrumpe el hilo.
- `boolean isAlive()`: Devuelve si el hilo está vivo.
- `static void yield()`: Hace que el hilo actual ceda el procesador.
- `static Thread currentThread()`: Devuelve el hilo actual.
- `static void dumpStack()`: Muestra la pila de llamadas del hilo actual.

### **java.lang.Runnable**

Se encarga de manejar los hilos de ejecución. Se puede obtener una instancia de esta clase mediante el método `run()`, y se puede ejecutar un hilo mediante el constructor `Thread(Runnable target)`. 

```java
Runnable r = new Runnable() {
    @Override
    public void run() {
        System.out.println("Hilo ejecutado");
    }
};
Thread hilo = new Thread(r);
hilo.start();
```

### Diferencia entre `Thread` y `Runnable`

La diferencia principal es que `Thread` es una **clase** que extiende de `Object`, mientras que `Runnable` es una **interfaz** que se puede implementar en una clase.

### **Método join() [Clase Thread]**

El método `join()` de la clase `Thread` hace que el hilo actual espere a que termine el hilo en el que se ha llamado, antes de continuar con el programa.

```java
Thread hilo = new Thread();
hilo.start(); // Inicia el hilo
hilo.join(); // Espera a que el hilo termine antes de continuar con el programa
System.out.println("Hilo terminado");
```

### **Método sleep() [Clase Thread]**

El método `sleep()` de la clase `Thread` hace que el hilo actual duerma durante un tiempo determinado.

```java
Thread hilo = new Thread();
hilo.start(); // Inicia el hilo
hilo.sleep(1000); // Hace que el hilo duerma durante 1 segundo
System.out.println("Hilo terminado");
```

### **Método getInputStream() [Clase Process]**

El método `getInputStream()` de la clase `Process` devuelve la información o errores que se han producido durante la ejecución del proceso.

> [!IMPORTANT]
> Debemos simplificar el proceso con BufferedReader e InputStreamReader para poder leer la salida del proceso, además de métodos como `readLine()` para leer línea a línea.

```java
Process p = pbuilder.start();
BufferedReader br = new BufferedReader(new InputStreamReader(p.getInputStream()));
String linea;
while ((linea = br.readLine()) != null) {
    System.out.println(linea);
}
br.close();
```

### **Pipelines**

Un pipeline es una serie de procesos conectados entre sí, de manera que la salida de un proceso es la entrada del siguiente. Se pueden crear pipelines mediante la clase `ProcessBuilder`.

```java
List<ProcessBuilder> procesos = Arrays.asList(
    new ProcessBuilder("ls", "-l"),
    new ProcessBuilder("grep", "java"),
    new ProcessBuilder("wc", "-l")
); // Lista de procesos
List<Process> pipes = ProcessBuilder.startPipeline(procesos); // Inicia los procesos 
Process last = pipes.get(pipes.size() - 1);	// Último proceso
System.out.println("Resultado: " + last.getInputStream().read()); // Muestra el resultado del último proceso
```
