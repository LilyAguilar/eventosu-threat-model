# EventosU — Modelado de Amenazas (Threat Modeling)

Repositorio del modelado de amenazas en fase de diseño para la plataforma universitaria **EventosU**, elaborado mediante la metodología **STRIDE**, árboles de ataque, matriz de priorización de riesgos y trazabilidad hacia **OWASP ASVS v4.0.3** y controles de CI/CD.

---

## Integrantes

Lilian Aguilar - 16005910

---

## Alcance del Modelo

### Qué entra en el alcance (In-Scope)
- **Sitio Web (React SPA) y Ruta `/admin`:** Aplicación frontend servida desde un CDN y el almacenamiento local del token de sesión en el navegador.
- **API Backend (Node.js en contenedor cloud):** Lógica de negocio para registro/login, creación de inscripciones, recepción del webhook de pagos, emisión y validación de códigos QR, subida de afiches, exportación de listados CSV y administración de usuarios/roles.
- **Capa de Persistencia en la Nube:** Base de datos relacional administrada (**PostgreSQL**) y **Bucket de Objetos** para almacenar los afiches de los eventos y los archivos CSV exportados.
- **App Móvil de Puerta:** Aplicación utilizada por el personal de puerta para escanear códigos QR y consultar su validez ante la API.
- **Flujos de Integración Externa:** Intercambio de tokens OAuth 2.0 con **Microsoft Entra ID**, redirección y recepción del webhook desde la **Pasarela de Pagos**, y solicitudes de envío de correo hacia el **Servicio Externo de Correo**.

### Qué queda fuera del alcance (Out-of-Scope)
- Seguridad interna e infraestructura propia de los proveedores externos (**Microsoft Entra ID**, **Pasarela de Pagos** y cumplimiento PCI-DSS del procesador de tarjetas, y **Servicio de Correo**).
- Seguridad física de los centros de datos del proveedor en la nube y de las instalaciones universitarias donde se realizan los eventos.
- Seguridad del sistema operativo de los teléfonos móviles del personal de puerta y de las computadoras personales de los usuarios finales.

---

## Estructura del Repositorio

```text
eventosu-threat-model/
├── README.md               # Descripción general, integrantes, alcance e instrucciones de uso
├── model/
│   └── eventosu.json       # Modelo completo en formato OWASP Threat Dragon v2 (DFD Nivel 0, Nivel 1 y 18 amenazas)
└── docs/
    ├── Informe.pdf         # Informe final en formato PDF
    └── amenazas.csv        # Catálogo completo de las 18 amenazas exportado en formato CSV
```

---

## Cómo Abrir y Visualizar el Modelo

El archivo [`model/eventosu.json`](./model/eventosu.json) está construido siguiendo el esquema oficial de **OWASP Threat Dragon v2.x** y puede abrirse sin errores tanto en la aplicación de escritorio como en la versión web:

### Visualización en Versión Web
1. Ingresar a la instancia web oficial de [OWASP Threat Dragon](https://www.threatdragon.com/).
2. Seleccionar **"Local Session"** (Sesión local) -> **"Open Threat Model"**.
3. Cargar el archivo `model/eventosu.json` desde este repositorio.
