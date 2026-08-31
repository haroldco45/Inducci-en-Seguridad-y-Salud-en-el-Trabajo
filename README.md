# Inducción en Seguridad y Salud en el Trabajo — DISTRILECO CAUCASIA S.A.S.

App web instalable (PWA) para la inducción y reinducción en SST del personal de Distrileco Caucasia S.A.S. Funciona sin internet, guarda el avance en el dispositivo y expide constancia de asistencia con fecha y hora real de Colombia.

Parte de la **Biblioteca Legal Colombiana** — Vibras Positivas HM.

---

## Contenido

| Módulo | Tema |
|---|---|
| 01 | Qué es el SG-SST y para qué existe |
| 02 | Derechos y deberes del trabajador |
| 03 | Peligros reales por puesto de trabajo (bodega, transporte, ventas TAT, administración) |
| 04 | Elementos de protección personal |
| 05 | Manipulación manual de cargas y estibado |
| 06 | Seguridad vial y riesgo público en ruta |
| 07 | COPASST, Comité de Convivencia y brigada |
| 08 | Ambiente laboral libre de acoso y violencia |
| 09 | Reporte de accidentes e incidentes |
| 10 | Emergencias, evacuación y primeros auxilios |

Después de los diez módulos se habilita una evaluación de 10 preguntas (se aprueba con 8) y, con la evaluación aprobada, la constancia imprimible.

---

## Normatividad verificada al 31 de agosto de 2026

Novedades incluidas que la mayoría de inducciones aún no contempla:

- **Decreto 1040 de 2026** (5 de agosto de 2026) — política y protocolo obligatorios contra el acoso, la violencia, la violencia basada en género y la discriminación; adiciona el Capítulo 8 al Decreto 1072 de 2015. Rige desde su publicación, sin plazo de transición.
- **Resolución 3461 de 2025** — nuevo régimen del Comité de Convivencia Laboral; deroga las Resoluciones 652 y 1356 de 2012. Período de 2 años.
- **Resolución 1843 de 2025** — evaluaciones médicas ocupacionales; deroga la Resolución 2346 de 2007.
- **Ley 2466 de 2025** — jornada nocturna desde las 7:00 p. m.; recargo dominical y festivo al 90 % desde el 1 de julio de 2026.
- **Ley 2101 de 2021** — jornada máxima de 42 horas semanales desde el 15 de julio de 2026.
- **Circular 027 de 2026** — reporte digital de la autoevaluación de estándares mínimos.

Cifras 2026 incorporadas: SMLMV $1.750.905 y auxilio de transporte $249.095 (Decretos 1469 y 1470 de 2025, ratificados por el Decreto 0159 de 2026).

---

## Antes de publicar: ajustar la configuración

En `index.html`, al inicio del bloque `<script>`, está el objeto `CONFIG`. Es el único sitio que hay que tocar:

```js
const CONFIG = {
  empresa: 'DISTRILECO CAUCASIA S.A.S.',
  whatsappSST: '573117700431',   // celular que recibe las constancias
  arlNombre: 'la ARL de la empresa',
  telefonoARL: '',               // línea de la ARL
  puntoEncuentro: 'el parqueadero frente a la bodega principal',
  pinAdmin: '2026'               // PIN para ver la cédula completa
};
```

Pendientes por completar con datos reales de la empresa: nombre y línea de la ARL, punto de encuentro oficial de cada sede, y el PIN del responsable de SST.

---

## Archivos

```
induccion-sst-distrileco/
├── index.html        App completa (HTML + CSS + JS, sin dependencias)
├── manifest.json     Manifiesto PWA
├── sw.js             Service Worker (offline + instalabilidad)
├── icon-192.png      Ícono 192×192
├── icon-512.png      Ícono 512×512 (any + maskable)
├── og-image.png      Vista previa WhatsApp/redes 1200×630
└── README.md
```

---

## Despliegue en GitHub Pages

```bash
# dentro del repositorio biblioteca-legal
git add induccion-sst-distrileco
git commit -m "feat: inducción SST Distrileco — normatividad vigente ago/2026"
git push
```

URL resultante:

```
https://haroldco45.github.io/Inducci-en-Seguridad-y-Salud-en-el-Trabajo/
```

Si se publica en otra ruta, hay que actualizar `og:url` y `og:image` en `index.html` (deben ser URLs absolutas para que WhatsApp muestre la vista previa).

---

## Características técnicas

- HTML5, CSS3 y JavaScript vanilla. Sin frameworks ni dependencias externas más allá de Google Fonts.
- PWA instalable: manifest + Service Worker con caché de todos los recursos.
- Fecha y hora real de Colombia mediante `Intl.DateTimeFormat` con zona `America/Bogota`, independiente de la configuración del celular.
- Avance y resultado guardados en `localStorage`, con manejo de errores para modo incógnito.
- Constancia imprimible o exportable a PDF desde el navegador, y envío por WhatsApp.
- Accesible: foco visible por teclado, `aria-expanded` en los módulos, barra de progreso con rol ARIA y respeto a `prefers-reduced-motion`.
- Responsive, pensada para uso en celular dentro de la bodega.

---

## Protección de datos — Ley 1581 de 2012

- Los datos del trabajador se guardan **solo en el dispositivo**. No hay servidor ni base de datos remota.
- La cédula se muestra **enmascarada por defecto** en la constancia; solo se revela con el PIN del responsable de SST.
- El formulario incluye la autorización expresa de tratamiento de datos, obligatoria antes de generar la constancia.

---

## Aviso legal

Documento de carácter formativo. No sustituye el SG-SST documentado de la empresa, el reglamento interno de trabajo, ni la asesoría del responsable de SST o de la ARL. Las referencias normativas están verificadas a la fecha indicada; la normatividad colombiana cambia con frecuencia y debe revisarse antes de cada ciclo anual de reinducción.

---

*Desarrollada por **Vibras Positivas HM** — Derechos de Autor Reservados*
*vibraspositivashm.com · Caucasia, Antioquia, Colombia · 2026*
