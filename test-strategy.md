# Test strategy for "Adivina tu número" game

## Objetivo
El objetivo de las pruebas es asegurar el correcto funcionamiento, validación de entradas del usuario y la lógica de negocio del juego "Adivina tu número".

## Alcance
El juego consiste en adivinar un número entre 1 y 100 proporcionando al usuario una retroalimentación en cada intento, y tener un máximo de 10 intentos permitidos.

## Tipos de pruebas realizadas
1. **Pruebas funcionales**: Para verificar que la lógica del juego funcione como se espera.
2. **Pruebas de límite**: Para testear los límites del rango de números (1-100) asegurando que no se acepten números fuera de éste rango.
3. **Pruebas de validación**: Para comprobar que únicamente se acepten números enteros como entrada.
4. **Pruebas de interfaz de usuario**: Para asegurar la correcta visualización de mensajes y retroalimentar al jugador.
5. **Pruebas de regresión**: Para garantizar que cualquier cambio no afecte la funcionalidad existente.

## Escenarios de prueba

### 1. Validación de entradas (Números enteros)
- **Caso de prueba 1.1:** Ingresar un número entero válido (dentro del rango 1-100).  
  **Esperado:** El número se evalúa correctamente.
- **Caso de prueba 1.2:** Ingresar un valor no entero (texto o número decimal).  
  **Esperado:** Mostrar alerta y no contar el intento.
- **Caso de prueba 1.3:** Ingresar un número fuera del rango (menor que 1 o mayor que 100).  
  **Esperado:** Mostrar alerta y no contar el intento.

### 2. Comportamiento del juego según el número ingresado
- **Caso de prueba 2.1:** El número ingresado es mayor al número a adivinar.  
  **Esperado:** Mostrar "El número es menor!" en color negro.
- **Caso de prueba 2.2:** El número ingresado es menor al número a adivinar.  
  **Esperado:** Mostrar "El número es mayor!" en color negro.

### 3. Límite de intentos
- **Caso de prueba 3.1:** Después de 10 intentos fallidos.  
  **Esperado:** Mostrar "!!!Pérdistes!!!" en color rojo.

### 4. Victoria del jugador
- **Caso de prueba 4.1:** El jugador adivina el número antes de 10 intentos.  
  **Esperado:** Mostrar "Felicitaciones! adivinaste el número!" en color verde.

### 5. Reinicio del juego
- **Caso de prueba 5.1:** El juego debe reiniciarse correctamente después de completar una ronda (victoria o derrota).  
  **Esperado:** Se reinicia el número aleatorio y los intentos.

## Errores encontrados con sus respectivas soluciones

### 1. Cálculo incorrecto del número aleatorio
- **Error:** El número aleatorio generado estaba fuera del rango (0-10 en lugar de 1-100).
- **Solución:** Se corrigió el cálculo a `Math.floor(Math.random() * 100) + 1` para ajustarse al rango adecuado.

### 2. Validación de entrada faltante para números enteros
- **Error:** No se realizaba ninguna validación para verificar si el número ingresado era un entero.
- **Solución:** Se agregó una validación para mostrar una alerta cuando el número ingresado no sea un entero y evitar que el intento sea contabilizado.

### 3. Lógica de los mensajes de victoria/derrota invertida
- **Error:** Los mensajes de victoria ("Felicitaciones!") y derrota ("!!!Pérdistes!!!") estaban invertidos.
- **Solución:** Se corrigió la lógica para mostrar el mensaje correcto según si el jugador gana o pierde.

### 4. Errores tipográficos en las funciones de eventos
- **Error:** El evento `addeventListener` estaba mal escrito.
- **Solución:** Se corrigió a `addEventListener`.

### 5. Uso incorrecto de constantes (cantidad de intentos)
- **Error:** El número máximo de intentos estaba configurado en 5 en lugar de 10.
- **Solución:** Se corrigió el valor de la constante `ATTEMPTS` a 10.

### 6. Referencias incorrectas a elementos del DOM
- **Error:** La variable `lowOrHi` estaba mal referenciada con `querySelector('lowOrHi')`.
- **Solución:** Se corrigió a `querySelector('.lowOrHi')`.


## Conclusión
Los escenarios anteriores asegurarán una cobertura completa de la funcionalidad del juego desde la validación de entradas hasta la mecánica del juego.
