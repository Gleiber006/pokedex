# Publicación de la App PokeDex con Azure Static Web Apps

Este documento detalla cómo poner en línea tu aplicación **PokeDex** usando **Azure Static Web Apps**. Necesitarás una cuenta de Azure (idealmente la de estudiante) y el repositorio de GitHub del proyecto.

---

## 📋 Requerimientos Previos

-   Cuenta activa en Microsoft Azure.
-   Suscripción válida (puede ser gratuita, de estudiante o de pago).
-   Sesión iniciada en GitHub con acceso al repositorio del proyecto.

---

## 🛠️ Guía de Despliegue Paso a Paso

### 1. Acceso al Portal de Azure

Ingresa a tu cuenta de Azure a través de este enlace:
🌐 [https://portal.azure.com](https://portal.azure.com)

---

### 2. Localizar "Static Web Apps"

Utiliza la barra de búsqueda superior del portal, introduce `Static Web Apps` y selecciona el servicio correspondiente.
Haz clic en **"Crear"** para comenzar la configuración.

---

### 3. Configuración de la Nueva Aplicación

#### a. Información del Proyecto

-   **Suscripción:** Elige la suscripción que vas a utilizar.
-   **Grupo de recursos:** Selecciona un grupo existente o crea uno nuevo para organizar tus recursos.

#### b. Detalles de la Aplicación Estática

-   **Nombre:** Define un nombre único globalmente para tu PokeDex App.
-   **Plan:** Selecciona el plan (usualmente "Gratis" para empezar).
-   **Región:** Escoge la ubicación geográfica óptima para tu aplicación.

#### c. Detalles de la Implementación (Deployment)

-   **Fuente (Source):** Selecciona `GitHub`.
-   Asegúrate de tener la sesión de GitHub activa en tu navegador.
-   Autoriza a Azure para que acceda a tus repositorios de GitHub.
-   **Organización:** Selecciona tu cuenta de GitHub.
-   **Repositorio:** Elige el repositorio específico de tu PokeDex.
-   **Rama (Branch):** Selecciona la rama principal que contiene el código listo para desplegar (ej. `main`, `master`).
-   **Valores preestablecidos de compilación (Build Presets):** Selecciona el framework adecuado (React, Angular, Vue, etc.) o configura manualmente las ubicaciones de la app, API (si aplica) y la salida de compilación (`/build`, `/dist`, etc.).

---

### 4. Verificación y Lanzamiento

Pulsa **"Revisar y crear"**. Azure comprobará la configuración proporcionada.
Azure intentará detectar la configuración de compilación automáticamente si no la especificaste.

---

### 5. Creación del Recurso

Tras la validación exitosa, haz clic en **"Crear"**.
Azure comenzará a configurar los recursos y a desplegar tu aplicación desde GitHub Actions.

---

## 🎉 ¡Despliegue Completado!

Al finalizar el proceso, Azure te proporcionará una URL pública. ¡Tu PokeDex ya estará accesible en línea!

---

## 🔒 Consideraciones de Seguridad

-   Evita subir archivos de configuración (`.env`) o claves secretas directamente al repositorio. Usa las variables de entorno de Azure Static Web Apps.
-   Configura CORS adecuadamente si tu frontend consume APIs externas.
-   Confirma que el tráfico a tu sitio sea a través de HTTPS (Azure lo habilita por defecto).

---

### ✍️ Creado por

Julian Santana — Iniciativa académica para Pueblo Paleta Inc.
