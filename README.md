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
- Bibliotecas estándar: `socket`, `sqlite3`, `threading`.  

---

## Ejecución del sistema

### 1. Iniciar el servidor
```bash
python servidor.py


### ¿Por qué hashear contraseñas?
Constituye una práctica esencial en el ámbito de la seguridad informática, que consiste en aplicar una función criptográfica que transforma la contraseña original en una cadena irreconocible e irreversible. De esta manera, incluso si la base de datos fuera comprometida, los atacantes no podrían recuperar las contraseñas reales de los usuarios.
Evita el almacenamiento de contraseñas en texto plano, protegiendo la información ante accesos no autorizados o fugas de datos.

### Ventajas de usar SQLite
- Portabilidad: toda la información se almacena en un solo archivo, fácilmente transportable.
- Simplicidad: no requiere instalación ni configuración de un servidor externo.
- Eficiencia: excelente rendimiento para volúmenes de datos moderados.
- Compatibilidad: integrada en Python mediante el módulo estándar sqlite3.
