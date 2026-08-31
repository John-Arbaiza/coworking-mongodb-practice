# coworking-mongodb-practice
Repositorio de aprendizaje práctico de MongoDB basado en un caso de uso realista: la gestión de un coworking.

> Nota: Este proyecto no pretende ser una aplicación de producción  ni una plantilla de arquitectura. Su objetivo principal es para aprender MongoDB mediante la práctica y documentar el proceso de aprendizaje.

## 🎯 Objetivo
Aprender MongoDB desde cero de forma progresiva, aplicando cada concepto sobre un mismo dominio de datos en lugar de utilizar ejemplos aislados.

El dominio elegido es la gestión de un coworking, que permite trabajar progresivamente con entidades como:

- Departamentos
- Puestos de trabajo
- Usuarios
- Espacios
- Reservas

La idea es que el modelo evolucione a medida que aparecen nuevos conceptos de MongoDB

## 🧠 ¿Por qué la estructura está organizada por conceptos?
En un proyecto de software tradicional, probablemente organizaríamos el código por dominio o por capas:

```
models/
services/
controllers/
routes/
...
```

Este repositorio tiene un propósito diferente.

Cada carpeta dentro de src/ representa un concepto de MongoDB, siguiendo aproximadamente el orden en el que se aprende.

## 🚀 Cómo ejecutar el proyecto

### Requisitos
* Docker
* Docker Compose
* MongoDB for VS Code
* Extensión de MongoDB para VS Code

### 1. Configurar las variables de entorno

**Crea un archivo `.env` a partir del ejemplo incluido:**
```bash
cp .env.example .env
```

Configura las credenciales de MongoDB según corresponda.

### 2. Iniciar MongoDB

```bash
docker compose up -d
```

Esto iniciará la instancia de MongoDB definida en `docker-compose.yml`.

## 🛠️ Stack

- **MongoDB 8.0** — base de datos utilizada para los ejercicios.
- **Docker / Docker Compose** — ejecución local de MongoDB.
- **MongoDB for VS Code** — ejecución de consultas y Playgrounds.
- **Archivos `.mongodb`** — scripts y ejercicios prácticos.

