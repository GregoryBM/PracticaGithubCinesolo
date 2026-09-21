# 🎬 Despliegue de Aplicación Web de Cine con Docker y Nginx

Guía para desplegar localmente una aplicación web de gestión y venta de entradas de cine utilizando **Nginx** dentro de un contenedor Docker.

---

## 📋 Prerrequisitos

Antes de empezar, asegúrate de tener instalados los siguientes programas:

- [Git](https://git-scm.com/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Un navegador web, como Chrome, Firefox o Edge

---

## 🛠️ Despliegue paso a paso

### 1. Obtener el código fuente

Clona el repositorio en tu equipo y accede a la carpeta del proyecto:

```bash
git clone https://github.com/tu-usuario/PracticaGithubCinesolo.git
cd PracticaGithubCinesolo
```

> Si trabajas desde una copia externa, puedes hacer primero un *fork* del repositorio.

### 2. Crear e iniciar el contenedor Nginx

Descarga la imagen oficial de Nginx y crea un contenedor llamado `servidor-cine`:

```bash
docker run -d -p 80:80 --name servidor-cine nginx
```

Este comando publica el puerto `80` del contenedor en el puerto `80` de tu equipo.

Comprueba que el contenedor está en ejecución:

```bash
docker ps
```

Deberías ver `servidor-cine` con el estado `Up`.

### 3. Preparar los archivos de la aplicación

Nginx utiliza automáticamente `index.html` como página principal. Renombra el archivo principal de la aplicación:

```bash
mv ventaentradas.html index.html
```

### 4. Copiar la aplicación al contenedor

Copia los archivos del proyecto al directorio web de Nginx:

```bash
docker cp . servidor-cine:/usr/share/nginx/html/
```

> Nginx sirve los archivos desde `/usr/share/nginx/html/` dentro del contenedor.

### 5. Comprobar el despliegue

Abre el navegador y visita:

```text
http://localhost
```

La página principal de venta de entradas debería mostrarse correctamente.

---

## 📁 Estructura del proyecto

```text
.
├── index.html            # Página principal de la aplicación
├── ticket.html           # Vista de confirmación de entradas
├── ventaentradas.css     # Estilos principales
├── ticket.css            # Estilos del ticket
├── ventaEntradas.js      # Lógica interactiva
└── README.md             # Documentación de instalación
```

---

## 👤 Datos de la entrega

- **Alumno:** Gregory
- **Asignatura:** Implantación de Sistemas Operativos / ERP-CRM
- **Criterios de evaluación:**  
  - RA2.c — Instalación monopuesto  
  - RA2.d — Instalación cliente/servidor
