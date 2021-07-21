# Rocketbot

  La webpage consta de dos páginas, una con un formulario en el que usuario se tiene que registrar, otra con los datos cuando completa el registro.
 Para guardar los datos, y que persistan al refrescar o reabrir la página, los almacené en Local Storage con el plugin https://www.npmjs.com/package/local-storage.
 En él también hay un booleano que indica si hay un usuario logeado.
 Al registrarse el usuario es inmediatamente llevado a la página con sus datos. Ésta tiene un botón para desloguearse, lo que vacía el Local Storage y devuelve a la página del formulario.
