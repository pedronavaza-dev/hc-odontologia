# HC Odontología — Sistema de gestión para consultorio

**Trabajo Final Integrador — Diplomatura en IA Aplicada a Entornos Digitales de Gestión (FCE-UBA, Cohorte 2026)**

Mini-sistema de gestión pensado para reemplazar la planilla Excel que usa un consultorio odontológico para llevar ventas, cobros, deudas y gastos. Diseñado 100% con asistencia de IA generativa (Claude Code) a partir de un problema real detectado en una consulta profesional.

---

## 🔗 Demo online

👉 **[Abrir la app](https://pedronavaza-dev.github.io/hc-odontologia/)**

_(Se despliega con GitHub Pages, no requiere instalación.)_

---

## 🩺 El problema que resuelve

El consultorio lleva hoy toda su gestión en una planilla Excel de 5 hojas (Ingresos, Egresos, Compras, Resultado, Listado). Los tres dolores concretos que motivaron este proyecto:

1. **Carga desde el celular tediosa** — la profesional carga los cobros desde el celular en el momento, y el Excel no está pensado para eso.
2. **Conceptos repetidos** — pacientes cargados con espacios extra o mayúsculas distintas ("Maziar, Andrey" vs "Maziar, Andrei"), prestaciones tipeadas distinto cada vez ("consulta" vs "consulta " vs "consulta urgencia"). Ensucia los datos y hace imposible analizar.
3. **Difícil sacar conclusiones** — al estar los datos sucios y en formato de planilla, no hay tablero real de qué se vendió, qué se debe, cuánto entró al mes.

## 💡 Cómo lo resuelve

- **Catálogos normalizados** — pacientes, prestaciones, proveedores e insumos se eligen de una lista con autocompletado. No se puede tipear cualquier cosa: o se elige uno existente o se crea uno nuevo desde un modal.
- **Diseño mobile-first** — la carga está optimizada para el celular (botones grandes, mínimos toques por operación).
- **Modelo de datos rico** — ventas con múltiples cobros parciales, deudas de pacientes, cuenta corriente con proveedores (laboratorios + insumos), número de operación autoincremental.
- **Vistas de análisis** — lista filtrable y exportable a Excel, cuenta corriente de deudores, resumen del mes.

---

## 🧭 Cómo usar la app

Al entrar, la home tiene dos solapas:

### 🎯 Solapa Acciones
Dos módulos desplegables:

- **📈 Ventas** — Nueva venta / Cargar cobro / Ver mis ventas / Deudores por venta
- **📉 Compras** — Cargar compra / Cargar gasto fijo / Cargar pago a proveedor

### 📊 Solapa Resumen
- **Flujo del mes** — cobrado, gastado, pagos a proveedores, flujo neto
- **Estado actual** — deudores de pacientes / deuda a proveedores

### Flujos principales que podés probar

1. **Cargar una venta** con cobro parcial: en Nueva venta, elegí paciente + prestación + monto, y agregá uno o varios cobros. Lo que no se cobra queda como deuda del paciente. El sistema asigna un número de operación (empezando en #1000).
2. **Cobrar un saldo pendiente**: desde "Cargar cobro" (o desde Deudores por venta), elegís el paciente y aparecen sus operaciones con saldo. Elegís y cobrás.
3. **Ver deudores**: en Deudores por venta ves la cuenta corriente de pacientes agrupada por persona, con opción de filtrar y exportar a Excel.
4. **Análisis de ventas**: en Ver mis ventas podés filtrar por período, paciente, prestación, medio de cobro o estado (saldadas / con saldo), y exportar el resultado a Excel.

---

## 🚦 Estado del proyecto

**Funcional real** (guarda datos en el navegador vía `localStorage`):
- ✅ Home con solapas
- ✅ Nueva venta con múltiples cobros parciales
- ✅ Cargar cobro suelto asociado a operación previa
- ✅ Lista de ventas con filtros múltiples y exportación a Excel (CSV)
- ✅ Deudores por venta con exportación a Excel
- ✅ Catálogos administrables (pacientes, prestaciones, medios de cobro)

**Maqueta visual** (diseño listo, sin persistencia):
- 🚧 Cargar compra (con soporte laboratorio + insumos)
- 🚧 Cargar gasto fijo
- 🚧 Cargar pago a proveedor (con imputación FIFO)
- 🚧 Deudas a proveedores

Cada pantalla maqueta tiene un cartel amarillo aclarando su estado. Los datos que aparecen en esas pantallas son de ejemplo, tomados del Excel real del consultorio.

---

## 🛠️ Stack técnico

- HTML puro + Tailwind CSS (vía CDN)
- JavaScript vanilla
- `localStorage` para persistencia
- GitHub Pages para el hosting

Sin frameworks (React/Vue/etc), sin backend, sin base de datos. Suficiente para prototipo y demostración de concepto. Para la implementación real en el consultorio se planea migrar a Next.js + Supabase (Postgres administrado).

---

## 🤖 Uso de IA generativa

Este proyecto se construyó íntegramente con **Claude Code** (Anthropic) como asistente. El proceso incluyó:

- **Fase 1 — Descubrimiento** — múltiples conversaciones para entender el dolor del usuario a partir del Excel real. Claude leyó el .xlsx, detectó duplicados, propuso una estructura de datos y flujos.
- **Fase 2 — Diseño** — modelado de las 11 "cajas" de datos (pacientes, prestaciones, ventas, cobros, compras, items, pagos, etc.), wireframes en texto de las 17 pantallas, decisiones de UX (mobile-first, autocompletado, saldos calculados, imputación FIFO en pagos).
- **Fase 3 — Implementación** — este código, escrito paso a paso, iterando con feedback del usuario.

Las decisiones de producto (qué priorizar, qué modelo mental usar, correcciones sobre supuestos incorrectos de la IA) fueron humanas. La IA asistió en la exploración, el diseño y la escritura del código.

---

## 🎯 Próximos pasos

1. **Adaptación a PC (responsive)** — hoy la app está pensada para celular. Adaptarla a formato desktop (sidebar de navegación, formularios en 2 columnas, tablas expandidas) va a permitir que la profesional analice cómodamente desde la computadora del consultorio.
2. **Backend real** — migrar de `localStorage` a una base de datos en la nube (Supabase) para que los datos persistan entre dispositivos y no se pierdan si se limpia el navegador.
3. **Completar los módulos maqueta** — activar la funcionalidad de Compras, Gastos y Pagos a proveedores.
4. **Migración del Excel actual** — cargar los ~1000 movimientos históricos del Excel, con deduplicación asistida de pacientes y prestaciones.
5. **Presupuestador de prestaciones** — usar el catálogo de insumos con "insumos típicos por prestación" para calcular automáticamente el precio sugerido de cada tratamiento.

---

## 📄 Sobre este TP

Trabajo realizado por **Pedro Navaza** para la Diplomatura en IA Aplicada a Entornos Digitales de Gestión (Facultad de Ciencias Económicas, UBA · Cohorte 2026).

El informe con la metodología, análisis crítico y conclusiones se entrega en PDF junto con este repositorio.
