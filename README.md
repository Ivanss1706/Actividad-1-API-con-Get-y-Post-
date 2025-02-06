# API REST de Gestión de Usuarios con FastAPI y Pydantic (Ejemplo Básico)

Este código proporciona un ejemplo básico de una API REST para la gestión de usuarios utilizando FastAPI y Pydantic en Python.

## Configuración Inicial

* Se utiliza el framework FastAPI para crear la API REST.
* Se define un modelo de datos `User` con Pydantic, que incluye los siguientes campos (basados en datos de ejemplo del Titanic):
    * `PassengerId` (int): Identificador único del pasajero.
    * `Survived` (bool): Indica si el pasajero sobrevivió (True) o no (False).
    * `Pclass` (int): Clase del billete (1, 2 o 3).
    * `Name` (str): Nombre del pasajero.
    * `Sex` (str): Sexo del pasajero.
    * `Age` (int, opcional): Edad del pasajero.

## Base de Datos Temporal

* Se utiliza una lista en memoria para almacenar los usuarios. **Importante:** Los datos se pierden al reiniciar el servidor.
* Se precargan 25 usuarios de ejemplo (datos del Titanic) en la lista.

## Endpoints Principales

* **`GET /usersclass/`**: Devuelve una lista con todos los usuarios.
* **`GET /usersclass/{id}`**: Busca un usuario por su `PassengerId` (Path parameter).
* **`GET /usersclass/?id=`**: Busca un usuario por su `PassengerId` (Query parameter). **Advertencia:** Este endpoint genera un conflicto con el anterior, ya que ambos utilizan la misma ruta base (`/usersclass/`).
* **`POST /usersclass/`**: Crea un nuevo usuario. Se valida que el `PassengerId` no exista previamente.

## Funcionalidades Clave

* **Validación de Datos:** Pydantic realiza la validación automática de los datos de entrada según el modelo `User`.
* **CRUD Básico:** Implementación básica de las operaciones Create y Read (Crear y Leer) para la gestión de usuarios.
* **Manejo de Errores:** Se incluyen manejos de errores sencillos para IDs no existentes.


## Uso Típico

* **Consultar todos los usuarios:** `GET http://localhost:8000/usersclass/`
* **Buscar usuario específico (Path parameter):** `GET http://localhost:8000/usersclass/5`
* **Crear usuario:** `POST http://localhost:8000/usersclass/` (con un cuerpo JSON que cumpla con el modelo `User`)
