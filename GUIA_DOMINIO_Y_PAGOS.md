# GUÍA TÉCNICA Y ESTRATÉGICA: CORPORAGRO.ORG
## Nuevo Sitio Web, Pasarela Redeban y Configuración de Dominio

---

### 1. Resumen del Proyecto Realizado
Se realizó un scraping integral y extracción exhaustiva de la base de datos de WordPress de `corporagro.org`:
- **Documentos legales y oficiales recuperados e integrados:**
  - Cámara de Comercio y Certificado de Existencia y Representación Legal
  - Certificado DIAN de Régimen Tributario Especial (RTE)
  - Estados Financieros Auditados y Notas Contables
  - Certificación de Requisitos de Representante Legal y Miembros de Junta
  - Estatutos Sociales y Acta No. 01 de Fundación de 2006 (acredita más de 18 años de trayectoria formal)
- **Activos visuales:** Se descargaron los logotipos originales de alta resolución y las fotografías auténticas de campo (asistencia técnica, elaboración de abonos orgánicos, comunidades campesinas).
- **Portafolio ampliado de servicios:**
  1. Asistencia Técnica Directa Rural (ATDR)
  2. Formulación y Elaboración de Proyectos (Metodología MGA, Sistema General de Regalías, ADR, MinAgricultura)
  3. Consultoría y Asesoría Técnica Agropecuaria (Agrícola, Pecuaria, Piscícola, Forestal, Ambiental)
  4. Diseño, Instalación y Operación de Distritos de Riego y Drenaje
  5. Infraestructura Rural y Obras Civiles (Centros de acopio, vías terciarias, acueductos comunitarios)
  6. Comercialización de Insumos Agropecuarios, Plántulas de Vivero y Alevinos

---

### 2. Integración del Canal de Pagos Seguros con Redeban

Para que las organizaciones, entidades públicas o clientes que van a transferir fondos sientan **100% de confianza**:
1. **Canal Visible en Todo el Sitio:**
   - Botón permanente en el Navbar con insignia de seguridad y alerta visual.
   - Sección interactiva dedicada a **Pagos Seguros Redeban** con explicación de respaldo bancario (PSE y Tarjetas Visa, Mastercard, American Express).
   - Modal interactivo donde el usuario indica concepto de pago y referencia.
2. **Cómo vincular la URL exacta que entregó Redeban:**
   En el archivo `index.html`, en la línea ~495 (sección `<script>`), encontrará:
   ```javascript
   const REDEBAN_MERCHANT_CONFIG = {
       defaultPaymentUrl: "https://checkout.pagosredeban.com/corporagro", // <-- AQUÍ SE PEGA EL ENLACE ENTREGADO POR REDEBAN
       merchantName: "CORPORACION PARA EL DESARROLLO RURAL Y AGROPECUARIO",
       nit: "900.074.281-5",
       whatsappSupport: "573205436104"
   };
   ```
   *Nota: Si Redeban les dio un link de recaudo SmartPay / Enlace de cobro, simplemente se reemplaza esa comilla con su enlace y el botón redirigirá instantáneamente.*

---

### 3. Asesoría para Conservar el Dominio `corporagro.org`

Usted mencionó: *"Este dominio que ellos tienen nos toca respetarles su dominio, o sea que vamos a desarrollarlo nosotros, pero luego necesitamos que quede en ese mismo dominio. Me asesoras en todo eso"*.

Aquí está el procedimiento profesional recomendado para que **no se pierda el dominio**, no se caigan los correos corporativos y el sitio cargue a máxima velocidad:

#### Opción A: Mantener el mismo Hosting actual (si tienen cPanel o hosting donde estaba WordPress)
1. Ingrese al **cPanel** del hosting actual de Corporagro.
2. Vaya al **Administrador de Archivos** (`File Manager`).
3. Abra la carpeta `public_html`.
4. Cree una carpeta de respaldo llamada `backup_wordpress_antiguo` y mueva los archivos de WordPress allí (por si alguna vez desean consultar algo antiguo).
5. Suba a `public_html` los archivos del nuevo sitio web:
   - `index.html`
   - Carpeta `assets/` (con `assets/img/` y `assets/docs/`)
6. **Resultado:** Al ingresar a `https://corporagro.org` inmediatamente cargará el nuevo sitio, con certificado SSL automático y sin alterar ningún registro de correo.

#### Opción B: Hospedaje Gratuito de Alto Rendimiento (Vercel, Netlify o Cloudflare Pages)
Si desean un hosting moderno, ultra rápido, que nunca se caiga y con costo \$0:
1. Subir este proyecto a un repositorio GitHub o arrastrar la carpeta a **Vercel** o **Netlify**.
2. En el registrador donde compraron el dominio `corporagro.org` (GoDaddy, Namecheap, DonDominio, etc.), ir a la sección de **Zona DNS**:
   - Cambiar el **Registro A** `@` apuntándolo a la IP provista por el nuevo hosting.
   - O apuntar el **CNAME** `www` a `cname.vercel-dns.com` (o el equivalente).
   - **IMPORTANTE:** No tocar los registros **MX**, **TXT (SPF)** ni **DKIM**, para que los correos corporativos sigan funcionando sin interrupción.

---

### 4. Estructura de Archivos en su Computador
```
c:\Users\JhonZapata\Desktop\CORPORAGRO\
│
├── index.html                  # Sitio web completo, responsivo y ultra moderno
├── GUIA_DOMINIO_Y_PAGOS.md     # Esta guía de despliegue y pasarela Redeban
└── assets/
    ├── img/                    # Logotipos oficiales, fotos de proyectos y campo
    └── docs/                   # Documentos oficiales de la DIAN, Cámara de Comercio y Estados Financieros
```
