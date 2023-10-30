# Entrenar a la IA a jugar

## Reducir el número de neuronas

    Es posible reducir el número de neuronas necesarias para realizar el aprendizaje, sin embargo habría que hacer modificaciónes más complejas en el modelo de entrenamiento. Actualmente el modelo tiene dos neuronas de salida, lo que representa que el personaje el tiempo en tierra y el tiempo en aire, sin embargo, con una sola neurona de salida es posible realizar dicha acción. Puesto que la salida de la neurona puede ser interpretada como 1 = salta y 0 = no saltes.

    En la estructura del perceptrón, el arreglo pasa de tener dos neuronas de salida a una de la siguiente forma.

```` JavaScript
    // nnNetwork =  new synaptic.Architect.Perceptron(2, 6, 6, 2); //* Original
    nnNetwork =  new synaptic.Architect.Perceptron(2, 6, 6, 1);
    nnEntrenamiento = new synaptic.Trainer(nnNetwork);
````

    Además de modificar la estructura del perceptrón, es necesario modificar los paramatros de entrenamiento para que la red neuronal interprete correctamente la realización del salto. De manera que el código quedaría de la siguiente manera.

`````` JavaScript
    function datosDeEntrenamiento(param_entrada){

        //* Original (2 neuronas de salida) 
        // -------------------------------------------------------------------------
        // console.log("Entrada",param_entrada[0]+" "+param_entrada[1]);
        // nnSalida = nnNetwork.activate(param_entrada);
        // var aire=Math.round( nnSalida[0]*100 );
        // var piso=Math.round( nnSalida[1]*100 );
        // console.log("Valor ","En el Aire %: "+ aire + " En el suelo %: " + piso );
        // return nnSalida[0]>=nnSalida[1];
        // -------------------------------------------------------------------------

        console.log("Entrada",param_entrada[0]+" "+param_entrada[1]);
        nnSalida = nnNetwork.activate(param_entrada)
        var saltar = nnSalida>=0.5
        console.log("Valor único de salida: "+nnSalida+" Salta: "+saltar);
        return saltar
    }
``````

## Modificar el movimiento de la bala

Si el comportamiento de la bala disparada fuera como una funcion senoidal, sería necesario agregar más movilidades al personaje para que este pudiera esquivar la bala, ya sea que este tenga la facultada para agacharse, o que pueda moverse horizontalmente.

### Realizar el movimiento de la bala

Para programar el movimiento de la bala hay dos opciones

- Hacer una función senoidal de manera que dictamine el posicionamiento de la bala
- Mantener el movimiento rectilineo horizontal y agregar en el movimiento de la vala una iteración que haga que esta suba y baje.

### Modificaciones al entrenamiento de la IA

Lo primero que habría que modificar son las neuronas de entrada, ahora serían 3, una para tomar en cuenta la velocidad, otra para tomar en cuenta la posición en x y otra para tomar en cuenta la posición en Y,

Respecto a las neuronas de salida se necesitan 3, una para dictaminar si se debe saltar o no. Las otras dos neuronas seran la salida para indicar si debe hacer un movimiento horizontal y para determinar si se hace a la izquierda o derecha.
