# 🚀 Kanban Board - Sistema de Gestión de Tareas Colaborativo

## ✨ Descripción del Proyecto

**Kanban Board** es un sistema de gestión de tareas colaborativo estilo Kanban, construido con las últimas versiones de **Laravel (v12)**, **Livewire** y **Volt**. Permite a los usuarios organizar sus proyectos y equipos de manera eficiente, creando tableros personalizados, listas (columnas) y tarjetas (tareas). La aplicación facilita la colaboración en tiempo real, asignación de responsabilidades y seguimiento del progreso.

Este proyecto ha sido desarrollado siguiendo estrictas **buenas prácticas de codificación** (SOLID, DRY, PSR-12), utilizando **patrones de diseño modernos** de Laravel y enfocado en la modularidad y el rendimiento, con un enfoque en la experiencia de usuario dinámica gracias a Livewire, Volt y Alpine.js.

## 🌟 Funcionalidades Destacadas

* **Autenticación de Usuarios Robusta:** Registro, inicio de sesión y cierre de sesión seguro, gestionado por Laravel Fortify.
* **Gestión Completa de Tableros:**
    * Creación, visualización, edición y eliminación de tableros.
    * Asignación de un creador principal (`owner`).
* **Colaboración en Tableros:**
    * Capacidad de invitar a otros usuarios a un tablero específico.
    * Control de acceso basado en roles (`owner`, `collaborator`).
* **Organización con Listas:**
    * Creación, edición y eliminación de listas (columnas) dentro de cada tablero.
    * **Reordenamiento dinámico de listas (drag-and-drop) con Livewire.**
* **Gestión Detallada de Tarjetas (Tareas):**
    * Creación, visualización, edición y eliminación de tareas.
    * Asignación de título, descripción y fecha de vencimiento.
    * **Reordenamiento de tarjetas dentro de una lista (drag-and-drop) con Livewire.**
    * **Movimiento intuitivo de tarjetas entre diferentes listas (drag-and-drop) con Livewire**, reflejando el progreso del Kanban.
* **Experiencia de Usuario Dinámica:** Interacciones fluidas y en tiempo real sin recargar la página, gracias a la sinergia de **Laravel Livewire, Volt y Alpine.js**.

## 🛠️ Tecnologías Utilizadas

* **Backend:**
    * **Laravel v12:** El framework PHP para aplicaciones web.
    * **PHP 8.3+:** Lenguaje de programación.
    * **Laravel Fortify:** Para el scaffolding del backend de autenticación.
    * **Eloquent ORM:** Para la interacción con la base de datos.
    * **Laravel Migrations:** Para la gestión de esquemas de base de datos.
    * **Laravel Policies & Gates:** Para el control de acceso y autorización.
    * **Laravel Notifications:** Para futuras implementaciones de notificaciones por correo electrónico/otros canales.
    * **Laravel Queues:** Para el procesamiento de tareas en segundo plano.
* **Frontend:**
    * **Laravel Livewire v3:** Para la construcción de interfaces dinámicas con PHP, permitiendo gran interactividad sin JavaScript complejo.
    * **Laravel Volt:** La nueva sintaxis de Livewire que simplifica la creación de componentes de Blade y PHP en un solo archivo.
    * **Alpine.js:** Un framework JavaScript declarativo y reactivo para interacciones mínimas en el cliente.
    * **Blade Templates:** El motor de plantillas de Laravel.
    * **Tailwind CSS:** Framework CSS para un desarrollo de UI rápido y escalable.
* **Base de Datos:**
    * **MySQL 8+ / PostgreSQL / SQLite:** La base de datos relacional. (Configurable en `.env`)
* **Contenedorización:**
    * **Docker:** Para un entorno de desarrollo aislado y consistente.
    * **Laravel Sail:** La interfaz de línea de comandos ligera para Docker con Laravel.

## 📦 Requisitos del Sistema

* **Docker Desktop** (o Docker Engine en Linux) instalado y funcionando.
* **Composer** (si decides instalar dependencias PHP fuera del contenedor).
* **Git** (para clonar el repositorio).

## 🚀 Instalación y Uso (con Laravel Sail)

Sigue estos pasos para poner en marcha el proyecto en tu máquina local:

1.  **Clonar el Repositorio:**
    ```bash
    git clone [https://github.com/julian-dominguez/kanban-board.git](https://github.com/julian-dominguez/kanban-board.git)
    cd kanban-board
    ```

2.  **Configurar Variables de Entorno:**
    Copia el archivo de ejemplo `.env.example` a `.env`:
    ```bash
    cp .env.example .env
    ```
    Abre el archivo `.env` y ajusta las credenciales de tu base de datos si es necesario. Por defecto, Sail usa `mysql` y un usuario `sail` con contraseña `password`.

    * **Para SQLite (opción más rápida para desarrollo):**
      Cambia `DB_CONNECTION` a `sqlite` y elimina/comenta las otras líneas `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`. Luego, crea el archivo de base de datos:
        ```bash
        touch database/database.sqlite
        ```

3.  **Iniciar los Contenedores Docker con Sail:**
    Ejecuta el siguiente comando para construir e iniciar los servicios de Docker definidos en `docker-compose.yml`:
    ```bash
    ./vendor/bin/sail up -d
    ```
    * `up`: Inicia los contenedores.
    * `-d`: Ejecuta los contenedores en segundo plano (detached mode).

    Espera unos momentos mientras Docker descarga las imágenes y construye los contenedores.

4.  **Instalar Dependencias de Composer:**
    Una vez que los contenedores estén en marcha, instala las dependencias de PHP usando `Sail`:
    ```bash
    ./vendor/bin/sail composer install
    ```
    * **Nota:** Si encuentras errores de permisos, puedes intentar `sail artisan storage:link` y `sail down && sail up -d`.

5.  **Generar la Clave de la Aplicación:**
    ```bash
    ./vendor/bin/sail artisan key:generate
    ```

6.  **Ejecutar Migraciones de Base de Datos:**
    Esto creará las tablas necesarias en tu base de datos.
    ```bash
    ./vendor/bin/sail artisan migrate
    ```

7.  **Poblar la Base de Datos con Datos de Prueba (Opcional pero Recomendado):**
    Para tener algunos usuarios, tableros, listas y tareas de ejemplo:
    ```bash
    ./vendor/bin/sail artisan db:seed
    ```
    * **Credenciales de Usuario de Prueba:**
        * **Email:** `john@example.com`
        * **Contraseña:** `password`

8.  **Compilar Assets de Frontend:**
    Instala las dependencias de Node.js y compila los assets (Tailwind CSS, Livewire, Alpine.js):
    ```bash
    ./vendor/bin/sail npm install
    ./vendor/bin/sail npm run dev # Para desarrollo con hot-reloading
    # O ./vendor/bin/sail npm run build # Para producción
    ```

9.  **Acceder a la Aplicación:**
    La aplicación debería estar accesible en tu navegador en:
    `http://localhost`

## 👨‍💻 Demostración y Credenciales de Acceso

Para una demostración rápida de las funcionalidades, utiliza las siguientes credenciales para iniciar sesión:

* **Email:** `john@example.com`
* **Contraseña:** `password`

Una vez logueado, podrás explorar los tableros de ejemplo, crear los tuyos propios, añadir listas, tareas y probar las funcionalidades de arrastrar y soltar.

## ⚙️ Estructura del Código y Buenas Prácticas

Este proyecto está estructurado para demostrar un profundo entendimiento de las buenas prácticas de Laravel y patrones de diseño:

* **Separación de Responsabilidades (SOLID):**
    * Uso de **Form Requests** para la validación de datos de entrada en controladores, manteniendo la lógica limpia.
    * Controladores delgados, delegando la lógica de negocio a los modelos o, si fuera más complejo, a **Service Classes** (o "Actions").
* **Patrones de Autorización:** Implementación de **Laravel Policies y Gates** para un control de acceso granular y reutilizable a los recursos (ej. ¿Quién puede editar un tablero? ¿Quién puede mover una tarea?).
* **Eloquent ORM:** Uso eficiente de relaciones Eloquent (uno-a-muchos, muchos-a-muchos) y Query Scopes para consultas legibles y optimizadas.
* **Vistas con Livewire y Volt:** Construcción de componentes dinámicos con Livewire, aprovechando la sintaxis simplificada de Volt para la interactividad del tablero (arrastrar y soltar, edición inline) que demuestran una experiencia SPA-like sin la complejidad de un framework JavaScript completo.
* **Docker y Laravel Sail:** Entorno de desarrollo consistente y reproducible, facilitando la colaboración y el despliegue.
* **Code Styling (PSR-12):** El código sigue los estándares de codificación de PHP-FIG para alta legibilidad.
* **Manejo de Errores y Excepciones:** Errores controlados y mensajes amigables al usuario.
* **Optimización de Base de Datos:** Migraciones bien estructuradas con relaciones clave foránea.

## 🛑 Cómo Detener el Proyecto

Para detener los contenedores de Docker cuando hayas terminado de trabajar:
```bash
./vendor/bin/sail down
```
## 📄 Licencia
Este proyecto es de código abierto y está bajo la Licencia MIT.
