![logo](https://github.com/cyanproject/cyan/blob/58a38f5a04b562c8136d28cd4d1b114a08ee2377/logo-350x350.png)
# Cyan
Librería JavaScript para crear ventanas movibles.

## Uso

Descarga el archivo *cyan-1.0.0.js* (o la versión que corresponda) y añádelo a tu proyecto en la sección **`<head>`** del *index.html*, y escribe funcionalidades en ventanas con Cyan y JavaScript entre etiquetas **`<script></script>`**. También puedes escribir el código de cada ventana o componente en archivos *.js* y luego importarlos dentro de esas etiquetas.

Se recomienda que cada documento o componente se escriba en un archivo aparte, para lograr una estructura clara que ayude a la actualización del software, y permita su reutilización en otros proyectos. Los documentos son similares a las ventanas tradicionales: se pueden mover, organizar, cerrar u ocultar. También se pueden crear componentes sin asociarse a un documento, como por ejemplo, una barra de menús.

**cyan.Begin()**

Esta sentencia inicializa Cyan, mostrando por defecto la mesa 0 y una barra de herramientas para gestionar los documentos. Las mesas son espacios donde puedes organizar grupos de ventanas, y no interfieren con el resto de tu aplicación web. A partir de esta instrucción, puedes escribir, por ejemplo, *AddDocument* para crear un nuevo documento, y luego, dentro de él, puedes escribir sentencias como *AddButton*, *AddLabel*, etc, para crear objetos de la interfaz de usuario.

Si escribes esta sentencia con el parámetro cyan.Begin(cyan.Const.DarkMode), las ventanas cambiarán a modo oscuro.

### Características:

- Multitarea: las funcionalidades de las aplicaciones pueden programarse en documentos que el usuario puede abrir conjuntamente, permitiéndole trabajar en distintas tareas al mismo tiempo. Si se tiene un monitor de alta resolución ultra wide, se podría aprovechar mejor esta capacidad.
  
- Rapidez: los documentos se muestran al usuario instantáneamente, pues ya se descargaron en segundo plano. Esta descarga se realiza en segundo plano pero secuencialmente, brindando un control preciso sobre los componentes.

- Cada documento puede escribirse en un archivo con la interfaz de usuario, datos y métodos, como un componente completo para mejorar la organización y reutilización.

- No se requiere crear funciones de eventos. Estos están listos para ser programados en funciones como: function NombreObjeto_OnNombreEvento() { tu código... }

- Pueden escribirse componentes que no se referencian entre sí ni a sus objetos, para lograr componentes completamente reutilizables. Esto se puede conseguir porque cada objeto dispone de un método *Talk* a través del cual emitir mensajes "al aire", y un método *Listen* que escucha a los demás. Así, los componentes pueden comunicarse y actuar a mensajes específicos que escuchen.

- Se incluye validación de datos automática, como enteros, reales, rangos, alfanuméricos, etc.

- El usuario dispone de una barra de herramientas para organizar sus documentos como desee. Por ejemplo, puede reordenar las ventanas en la pantalla, o llevar grupos a mesas distintas para trabajar ordenado.


### ¡Hola mundo!

El siguiente código crea un documento con el clásico saludo *¡Hola mundo!* Aunque pudo haberse escrito el código en el mismo archivo *index.html*, se prefirió escribir el documento en el archivo *DocHolaMundo.js* para ilustrar el uso de componentes, que se cargan con la sentencia **cyan.LoadComponent()**. Notará el uso de algunas constantes de posición de Cyan, como por ejemplo, cyan.Col5, y de otras de tamaño, como por ejemplo, cyan.B4W. Estas y otras constantes las ofrece Cyan para facilitar el desarrollo y no tener que estar especificando números.

La función *ComponentDocHolaMundo_OnLoaded()* se ejecuta cuando el componente completa su carga, por eso se escribió ahí que en ese momento se muestre el documento en pantalla (con la sentencia *Bring()*). También podría mostrarse en pantalla un documento al pulsar un botón, seleccionar una opción de un menú, etc.

![holamundo](https://github.com/cyanproject/cyan/blob/0a2f2590ef1b307687ab783733530ea033a7c5b2/hola-mundo.png)

Archivo: index.html
```
<!DOCTYPE html>
<head>
    <script type="text/javascript" src="./cyan-1.0.0.js"></script>
</head>
<body>
    <h1>¡Hola mundo!</h1>

    <script>
        cyan.Begin()
        cyan.LoadComponent("DocHolaMundo.js")
    </script>
</body>
</html>
```

Archivo: DocHolaMundo.js
```
cyan.AddDocument(cyan.Col5, cyan.Row3, cyan.B4W, cyan.B4H, 'Documento Hola mundo', 'DocHolaMundo')
DocHolaMundo.AddLabel(cyan.Col2, cyan.Row2, '¡Hola mundo!')

function ComponentDocHolaMundo_OnLoaded() {
    DocHolaMundo.Bring()
}
```
---

**Manual de usuario**

El manual de usuario con el detalle de todos los comandos para crear objetos, así como los métodos de cada uno, la lista de constantes y otros objetos que ofrece Cyan y cómo modificar la interfaz de usuario, comenzará prontamente a ser escrito.
Por ahora, se indica en la siguiente sección los comandos para crear objetos en la pantalla (o en las mesas número *z*).

## Sentencias para crear objetos

cyan.AddDocument(x: number, y: number, width: number, height: number, caption: string, id: string)

cyan.AddCanvas(x: number, y: number, z: number, width: number, height: number, id: string)

cyan.AddBox(x: number, y: number, z: number, width: number, height: number, borderWidth: number, borderColor: string, fillColor: string, id: string)

cyan.AddEllipse(x: number, y: number, z: number, width: number, height: number, borderWidth: number, borderColor: string, fillColor: string, id: string)

cyan.AddLabel(x: number, y: number, z: number, caption: string, id: string)

cyan.AddTextBox(x: number, y: number, z: number, caption: string, id: string)

cyan.AddButton(x: number, y: number, z: number, caption: string, id: string)

cyan.AddImage(x: number, y: number, z: number, width: number, height: number, imageFile: string, caption: string, id: string)

cyan.AddVideo(x: number, y: number, z: number, width: number, height: number, videoFile: string, autoPlay: boolean = false, id: string)

cyan.AddCheckBox(x: number, y: number, z: number, caption: string, id: string)

cyan.AddRadioButtonGroup(x: number, y: number, z: number, id: string)

cyan.AddComboBox(x: number, y: number, z: number, id: string)

cyan.AddFile(x: number, y: number, z: number, id: string)

cyan.AddApi(id: string)

cyan.AddChronometer(id: string)

cyan.AddTimer(hours: number, minutes: number, seconds: number, centiseconds: number, id: string)

cyan.AddDiv(x: number, y: number, z: number, width: number, height: number, borderWidth: number, borderColor: string, fillColor: string, id: string)

cyan.AddMenuBar(x: number, y: number, z: number, id: string)

cyan.AddPulldownMenu(id: string)

**Notas**

- El parámetro *z* corresponde al número de mesa donde se creará el objeto, en las coordenadas *x* e *y*. La mesa mostrada al inicio es la 0.
- Cuando se añade un objeto a un documento, no se debe especificar el parámetro *z*, porque su valor siempre será el que tenga el propio documento; además, en lugar de comenzar la sentencia con "cyan.", debes usar simplemente el nombre del documento. Por ejemplo: DocHolaMundo.AddLabel(cyan.Col2, cyan.Row2, '¡Hola mundo!')

---

## PARTICIPACIÓN

Este proyecto es open source, y queda disponible a la comunidad tanto para su uso como para participar activamente, sea proponiendo y programando nuevas características, escribiendo el manual, realizando pruebas, difundiendo o aportando ideas. Todos son bienvenidos.

**Para colaborar desarrollando:**

Toma uno de los issues (puedes proponer nuevos) y crea una rama para desarrollarlo editando el archivo *cyan-1.0.0.ts* (o la versión que corresponda). Cuando termines, realiza un Pull Request. Ya luego subiremos una nueva versión tanto del archivo .ts como de la librería minificada para su uso.

Muchísimas gracias.

# Licencia

[MIT](https://opensource.org/licenses/MIT)

Copyright (c) 2025, Gabriel Lucero
