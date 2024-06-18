# DESAFÍO ENTREGABLE - Cuarta práctica integradora - Coderhouse/Backend

Este repositorio contiene el desafío "Cuarta práctica integradora" con las siguientes características:

## Ruta /api/users/premium/:uid

- La ruta suelta /api/users/premium/:uid fue movida a un router específico para usuarios en /api/users/

<small>Directorio/s de referencia</small>

- `/src/components/users/index.js`: Rutas de users.
- `/src/components/users/usersController/usersController.js` : Controlador de users.
- `/src/components/users/usersServices/usersServices.js`: Servicios de users.

### - Ruta /api/users/premium/:uid

https://github.com/lisandrojm/desafio_cuarta_practica_integradora/assets/35199683/23b48dbb-886b-479d-a3a3-bf005af42e63

## Modelo de User

- El modelo de User cuenta con una nueva propiedad “documents” la cual es un array que contiene los objetos con las siguientes propiedades:

  - name: String (Nombre del documento).
  - reference: String (link al documento).

- Se agregó la propiedad “last_connection”, la cual se modifica cada vez que el usuario realiza un proceso de login y logout

<small>Directorio/s de referencia</small>

- `/src/models/users.js`: Modelo de users.

## Endpoint /api/users/:uid/documents

- Endpoint creado en el router de usuarios api/users/:uid/documents con el método POST que permite subir uno o múltiples archivos.

<small>Directorio/s de referencia</small>

- `/src/components/users/index.js`: Rutas de users.
  - Ruta:
    - /api/users/:uid/documents
- `/src/components/users/usersController/usersController.js` : Controlador de users.
- `/src/components/users/usersServices/usersServices.js`: Servicios de users.

## Middleware de Multer

- Se utiliza el middleware de Multer para poder recibir los documentos que se cargan desde router de usuarios api/users/:uid/documents y actualizar en el usuario su status para hacer saber que ya subió algún documento en particular.

- El middleware de multer fue modificado para que pueda guardar en diferentes carpetas los diferentes archivos que se suban.

  - Si se sube una imagen de perfil lo guarda en la carpeta profiles.
  - En caso de recibir una imagen de producto lo guarda en la carpeta products.
  - Ahora al cargar un documento, lo guarda en la carpeta documents.

<small>Directorio/s de referencia</small>

- `/src/utils/multer/multer.js` Configuración del middleware de Multer.

## Endpoint /api/users/premium/:uid

- El /api/users/premium/:uid fue modificado para que sólo actualice al usuario a premium si ya ha cargado los siguientes documentos:
  - Identificación.
  - Comprobante de domicilio.
  - Comprobante de estado de cuenta
- En caso de llamar al endpoint, si no se ha terminado de cargar la documentación, se devuelve un error indicando que el usuario no ha terminado de procesar su documentación. (Esto sucede sólo si quiere pasar de user a premium, no al revés)

---

## Requisitos

Asegúrate de tener los siguientes requisitos instalados en tu entorno de desarrollo:

- Node.js
- MongoDB
