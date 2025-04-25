# Implementación de la App PokeDex en Azure usando Static Web Apps

Este documento describe cómo desplegar la aplicación **PokeDex** mediante el servicio **Azure Static Web Apps**, utilizando una cuenta de Microsoft Azure y tu repositorio de GitHub.

---

## ✅ Antes de Comenzar

Asegúrate de contar con:

- Una cuenta de Azure activa (preferiblemente con acceso al plan de estudiantes).
- Una suscripción válida (gratuita, estudiantil o de pago).
- Sesión iniciada en GitHub y acceso al repositorio donde está el código de PokeDex.

---

## 🚀 Pasos para el Despliegue

### 1. Ingreso al Portal de Azure

Visita el portal principal de Azure:  
🔗 [https://portal.azure.com](https://portal.azure.com)

Inicia sesión con tus credenciales.

---

### 2. Búsqueda del Servicio Static Web Apps

En la barra superior del portal, escribe `Static Web Apps`.  
Haz clic en el resultado correspondiente y selecciona **"Crear"** para iniciar el proceso.

---

### 3. Configuración del Servicio

#### 🔹 Parámetros Iniciales

- **Suscripción**: Escoge la suscripción disponible.
- **Grupo de recursos**: Usa uno existente o crea uno nuevo para este proyecto.

#### 🔹 Detalles del Sitio Web

- **Nombre de la app**: Ingresa un nombre único a nivel global (ej: `pokedex-rony`).
- **Plan de hosting**: Selecciona la opción gratuita si es tu primer despliegue.
- **Región**: Elige una localización cercana a tus usuarios (ej: East US, West Europe).

#### 🔹 Configuración de GitHub

- En **Origen**, selecciona **GitHub** como fuente del código.
- Concede permisos para que Azure acceda a tu cuenta y repositorios.
- Selecciona:
  - Tu usuario o cuenta de organización de GitHub
  - El repositorio donde está tu proyecto
  - La rama (por lo general `main` o `master`)
- Define los valores para compilación según el stack que estés utilizando:
  - Ruta de la app (por ejemplo `/`)
  - Ruta de la API (si no hay, deja vacío)
  - Directorio de salida de la build (como `/dist` o `/build`)

---

### 4. Revisión y Confirmación

Haz clic en **"Revisar y crear"**.  
Azure validará los parámetros y verificará si todo está correctamente definido.

---

### 5. Despliegue Automático

Una vez validado, selecciona **"Crear"**.  
Azure empezará el proceso de despliegue utilizando GitHub Actions en segundo plano.

---

## 🌐 Tu App Está en Línea

Cuando termine el despliegue, se te asignará una URL pública del estilo:  
`https://nombre-app.azurestaticapps.net`

¡Puedes compartir este enlace con cualquier persona y ver tu app PokeDex en acción!

---

## 🔐 Buenas Prácticas de Seguridad

- No incluyas archivos `.env` ni claves API directamente en tu código.
- Usa las variables de entorno del portal Azure para guardar secretos.
- CORS: asegúrate de que esté configurado adecuadamente si tu app interactúa con APIs externas.
- HTTPS ya viene habilitado por defecto en Static Web Apps. No necesitas configurarlo manualmente.

---

### 👨‍💻 Autor

Rony Valdelamar — Proyecto académico para Pueblo Paleta Inc.
