---
title: "Contact Me"
layout: staticpage
---

<style>
  /* Estilos para el formulario */
  form {
    width: 500px; /* Ancho del formulario */
    margin: 0 auto; /* Centramos el formulario */
  }

  /* Estilos para los campos del formulario */
  input, textarea {
    width: 100%; /* Hacemos que los campos ocupen todo el ancho del formulario */
    padding: 12px 20px; /* Espacio interno para los campos */
    box-sizing: border-box; /* Ajustamos el tamaño de los campos a su contenido */
    border: 2px solid #ccc; /* Borde delgada y gris para los campos */
    border-radius: 4px; /* Esquinas redondeadas para los campos */
    font-size: 16px; /* Tamaño de la fuente para los campos */
    color: #333; /* Color de la fuente para los campos */
  }

  /* Estilos para el botón de envío */
  input[type="submit"] {
    width: 100%; /* Hacemos que el botón ocupe todo el ancho del formulario */
    background-color: #333; /* Color de fondo para el botón */
    color: #fff; /* Color de la fuente para el botón */
    font-size: 18px; /* Tamaño de la fuente para el botón */
    padding: 12px 20px; /* Espacio interno para el botón */
    border: none; /* Sin borde para el botón */
    border-radius: 4px; /* Esquinas redondeadas para el botón */
    cursor: pointer; /* Puntero del mouse al pasar por encima del botón */
  }
</style>

<!-- Formulario de contacto -->
<form>
  <!-- Campo para el nombre -->
  <label for="name">Name:</label><br>
  <input type="text" id="name" name="name"><br>

<!-- Campo para el código del país -->
<label for="country-code">Phone Country code:</label><br>
<input type="text" id="country-code" name="country-code" placeholder="51"><br>

<!-- Campo para el número de celular con código del país -->
<label for="phone">Phone Number:</label><br>
<input type="tel" id="phone" name="phone" placeholder="XXX XXX XXXX"><br>

  <!-- Campo para el correo electrónico -->
  <label for="email">Email:</label><br>
  <input type="email" id="email" name="email"><br>

  <!-- Campo para el mensaje -->
  <label for="message">Message:</label><br>
  <textarea id="message" name="message" rows="5" maxlength="500"></textarea><br>

  <!-- Botón de envío -->
  <input type="submit" value="Enviar">

</form>

<script>
  // Obtenemos el formulario
  const form = document.querySelector('form');

  // Agregamos un manejador de eventos para el evento submit del formulario
  form.addEventListener('submit', function(event) {
    // Prevenimos el comportamiento por defecto del formulario (recargar la página)
    event.preventDefault();

    // Obtenemos los datos del formulario
    const data = new FormData(form);
 
    // Creamos una solicitud HTTP POST hacia el script que procesará la información del formulario
    const request = new XMLHttpRequest();
    request.open('POST', 'http://144.22.34.252/blog/receive_message');
    request.send(data);

    // Cuando la solicitud termine, verificamos si el servidor ha devuelto una respuesta positiva
    request.addEventListener('load', function() {
      if (request.status === 200) {
        // Si el servidor ha devuelto una respuesta positiva, mostramos un mensaje de éxito al usuario
        alert('¡Formulario enviado correctamente!');
      } else {
        // Si el servidor ha devuelto una respuesta negativa, mostramos un mensaje de error al usuario
        alert('¡Error al enviar el formulario!');
      }
    });
  });
</script>



