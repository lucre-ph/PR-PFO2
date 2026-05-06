# PR-PFO2
## Entrega 2 – Práctica Formativa Obligatoria

Este proyecto implementa un sistema **cliente-servidor en Python** utilizando **sockets** y una base de datos **SQLite**.  
El objetivo es aplicar conceptos de programación en red, modularización y gestión de datos persistentes, en el marco de la asignatura correspondiente.

---

## Objetivo del trabajo
- Desarrollar un sistema que permita la comunicación entre un cliente y un servidor.  
- Incorporar almacenamiento persistente mediante SQLite.  
- Analizar aspectos de seguridad y buenas prácticas en el manejo de información.  

---

## Estructura del repositorio
- `cliente.py`: script del cliente. Se conecta al servidor, envía mensajes y recibe respuestas.  
- `servidor.py`: script del servidor. Escucha conexiones, procesa solicitudes y accede a la base de datos.  
- `docs/`: documentación y archivos auxiliares.  
- `README.md`: este archivo.  

---

## Requisitos técnicos
- Python 3.10 o superior.  
- pip  

---

## Ejecución del sistema

### 1. Iniciar el servidor
```bash
python servidor.py
```

El servidor queda disponible en `http://127.0.0.1:5001`. La base de datos `tareas.db` se crea automáticamente al iniciar.

## Uso del cliente (consola)

Con el servidor corriendo, en otra terminal:

```bash
python3 cliente.py
```

El cliente muestra un menú interactivo para registrarse, iniciar sesión, y gestionar tareas.

---

## Endpoints

### `POST /registro`

Registra un nuevo usuario.

**Body JSON:**

```json
{ "usuario": "usuario123", "password": "1234" }
```

**Respuestas:**

- `201` — Usuario registrado exitosamente.
- `409` — El usuario ya existe.
- `400` — Faltan campos o no cumplen el largo mínimo.

---

### `POST /login`

Verifica las credenciales de un usuario.

**Body JSON:**

```json
{ "usuario": "usuario123", "password": "1234" }
```

**Respuestas:**

- `200` — Credenciales válidas.
- `401` — Credenciales inválidas.

---

### `GET /tareas` _(requiere autenticación)_

Muestra las tareas del usuario autenticado.

- Desde el **navegador** (con Basic Auth): devuelve una página HTML de bienvenida con la lista de tareas.
- Desde el **cliente**: devuelve JSON.

Si no se envían credenciales, se muestra un mensaje de error indicando que el usuario no está logueado.

### `POST /tareas` _(requiere autenticación)_

Crea una nueva tarea para el usuario autenticado.

**Body JSON:**

```json
{ "descripcion": "tarea mia" }
```

**Respuestas:**

- `201` — Tarea creada, devuelve el `id` asignado.
- `400` — Descripción vacía o ausente.

### `DELETE /tareas/<id>` _(requiere autenticación)_

Elimina una tarea del usuario autenticado por su `id`.

**Respuestas:**

- `200` — Tarea eliminada.
- `404` — Tarea no encontrada o no pertenece al usuario.



### ¿Por qué hashear contraseñas?
Constituye una práctica esencial en el ámbito de la seguridad informática, que consiste en aplicar una función criptográfica que transforma la contraseña original en una cadena irreconocible e irreversible. De esta manera, incluso si la base de datos fuera comprometida, los atacantes no podrían recuperar las contraseñas reales de los usuarios.
Evita el almacenamiento de contraseñas en texto plano, protegiendo la información ante accesos no autorizados o fugas de datos.

### Ventajas de usar SQLite
- Portabilidad: toda la información se almacena en un solo archivo, fácilmente transportable.
- Simplicidad: no requiere instalación ni configuración de un servidor externo.
- Eficiencia: excelente rendimiento para volúmenes de datos moderados.
- Compatibilidad: integrada en Python mediante el módulo estándar sqlite3.


## Pruebas:  
### Menú principal:
<img width="576" height="278" alt="image" src="https://github.com/user-attachments/assets/d4b20835-cc69-4cbf-a804-2a214aa35895" />

### Registro de usuario:  
<img width="560" height="335" alt="image" src="https://github.com/user-attachments/assets/ad19cc04-8076-4c3d-b7d7-d65a65ad399e" />

### Inicio de sesión (usuario ya registrado):  
<img width="581" height="350" alt="image" src="https://github.com/user-attachments/assets/4ead0708-eb71-49c7-a5d4-0955ffa7db5f" />

### Inicio de sesión (usuario no registrado):  
<img width="601" height="325" alt="image" src="https://github.com/user-attachments/assets/932dad8a-8103-4389-92f4-700a43ecbfa4" />

### Ver mis tareas (no registrado):
<img width="511" height="260" alt="image" src="https://github.com/user-attachments/assets/796a1b4f-3d41-4fea-a798-616f28ce647b" />

### Ver mis tareas (registrado):
<img width="624" height="321" alt="image" src="https://github.com/user-attachments/assets/ab3d2910-b965-4447-86e2-f77753dc7583" />

### Cerrar sesión:  
<img width="606" height="284" alt="image" src="https://github.com/user-attachments/assets/c13cf7f0-3e84-47e7-84fd-9af8b341cf6e" />

### Salir:  
<img width="603" height="228" alt="image" src="https://github.com/user-attachments/assets/0cbe9a1f-e1a7-4906-a650-9f7bb5ebe98c" />
