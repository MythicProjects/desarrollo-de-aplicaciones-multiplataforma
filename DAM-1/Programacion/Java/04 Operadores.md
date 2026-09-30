---
tags:
  - java
  - programacion
  - dam1
unidad: 4
tema: Operadores
---

# Unidad 4. Operadores

> [!abstract] Objetivos de la unidad
> - Comprender los conceptos de operador, operando y expresión.
> - Utilizar correctamente los operadores aritméticos, teniendo en cuenta las particularidades de la división entera y el módulo.
> - Diferenciar el preincremento del postincremento y el predecremento del postdecremento.
> - Aplicar los operadores de asignación simple y compuesta.
> - Construir expresiones de comparación y expresiones lógicas complejas.
> - Conocer la evaluación en cortocircuito y la precedencia de los operadores.

---

## 1. Conceptos fundamentales

> [!note] Definiciones
> - **Operador:** símbolo que indica al compilador que realice una operación determinada (matemática, lógica, de comparación, etc.).
> - **Operando:** valor o variable sobre el que actúa un operador.
> - **Expresión:** combinación de operandos y operadores que, al evaluarse, produce un **único valor** de un tipo determinado.

```java
int resultado = a + b;
//              │ │ └── operando
//              │ └──── operador
//              └────── operando
//              a + b → expresión (se evalúa a un valor int)
```

### 1.1. Clasificación según el número de operandos

| Tipo | Número de operandos | Ejemplos |
|---|---|---|
| **Unario** | Uno | `-a`, `++a`, `!esValido` |
| **Binario** | Dos | `a + b`, `a > b`, `a && b` |
| **Ternario** | Tres | `condicion ? valor1 : valor2` |

### 1.2. Clasificación según su función

| Categoría | Operadores |
|---|---|
| Aritméticos | `+` `-` `*` `/` `%` |
| Unarios | `+` `-` `++` `--` `!` |
| De asignación | `=` `+=` `-=` `*=` `/=` `%=` |
| De comparación (relacionales) | `==` `!=` `>` `>=` `<` `<=` |
| Lógicos | `&&` `\|\|` `!` |
| Ternario | `? :` |

> [!note] Alcance
> El operador ternario, por su relación con las estructuras condicionales, se estudia en la [[06 Estructuras condicionales|Unidad 6]].

---

## 2. Operadores aritméticos

### 2.1. Tabla de operadores

| Operador | Operación | Ejemplo | Resultado |
|---|---|---|---|
| `+` | Suma | `7 + 2` | `9` |
| `-` | Resta | `7 - 2` | `5` |
| `*` | Multiplicación | `7 * 2` | `14` |
| `/` | División | `7 / 2` | `3` (división entera) |
| `%` | Módulo (resto de la división) | `7 % 2` | `1` |

> [!info] El operador `+` con cadenas
> Cuando al menos uno de los operandos es una cadena, el operador `+` no suma, sino que **concatena** (véase la [[03 Cadenas de texto|Unidad 3]]).

### 2.2. La división entera

El tipo del resultado de una operación aritmética depende del tipo de sus operandos:

- Si **ambos operandos son enteros**, el resultado es **entero**: la parte decimal se **descarta** (no se redondea).
- Si **al menos uno** de los operandos es **decimal**, el resultado es **decimal**.

```java
System.out.println(7 / 2);     // 3    → ambos enteros
System.out.println(7.0 / 2);   // 3.5  → un operando es double
System.out.println(7 / 2.0);   // 3.5
System.out.println((double) 7 / 2); // 3.5 → casting previo a la división
```

> [!danger] Error lógico frecuente
> Asignar el resultado a una variable `double` **no** evita la división entera, porque la división se realiza **antes** de la asignación:
> ```java
> int suma = 7, cantidad = 2;
> double media = suma / cantidad;          // 3.0 → INCORRECTO
> double mediaOk = (double) suma / cantidad; // 3.5 → correcto
> ```

### 2.3. El operador módulo

El operador `%` devuelve el **resto** de la división entera entre dos números. Sus aplicaciones más habituales son:

| Aplicación | Expresión | Interpretación |
|---|---|---|
| Comprobar si un número es par | `n % 2 == 0` | Resto 0 al dividir entre 2 → par |
| Comprobar si un número es impar | `n % 2 != 0` | Resto distinto de 0 → impar |
| Comprobar divisibilidad | `n % d == 0` | `n` es divisible entre `d` |
| Obtener la última cifra | `n % 10` | `1234 % 10` → `4` |

```java
System.out.println(10 % 3);  // 1
System.out.println(10 % 2);  // 0 → 10 es par
System.out.println(1234 % 10); // 4
```

### 2.4. División por cero

| Operación | Comportamiento |
|---|---|
| Entero entre cero (`10 / 0`) | Lanza la excepción `ArithmeticException` y el programa se detiene. |
| Decimal entre cero (`10.0 / 0`) | No lanza excepción; devuelve `Infinity`. |

> [!note] Alcance
> La gestión de excepciones como `ArithmeticException` se estudia en la [[10 Errores y excepciones|Unidad 10]].

### 2.5. Operaciones matemáticas avanzadas: la clase `Math`

Java no dispone de operadores para la potencia o la raíz cuadrada. Para estas operaciones se utiliza la clase **`Math`** (paquete `java.lang`, importado automáticamente):

| Método | Descripción | Ejemplo | Resultado |
|---|---|---|---|
| `Math.pow(base, exp)` | Potencia | `Math.pow(2, 3)` | `8.0` |
| `Math.sqrt(x)` | Raíz cuadrada | `Math.sqrt(16)` | `4.0` |
| `Math.abs(x)` | Valor absoluto | `Math.abs(-5)` | `5` |
| `Math.round(x)` | Redondeo al entero más próximo | `Math.round(2.6)` | `3` |
| `Math.max(a, b)` / `Math.min(a, b)` | Máximo / mínimo | `Math.max(4, 9)` | `9` |
| `Math.PI` | Constante π | `Math.PI` | `3.141592653589793` |

> [!warning] Cuidado con `^`
> En Java, el símbolo `^` **no** representa la potencia (es un operador lógico a nivel de bits). Para elevar un número a una potencia se utiliza `Math.pow()`.

---

## 3. Operadores unarios

Los operadores unarios actúan sobre **un único operando**.

| Operador | Descripción |
|---|---|
| `+` | Indica un valor positivo (en la práctica no modifica el valor). |
| `-` | Cambia el signo del valor. |
| `++` | Incrementa el valor en 1. |
| `--` | Decrementa el valor en 1. |
| `!` | Niega un valor lógico (se estudia en el apartado 6). |

### 3.1. Operadores de signo

```java
int a = 3, resultado;

resultado = +a;
System.out.println("resultado +a = " + resultado); // 3

resultado = -a;
System.out.println("resultado -a = " + resultado); // -3
```

### 3.2. Incremento y decremento

Los operadores `++` y `--` suman o restan 1 a una variable. Pueden escribirse **antes** (forma *pre*) o **después** (forma *post*) de la variable. Cuando se utilizan como instrucción aislada, ambas formas son equivalentes:

```java
int contador = 5;
contador++; // contador = 6
++contador; // contador = 7
```

La diferencia aparece cuando el operador forma parte de una **expresión** cuyo valor se utiliza (por ejemplo, en una asignación):

| Forma | Sintaxis | Funcionamiento |
|---|---|---|
| **Preincremento** | `++a` | Primero **incrementa** la variable y después **utiliza** su nuevo valor. |
| **Postincremento** | `a++` | Primero **utiliza** el valor actual y después **incrementa** la variable. |
| **Predecremento** | `--a` | Primero **decrementa** la variable y después **utiliza** su nuevo valor. |
| **Postdecremento** | `a--` | Primero **utiliza** el valor actual y después **decrementa** la variable. |

```java
public class OperadoresUnarios {
    public static void main(String[] args) {
        int a, b, resultado;

        // Preincremento
        a = 3;
        resultado = ++a; // primero incrementa (a = 4), después asigna
        System.out.println("resultado ++a = " + resultado); // 4
        System.out.println("a = " + a);                     // 4

        // Postincremento
        a = 3;
        resultado = a++; // primero asigna (resultado = 3), después incrementa
        System.out.println("resultado a++ = " + resultado); // 3
        System.out.println("a = " + a);                     // 4

        // Predecremento
        b = -2;
        resultado = --b; // primero decrementa (b = -3), después asigna
        System.out.println("resultado --b = " + resultado); // -3
        System.out.println("b = " + b);                     // -3

        // Postdecremento
        b = -2;
        resultado = b--; // primero asigna (resultado = -2), después decrementa
        System.out.println("resultado b-- = " + resultado); // -2
        System.out.println("b = " + b);                     // -3
    }
}
```

> [!tip] Regla mnemotécnica
> La posición del operador indica el **orden** de las acciones:
> - `++a`: el operador va **delante** → **primero incrementa**.
> - `a++`: el operador va **detrás** → **incrementa después**.
>
> En ambos casos, la variable termina incrementada; lo único que cambia es el valor que devuelve la expresión.

> [!warning] Legibilidad
> Utilizar incrementos dentro de expresiones complejas dificulta la lectura del código. Se recomienda emplearlos como instrucciones aisladas (`contador++;`) o en la actualización de los bucles `for` (véase la [[07 Bucles|Unidad 7]]).

---

## 4. Operadores de asignación

### 4.1. Asignación simple

El operador **`=`** evalúa la expresión situada a su derecha y almacena el resultado en la variable de su izquierda:

```java
var miNumero = 10;
int miNumero2;
miNumero2 = 15;
```

### 4.2. Asignación compuesta

Los operadores de asignación compuesta combinan una operación aritmética con una asignación, lo que permite escribir de forma abreviada las instrucciones que modifican una variable a partir de su propio valor.

| Operador | Ejemplo | Equivalente a |
|---|---|---|
| `+=` | `n += 5` | `n = n + 5` |
| `-=` | `n -= 3` | `n = n - 3` |
| `*=` | `n *= 2` | `n = n * 2` |
| `/=` | `n /= 4` | `n = n / 4` |
| `%=` | `n %= 4` | `n = n % 4` |

```java
public class OperadoresAsignacion {
    public static void main(String[] args) {
        var miNumero = 10;

        miNumero += 5; // miNumero = miNumero + 5 → 15
        System.out.println("miNumero = " + miNumero);

        miNumero *= 2; // miNumero = miNumero * 2 → 30
        System.out.println("miNumero = " + miNumero);

        miNumero -= 10; // → 20
        miNumero /= 4;  // → 5
        miNumero %= 3;  // → 2
        System.out.println("miNumero = " + miNumero);
    }
}
```

> [!info] Uso con cadenas
> El operador `+=` también puede aplicarse a cadenas para concatenar texto al final: `mensaje += " añadido";`.

> [!info] Conversión implícita en la asignación compuesta
> Los operadores compuestos realizan un *casting* automático al tipo de la variable. Por ello, `int n = 5; n += 2.7;` compila y deja `n = 7`, mientras que `n = n + 2.7;` produce un error de compilación.

### 4.3. Asignación de variables múltiples

Pueden declararse y asignarse varias variables del mismo tipo en una sola instrucción:

```java
int a = 10, b = 15, c = 20;
System.out.println("a = " + a + ", b = " + b + ", c = " + c);
```

---

## 5. Operadores de comparación (relacionales)

### 5.1. Concepto

Los operadores de comparación **comparan dos valores** y devuelven siempre un resultado de tipo **`boolean`** (`true` o `false`). Son la base de las condiciones que controlan el flujo del programa.

| Operador | Significado | Ejemplo (`a = 3`, `b = 2`) | Resultado |
|---|---|---|---|
| `==` | Igual a | `a == b` | `false` |
| `!=` | Distinto de | `a != b` | `true` |
| `>` | Mayor que | `a > b` | `true` |
| `>=` | Mayor o igual que | `a >= b` | `true` |
| `<` | Menor que | `a < b` | `false` |
| `<=` | Menor o igual que | `a <= b` | `false` |

```java
public class OperadoresComparacion {
    public static void main(String[] args) {
        int a = 3, b = 2;

        var resultado = a == b;
        System.out.println("a == b : " + resultado); // false

        resultado = a != b;
        System.out.println("a != b : " + resultado); // true

        resultado = a > b;
        System.out.println("a > b : " + resultado);  // true

        resultado = a >= b;
        System.out.println("a >= b : " + resultado); // true

        resultado = a < b;
        System.out.println("a < b : " + resultado);  // false

        resultado = a <= b;
        System.out.println("a <= b : " + resultado); // false
    }
}
```

> [!danger] `=` frente a `==`
> - `=` es el operador de **asignación**: guarda un valor.
> - `==` es el operador de **comparación**: comprueba si dos valores son iguales.
>
> Confundirlos es uno de los errores más habituales al comenzar a programar.

> [!warning] Comparación de objetos
> Con tipos primitivos, `==` compara **valores**. Con objetos (como `String`), `==` compara **referencias**, no el contenido. Para comparar el contenido de cadenas se utiliza el método **`equals()`** (véase la [[03 Cadenas de texto|Unidad 3]]).

> [!info] Comparación de caracteres
> Los operadores relacionales también pueden aplicarse a valores `char`, ya que internamente cada carácter tiene asociado un código numérico Unicode. Por ejemplo, `'a' < 'b'` devuelve `true`.

---

## 6. Operadores lógicos

### 6.1. Concepto

Los operadores lógicos **combinan o modifican valores booleanos** y devuelven un resultado `boolean`. Permiten construir condiciones complejas a partir de condiciones simples.

| Operador | Nombre | Devuelve `true` si… |
|---|---|---|
| `&&` | AND (Y lógico) | **Ambos** operandos son `true`. |
| `\|\|` | OR (O lógico) | **Al menos uno** de los operandos es `true`. |
| `!` | NOT (negación) | El operando es `false` (invierte el valor). |

> [!tip] Escritura del operador OR
> El operador OR se escribe con dos caracteres ***pipe*** (`||`). En los teclados españoles se obtiene con `AltGr + 1`.

### 6.2. Tablas de verdad

Una **tabla de verdad** muestra el resultado de un operador lógico para todas las combinaciones posibles de sus operandos.

**Operador AND (`&&`)**

| `a` | `b` | `a && b` |
|:---:|:---:|:---:|
| `true` | `true` | **`true`** |
| `true` | `false` | `false` |
| `false` | `true` | `false` |
| `false` | `false` | `false` |

**Operador OR (`||`)**

| `a` | `b` | `a \|\| b` |
|:---:|:---:|:---:|
| `true` | `true` | `true` |
| `true` | `false` | `true` |
| `false` | `true` | `true` |
| `false` | `false` | **`false`** |

**Operador NOT (`!`)**

| `a` | `!a` |
|:---:|:---:|
| `true` | `false` |
| `false` | `true` |

```java
public class OperadoresLogicos {
    public static void main(String[] args) {
        boolean a = true, b = false;

        System.out.println("a && b = " + (a && b)); // false
        System.out.println("a || b = " + (a || b)); // true
        System.out.println("!a = " + !a);           // false
    }
}
```

### 6.3. Combinación con operadores de comparación

Lo habitual es combinar los operadores lógicos con los de comparación para expresar condiciones compuestas:

```java
int edad = 20;
boolean tieneDni = true;
boolean esMiembro = false;

boolean puedeVotar = edad >= 18 && tieneDni;        // true
boolean tieneDescuento = edad < 25 || esMiembro;    // true
boolean esMenor = !(edad >= 18);                    // false
```

### 6.4. Comprobación de un valor dentro de un rango

Un caso de uso muy frecuente del operador `&&` es verificar si un valor se encuentra dentro de un intervalo, comprobando que es mayor o igual que el límite inferior **y** menor o igual que el límite superior:

```java
public class ValorDentroRango {
    public static void main(String[] args) {
        // Límites del rango definidos como constantes
        final var MINIMO = 0;
        final var MAXIMO = 5;

        var dato = 3;

        var estaDentroRango = dato >= MINIMO && dato <= MAXIMO;
        System.out.println("¿Está dentro del rango? " + estaDentroRango); // true
    }
}
```

> [!warning] Sintaxis de los rangos
> En Java no es posible encadenar comparaciones como en matemáticas. La expresión `0 <= dato <= 5` produce un error de compilación; debe escribirse `dato >= 0 && dato <= 5`.

### 6.5. Evaluación en cortocircuito

Los operadores `&&` y `||` se evalúan **en cortocircuito**: si el resultado de la expresión puede determinarse con el primer operando, el segundo **no llega a evaluarse**.

| Operador | Si el primer operando es… | Resultado | ¿Se evalúa el segundo? |
|---|---|---|---|
| `&&` | `false` | `false` | No |
| `\|\|` | `true` | `true` | No |

Este comportamiento mejora la eficiencia y, además, permite escribir condiciones seguras en las que la segunda comprobación solo tiene sentido si la primera se cumple:

```java
int divisor = 0;
// La división no se ejecuta porque la primera condición es false
boolean esValido = divisor != 0 && 10 / divisor > 2; // false, sin error
```

> [!tip] Orden de las condiciones
> En las expresiones con `&&` y `||` conviene colocar primero la condición que protege a las siguientes (por ejemplo, comprobar que un valor no es cero o no es `null`).

---

## 7. Precedencia y asociatividad de los operadores

### 7.1. Concepto

Cuando una expresión contiene varios operadores, la **precedencia** determina el orden en que se evalúan. La **asociatividad** establece el orden de evaluación entre operadores con la misma precedencia (habitualmente, de izquierda a derecha).

### 7.2. Tabla de precedencia

De **mayor** a **menor** precedencia:

| Nivel | Operadores | Descripción |
|:---:|---|---|
| 1 | `()` | Paréntesis |
| 2 | `++` `--` (post) | Postincremento y postdecremento |
| 3 | `++` `--` (pre), `+` `-` (unarios), `!` | Operadores unarios |
| 4 | `*` `/` `%` | Multiplicativos |
| 5 | `+` `-` | Aditivos |
| 6 | `<` `<=` `>` `>=` | Relacionales |
| 7 | `==` `!=` | Igualdad |
| 8 | `&&` | AND lógico |
| 9 | `\|\|` | OR lógico |
| 10 | `? :` | Ternario |
| 11 | `=` `+=` `-=` `*=` `/=` `%=` | Asignación (asociatividad de derecha a izquierda) |

### 7.3. Ejemplos

```java
int r1 = 2 + 3 * 4;      // 14 → la multiplicación se evalúa antes que la suma
int r2 = (2 + 3) * 4;    // 20 → los paréntesis alteran el orden
int r3 = 10 - 4 - 2;     // 4  → asociatividad de izquierda a derecha: (10 - 4) - 2

boolean r4 = true || false && false; // true → && se evalúa antes que ||
```

> [!tip] Buena práctica
> Ante la duda, conviene utilizar **paréntesis**. Además de garantizar el orden de evaluación deseado, hacen explícita la intención del programador y mejoran la legibilidad:
> ```java
> boolean accesoPermitido = (edad >= 18 && tieneEntrada) || esVip;
> ```

---

## 8. Ejemplo integrador

El siguiente programa determina si una persona puede acceder a una atracción de un parque, combinando operadores aritméticos, de comparación, lógicos y de asignación. Las condiciones de acceso son: tener una edad mínima **y** una altura mínima, **o** ir acompañado de un adulto.

```java
public class AccesoAtraccion {
    public static void main(String[] args) {
        final int EDAD_MINIMA = 12;
        final double ALTURA_MINIMA = 1.40;
        final double PRECIO_BASE = 20.0;

        int edad = 10;
        double altura = 1.45;
        boolean vaAcompanado = true;
        boolean esSocio = true;

        // Operadores de comparación y lógicos
        boolean cumpleRequisitos = edad >= EDAD_MINIMA && altura >= ALTURA_MINIMA;
        boolean puedeAcceder = cumpleRequisitos || vaAcompanado;

        // Operadores aritméticos y de asignación compuesta
        double precio = PRECIO_BASE;
        if (esSocio) {
            precio -= precio * 0.15; // descuento del 15 %
        }

        System.out.println("¿Cumple requisitos? " + cumpleRequisitos); // false
        System.out.println("¿Puede acceder? " + puedeAcceder);         // true
        System.out.println("Precio final: " + precio);                 // 17.0
        System.out.println("¿Edad par? " + (edad % 2 == 0));           // true
    }
}
```

> [!note] Estructura `if`
> La instrucción `if` del ejemplo ejecuta el bloque solo cuando la condición es verdadera. Se estudia en detalle en la [[06 Estructuras condicionales|Unidad 6]].

---

## 9. Resumen de la unidad

> [!summary] Ideas clave
> - Una **expresión** combina operandos y operadores y se evalúa a un único valor.
> - La **división entre enteros** descarta la parte decimal; para obtener un resultado decimal, al menos un operando debe ser `double`.
> - El operador **`%`** devuelve el resto de la división y permite, por ejemplo, comprobar la paridad (`n % 2 == 0`).
> - En **`++a`** la variable se incrementa antes de usarse; en **`a++`**, después.
> - Los operadores de **asignación compuesta** (`+=`, `-=`, `*=`, `/=`, `%=`) abrevian las operaciones sobre una misma variable.
> - Los operadores de **comparación** devuelven siempre un `boolean`. No hay que confundir `=` (asignación) con `==` (comparación).
> - **`&&`** exige que se cumplan todas las condiciones; **`||`**, al menos una; **`!`** invierte el valor lógico.
> - `&&` y `||` se evalúan **en cortocircuito**.
> - La **precedencia** determina el orden de evaluación; los **paréntesis** permiten modificarlo y aportan claridad.

---

**Navegación:** Anterior: [[03 Cadenas de texto|Unidad 3. Cadenas de texto]] · [[00 Índice|Índice]] · Siguiente: [[05 Entrada y salida|Unidad 5. Entrada y salida]]
