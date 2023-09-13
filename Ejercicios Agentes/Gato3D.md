# Gato en 3D

Estableciendo un mapa de gato de tres niveles generar una IA que nunca pierda.

## Gato Normal

### Secuencia de Percepción

- Se juega por turnos
- Se debe formar una línea recta de 3 simbolos iguales antes que el rival
- La línea puede formase de manera horizontal vertical o diagonal
- No puede haber más de un simbolo por casilla
- Solo se puede colocar un simbolo por turno

### Medidas de Rendimiento

- Número de movimientos requeridos para formar una línea recta
- Número de bloqueos al rival

### Estrategia de Victoria

#### Primer turno es propio

- 1er Turno: Tomar una de las equinas
- 2do Turno: Si la orilla contraria esta disponible después del turno del rival fichar en esa casilla. En caso contrario fichar en el centro.

3er Turno en adelante

- Si el rival no bloquea la linea fichar para ganar.
- Si el rival si ha bloqueado, verificar que no tenga jugadas para ganar y bloquearlas.
- Buscar fichar donde exista más de una linea para conectar

#### Primer turno es del oponente

- 1er turno: Tomar el centro
- 2do turno: Si el rival puede completar la linea, bloquear la casilla, en caso contrario, fichar una de las casillas centrales de los bordes

3er Turno en adelante

- Si el rival no bloquea para completar la linea, fichar la casilla que complete la línea.
- Si el rival puede generar una linea bloquearla

## Gato 3D

### Secuencia de  Precepción

- Se juega por turnos
- Se debe formar una líena recta de 3 simbolos iguales antes que el rival
- La línea puede ser formada de manera horizontal, vertical o diagonal en los ejes **x**, **y** y **z**
- No puede haber más de un simbolo por casilla
- Solo se puede colocar un simbolo por turno

### Medidas de  Rendimiento

- Número de movimientos requeridos para formar una línea recta
- Número de bloqueos al rival

### Estrategia de  Victoria

#### El primer turno es mío

- 1er turno: Tomar el centro
- 2do turno: Tomar una esquina en un nivel superior o inferior

3er Turno en adelante

- Si se puede completar una linea, fichar para ganar
- Si el rival puede completar una linea bloquearla
- Fichar en la casilla que genere una intersección entre las fichas anteriormente colocadas.

#### El primer turno es del rival

- 1er turno: Si el centro esta disponible ficharlo, en caso contrario fichar en paralelo al rival.
- 2do turno: Si el rival puede completar una línea bloquearla, en caso contrario fichar en paralelo a una de las fichas del rival

3er turno en adelante

- Si se puede fichar para completar una línea, completar la línea
- Si el rival puede completar una línea bloquearla
- Buscar fichar en donde se puedan generar múltiples opciones para completar la línea.
