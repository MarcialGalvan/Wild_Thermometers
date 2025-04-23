# log de versiones.
# V0: Sin termometros.

La versión cero resuelve el problema sin termometros, es decir, considera solamente la ocupacion y no el "rellenado", con lo que ofrecera soluciones que no se ajustan a las normas, pero permitira tener un resolvedor en el que poner despues la restricciones.

*01* empiezo a usar PyGAD a ver si encuentra la solucion basica sin restricciones.
    Consigo que funcione perfecto, el truco fue en bajar la probabilidad de mutación, al principio trabajaba con mutaciones muy altas,  con lo que la convergencia se veia seriamente comprometida e iba a saltos. La baje, con 0.01 converge siempre a la solución exacta. 
    
*02* refactorizo la 01 antes de pasar a la versión con termómetros
    Demostrada la viabilidad, paso ahora a la version 1 en la que incluyo los temómetros.

# V1: Con termometros

en esta versión incluyo la existencia de los termometros. Esto va a cambiar, fundamentalmente, la función de fitness.  La condición es que se han de rellenar desde el bulbo inicial hasta el final, sin dejar huecos, como si fuera un tubo con fluido.

v11: no he logrado que converja, asi que voy a hacer cosas con la función de fitness, a ver si asi...
v12: cambio la funcion de costo por una exponencial, cada costo mas lejos cuesta muchisimo menos. a ver que pasa.
# V2: Diferential Evolution.

Con los geneticos no ha habido forma, no logro la convergencia mas alla de 5, asi que voy a probar con scipy y diferential evolution.

DE esta pensado para funciones continuas, he intentado adaptar la función de costo pero la forma que tiene de operar realmente dificulta el trabajar con el problema tal y como lo tengo definido.


# V3 Cambio el enfoque.
Paso de trabajar con el tablero a trabajar con los termómetros. 
Permite modelarlo de forma continua que luego discretizamos, asi que podre trabajar con diferential evolution.
Tiene que ajustar 35 variables, y no 144.
Con ese enfoque el espacio de busqueda es de 2,23007452e43. Estoy intentando encontrar la solución 


## Log de trabajo.
220806sa. 

Me acabo de dar cuenta de que la función de fitness tiene multiplicidad de soluciones, hay muchos cambios que conducen al mismo valor. ¿lo puedo mejorar?

Ha pasado la fecha, este ticket lo hemos perdido, pero algunos aprendizajes.

 1. Hemos refrescado la codificacion en python, usado librerias, pandas, scipy,... y el ajuste de algoritmos
 2. Hemos trabajado con Algoritmos genéticos y differential evolution.
 3. codificación de un problema complejo y busqueda de solución.
 4. funciono para un 4x4, claro que el de 12x12 tiene una explosión combinatoria asociada
 5. nos hemos quedado cerquita de la solución, tar cerca como 5 puntos de coste!
 

11.8.22 ju.
Lo retomo, he encontrado otro enfoque, trabajar con los termometros y no con el trablero. el ajuste continuo de 35 variables frente al discreto de. El espacio combinatorio es muuucho mas pequeño. mult 1 a t longitudes.
3^35 = 5,00315451e16
2^144 = 2,230074519853062e43

Bajamos 27 ordenes de magnitud el tamaño del espacio de busqueda.

