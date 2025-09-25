# 📌 CalculadoraSimple

Una calculadora de consola escrita en **Java**, diseñada con:

- **Algoritmo Shunting-yard (Dijkstra)** para el análisis de expresiones.  
- **Evaluador en notación polaca inversa (RPN)** para soportar operaciones con precedencia correcta y funciones avanzadas.  

Este proyecto nació como un ejercicio de programación y evolucionó hasta convertirse en una calculadora **extensible y modular**.

---

## 🚀 Características

- Entrada de expresiones matemáticas en formato natural:  
  `3+4*2/(1-5)^2`  
- Soporte de:
  - **Operadores aritméticos:** `+`, `-`, `*`, `/`, `^`  
  - **Operadores unarios:** `-x`, `+x`  
  - **Funciones:** `sin`, `cos`, `log`  
  - **Raíz cuadrada:** `√`  
- Precedencia correcta entre operadores.  
- **Módulos separados por responsabilidad** (`parser`, `comandos`, `terminalmenu`).  
- Extensible: nuevos operadores o funciones se agregan fácilmente en `OperatorRegistry`.  

---

## Clases clave:  
- `Tokenizer`: convierte la entrada en tokens (números, operadores, funciones).  
- `ShuntingYardParser`: transforma tokens en notación polaca inversa (RPN).  
- `RpnEvaluator`: evalúa la RPN aplicando operadores y funciones.  
- `OperatorRegistry`: registro central de operadores y funciones.  
- `ComandoResolverExpresion`: comando de menú para evaluar expresiones.  

---

## 🖥️ Ejemplo de uso
=== CALCULADORA SIMPLE ===

Resolver expresión

Salir

Ingresa una expresión (ej: 1+2*3):

`-(√9)^2` 

Resultado: -9.0

Otros ejemplos:

- `3+4*2/(1-5)^2` → `3.5`  
- `√9+16` → `19.0`  
- `sin(0)` → `0.0`  
- `cos(0)` → `1.0`  

---

## 🧪 Pruebas
El proyecto incluye un set de **pruebas unitarias JUnit 5** que cubren:

- Operadores básicos.  
- Funciones trigonométricas y logaritmo.  
- Raíz cuadrada y su versión con signo (`-√`).  
- Precedencia entre operadores.  
- Casos de error (`√-9`, división por cero, etc.).  

Para ejecutarlas en **BlueJ**:  
1. Abrir el proyecto.  
2. Clic derecho en la clase de test → `Probar todo`.  

---

## 🔧 Extensión

Para agregar nuevos operadores o funciones:  
1. Registrar en `OperatorRegistry`.  
2. Definir su precedencia, asociatividad y operación.  

Ejemplo (módulo `%`):

    java
    operators.put("%", new Operator("%", 2, Associativity.LEFT, (a, b) -> a % b));

## 📦 Dependencias

Este proyecto utiliza la librería [terminal-menu](https://github.com/philbone/java-terminal-menu)  
para construir menús interactivos en consola.

Para compilar y ejecutar, asegúrate de tener disponible el archivo `terminal-menu.jar` en tu classpath.

Ejemplo de ejecución:

    bash
    javac -cp .:terminal-menu.jar calculadorasimple/CalculadoraMain.java
    java  -cp .:terminal-menu.jar calculadorasimple.CalculadoraMain