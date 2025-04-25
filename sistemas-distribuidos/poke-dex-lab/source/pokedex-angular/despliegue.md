# Diagrama de Arquitectura en Azure para PokeDex

```
                    [Usuario Final]
                          |
                          v
                  [Navegador (HTTPS)]
                          |
                          v
+------------------------------------------------------+
|                  AZURE STATIC WEB APPS               |
|                                                      |
|  - Hosting para la aplicación PokeDex Angular        |
|  - URL: https://[nombre-app].azurestaticapps.net     |
|  - HTTPS automático                                  |
+------------------------------------------------------+
                          ^
                          |
                          v
+------------------------------------------------------+
|                INTEGRACIÓN CON GITHUB                |
|                                                      |
|  +-------------------+    +----------------------+   |
|  | GitHub Repository |    | GitHub Actions       |   |
|  | PokeDex Angular   |--->| CI/CD Automatizado   |   |
|  +-------------------+    +----------------------+   |
+------------------------------------------------------+
                          ^
                          |
                          v
+------------------------------------------------------+
|              ADMINISTRACIÓN Y SEGURIDAD              |
|                                                      |
|  +-------------------+    +----------------------+   |
|  | Resource Group    |    | Azure Active         |   |
|  | (Administración)  |<-->| Directory (Usuarios) |   |
|  +-------------------+    +----------------------+   |
|                                                      |
|  +-------------------+    +----------------------+   |
|  | Application       |    | Azure Monitor        |   |
|  | Insights (Logs)   |<-->| (Alertas/Métricas)   |   |
|  +-------------------+    +----------------------+   |
+------------------------------------------------------+
```

## Componentes de la Arquitectura

### 1. Acceso de Usuario
- **Usuario Final**: Accede a la aplicación PokeDex a través de cualquier navegador web
- **HTTPS**: Conexión segura y cifrada para todas las comunicaciones

### 2. Azure Static Web Apps
- **Servicio principal de hosting** para aplicaciones web estáticas como PokeDex Angular
- **Características clave**:
  - URL pública con formato `https://[nombre-app].azurestaticapps.net`
  - Certificados SSL/TLS generados y gestionados automáticamente
  - Optimizado para Single Page Applications (SPA) como Angular
  - Plan gratuito disponible para estudiantes

### 3. Integración con GitHub
- **GitHub Repository**:
  - Almacena el código fuente de la aplicación PokeDex Angular
  - Control de versiones y revisión de código
  - Gestión de issues y características

- **GitHub Actions**:
  - Pipeline automático de Integración Continua y Despliegue Continuo (CI/CD)
  - Ejecución de pruebas automáticas
  - Compilación y despliegue a Azure con cada commit a la rama principal

### 4. Administración y Seguridad
- **Azure Resource Group**:
  - Agrupación lógica de recursos relacionados con PokeDex
  - Administración centralizada de permisos y políticas
  - Control de costos y facturación

- **Azure Active Directory**:
  - Sistema de autenticación y autorización
  - Gestión de identidades de estudiantes y desarrolladores
  - Políticas de acceso y seguridad

- **Application Insights**:
  - Telemetría y análisis del rendimiento de la aplicación
  - Registro de errores y excepciones
  - Seguimiento de uso y comportamiento del usuario

- **Azure Monitor**:
  - Sistema centralizado de monitoreo
  - Alertas basadas en umbrales definidos
  - Dashboards personalizables para visualización de métricas

## Flujo de Implementación

1. El desarrollador sube cambios de código al repositorio GitHub
2. GitHub Actions detecta los cambios y activa el pipeline de CI/CD
3. Se realizan pruebas automáticas y se compila la aplicación
4. La aplicación compilada se despliega en Azure Static Web Apps
5. La nueva versión está disponible instantáneamente para los usuarios
6. Application Insights monitorea el rendimiento y los errores
7. Azure Monitor alerta sobre posibles problemas o anomalías

## Beneficios de esta Arquitectura

1. **Simplicidad operativa**: No requiere gestión de servidores
2. **Seguridad mejorada**: HTTPS por defecto, protección a nivel de plataforma
3. **Integración nativa con GitHub**: Simplifica el ciclo de desarrollo
4. **Costos optimizados**: Modelo de pago por uso con opción gratuita para estudiantes
5. **Escalabilidad automática**: Se adapta al tráfico sin configuración adicional

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

- **Nombre de la app**: Ingresa un nombre único a nivel global (ej: `pokedex-Gleiber`).
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

Gleiber garces — Proyecto académico para Pueblo Paleta Inc.
