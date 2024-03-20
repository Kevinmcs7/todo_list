# Documentación sobre el todo_list en React

##### Introducción:
En el desarrollo de aplicaciones web con React.js, aprendí a utilizar funciones importantes para gestionar listas de tareas. Estas funciones, como agregar, eliminar, marcar como completadas y editar tareas, son esenciales para crear una experiencia de usuario interactiva y fluida.

## handelSubmit
La función `handleSubmit` maneja el evento de enviar un formulario. Su objetivo es tomar el valor ingresado en un campo de texto, crear un nuevo elemento de "todo" con este valor, y agregarlo a la lista de "todos" en la aplicación: esto fue lo que entendi sobre esta parte del trabajo, es decir es el apartado donde puedes agregar una nueva tarea. 
```jsx
function handleSubmit(e) {
  e.preventDefault(); // Evita el comportamiento predeterminado del evento
  let todo = document.getElementById('todoAdd').value; // Obtiene el valor del input
  const newTodo = {
    id: new Date().getTime(), // Genera un ID único basado en el tiempo actual
    text: todo.trim(),        // Establece el texto de la tarea, eliminando espacios en blanco iniciales y finales
    completed: false,         // Establece la tarea como no completada inicialmente
  };
  if (newTodo.text.length > 0) {
    setTodos([...todos].concat(newTodo)); // Agrega la nueva tarea al array de tareas
  } else {
    alert("Enter Valid Task"); // Muestra un mensaje de alerta si la tarea está vacía
  }
  document.getElementById('todoAdd').value = ""; // Limpia el valor del input después de agregar la tarea
}
```

## DeletoTodo
Este código se utiliza para eliminar una tarea de la lista de tareas. Recibe como argumento el ID de la tarea que se desea eliminar. Luego, crea una nueva matriz de tareas (updatedTodos) filtrando las tareas que no tienen el ID proporcionado. Finalmente, actualiza el estado de las tareas con la nueva matriz de tareas filtradas, eliminando así la tarea con el ID especificado.
```jsx
function deleteTodo(id) {
    // Crea una nueva matriz de tareas (updatedTodos) filtrando las tareas que no tienen el ID proporcionado
    let updatedTodos = [...todos].filter((todo) => todo.id !== id);    
    // Actualiza el estado de las tareas con la nueva matriz de tareas filtradas
    setTodos(updatedTodos);
}
```

## toggleComplete 
Este código se utiliza para cambiar el estado de completado de una tarea en la lista de tareas. Recibe como argumento el ID de la tarea que se desea cambiar. Luego, crea una nueva matriz de tareas (updatedTodos) mapeando todas las tareas existentes y modificando el estado de la tarea con el ID proporcionado. Finalmente, actualiza el estado de las tareas con la nueva matriz de tareas que incluye la tarea modificada.
```jsx
function toggleComplete(id) {
    // Crea una nueva matriz de tareas (updatedTodos) mediante el mapeo de todas las tareas existentes
    // Cambia el estado de la tarea con el ID proporcionado (completado o no completado)
    let updatedTodos = [...todos].map((todo) => {
        if (todo.id === id) { // Comprueba si la tarea tiene el ID proporcionado
            todo.completed = !todo.completed; // Cambia el estado de completado a no completado y viceversa
        }
        return todo; // Retorna la tarea actual, con o sin cambios
    });
    // Actualiza el estado de las tareas con la nueva matriz de tareas que incluye la tarea modificada
    setTodos(updatedTodos);
}
```

## submitEdits
Esta función se utiliza para aplicar los cambios realizados en la edición de una tarea. Recibe como argumento la nueva versión de la tarea editada. Luego, crea una nueva matriz de tareas (updatedTodos) mapeando todas las tareas existentes y actualizando el texto de la tarea si el ID coincide con el de la nueva tarea editada. Finalmente, actualiza el estado de las tareas con la nueva matriz de tareas que incluye la tarea editada y restablece el estado de edición de la tarea a null para indicar que la edición ha sido completada.
```jsx
function submitEdits(newtodo) {
    // Crea una nueva matriz de tareas (updatedTodos) mediante el mapeo de todas las tareas existentes
    const updatedTodos = [...todos].map((todo) => {
        // Si la tarea actual tiene el mismo ID que la nueva tarea editada,
        // actualiza el texto de la tarea con el valor del elemento HTML asociado al ID de la nueva tarea
        if (todo.id === newtodo.id) {
            todo.text = document.getElementById(newtodo.id).value;
        }
        return todo; // Retorna la tarea actual, con o sin cambios
    });
    // Actualiza el estado de las tareas con la nueva matriz de tareas que incluye la tarea editada
    setTodos(updatedTodos);
    // Restablece el estado de edición de la tarea a null, indicando que no hay tareas actualmente en proceso de edición
    setTodoEditing(null);
}
```

##### Conclusión
Ahora entiendo cómo estas funciones son componentes cruciales en la construcción de aplicaciones de gestión de tareas en React.js. Me di cuenta de cómo facilitan la interacción dinámica y efectiva con las listas de tareas, mejorando la usabilidad y funcionalidad general de la aplicación. Estas funciones son fundamentales para crear aplicaciones web interactivas y eficientes para la gestión de tareas.


