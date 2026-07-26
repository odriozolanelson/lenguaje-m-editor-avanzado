¿Qué hace exactamente el bloque let...in en lenguaje M? ¿Por qué cada paso puede referenciar al anterior?

El bloque let...in define una secuencia de transformaciones que Power Query ejecuta de forma ordenada. Dentro de let, cada línea crea un paso con un nombre y almacena el resultado de una transformación. Finalmente, la cláusula in indica cuál de esos pasos será el resultado final de la consulta.

Cada paso puede referenciar al anterior porque el resultado obtenido queda almacenado como una variable. Esto permite construir una cadena de transformaciones donde cada operación utiliza como entrada el resultado del paso previo, facilitando la lectura, el mantenimiento y la modificación del código.

¿Por qué M es Case Sensitive y qué consecuencia práctica tiene? Da un ejemplo de un error que esto puede causar.

El lenguaje M es Case Sensitive, lo que significa que distingue entre mayúsculas y minúsculas. Por ello, un nombre debe escribirse exactamente igual cada vez que se utiliza.

Por ejemplo, si un paso se llama LimpiarEspacios y posteriormente se hace referencia a limpiarespacios, Power Query no encontrará ese identificador y la consulta generará un error. Lo mismo ocurre con los nombres de las columnas o con las funciones del lenguaje.

¿Cuál es la diferencia entre usar Text.Trim y Text.Clean en M?

La función Text.Trim elimina los espacios en blanco ubicados al principio y al final de un texto, pero conserva los espacios internos.

En cambio, Text.Clean elimina los caracteres no imprimibles o de control que pueden aparecer en un texto, como saltos de línea, tabulaciones u otros caracteres invisibles, sin modificar los espacios normales.

Por lo tanto, ambas funciones cumplen objetivos diferentes y, en muchos procesos de limpieza de datos, pueden utilizarse de manera complementaria.

¿Por qué filtraste los registros "PRUEBA" después de estandarizar la categoría y no antes?

Primero se estandarizó la columna categoria utilizando Text.Proper para unificar todas las variantes de escritura de un mismo valor, por ejemplo "prueba", "PRUEBA" o "Prueba". Una vez que todos los registros quedaron con el mismo formato, se aplicó el filtro para eliminar aquellos cuya categoría era **"Prueba"`.

Realizar el filtrado después de la estandarización hace que la condición sea más simple y evita dejar registros sin eliminar debido a diferencias en el uso de mayúsculas y minúsculas.
