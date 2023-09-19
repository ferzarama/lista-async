const personas = {
  nombre: 'Pedro Peroni',
  edad: 39,
};

async function operacionAsincronica() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const exito = true;

      if (exito) {
        resolve('Operación exitosa. Pedro Peroni tiene 39 años:', personas);
      } else {
        reject('La operación falló.');
      }
    }, 4000);
  });
}

async function ejecutarOperacion() {
  try {
    const mensaje = await operacionAsincronica();
    console.log('Éxito:', mensaje);
  } catch (error) {
    console.error('Error:', error);
  }
}

ejecutarOperacion();



Con async y await:

Al utilizar async y await en la función ejecutarOperacion, la ejecución de la función se pausa en la línea que contiene await operacionAsincronica() hasta que la Promesa devuelta por operacionAsincronica se resuelva o rechace.
Durante esta espera, el hilo de ejecución no se bloquea, permitiendo que otras operaciones se realicen en paralelo.
Una vez que la Promesa se resuelve, la ejecución continúa y se imprime el mensaje de éxito o se maneja cualquier error que pueda haber ocurrido.
Con el método then():

Al utilizar el método .then() en la Promesa devuelta por operacionAsincronica, definimos dos funciones de callback: una para manejar el caso de éxito y otra para manejar cualquier error que ocurra durante la operación asíncrona.
Cuando la Promesa se resuelve, se ejecuta la función de éxito definida en .then().
Si la Promesa se rechaza, se ejecuta la función de error definida en .catch().
Diferencias entre async, await y el método then():

async y await permiten escribir código asíncrono de manera más similar al código síncrono, lo que mejora la legibilidad y mantenibilidad.
await pausa la ejecución de la función hasta que la Promesa se resuelva o rechace, pero no bloquea el hilo principal de ejecución.
El método .then() es parte de la API de Promesas y se utiliza para definir qué hacer cuando la Promesa se resuelve, mientras que .catch() se utiliza para manejar rechazos.
async funciones devuelven Promesas, lo que permite encadenar operaciones asincrónicas usando .then(). await solo se puede utilizar dentro de funciones declaradas con async.
