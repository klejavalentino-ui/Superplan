# 🛒 SúperPlan — Sistema Experto Local de Despensa, Nutrición y Compra Inteligente

**SúperPlan** es una aplicación web progresiva (**PWA**) 100% offline que funciona como un **sistema experto local basado en reglas** para organizar el inventario de casa (despensa, nevera y congelador), planificar el menú nutricional de la semana y optimizar la lista de la compra por pasillos y supermercados en **Castellón de la Plana** (**Mercadona**, **Carrefour** y **Alcampo**).

---

## ✨ ¿Qué es y cómo funciona?

A diferencia de otras aplicaciones que dependen de servidores externos o modelos de inteligencia artificial en la nube, **SúperPlan funciona íntegramente en tu dispositivo** mediante un motor determinista de reglas (`ExpertRuleEngine`) y almacenamiento local (`localStorage` + `Service Worker` offline).

### 🎯 Reglas prioritarias de decisión
El motor experto toma decisiones combinando tu inventario actual, fechas de caducidad, historial de compras, presupuesto semanal y objetivos nutricionales bajo 5 reglas jerárquicas:

1. **Consumir primero lo que ya tienes en casa**: Prioriza recetas cuyos ingredientes principales ya están en tu despensa.
2. **Priorizar productos cercanos a caducar**: Detecta alimentos que caducan en $\le 5$ días y los incorpora de forma preferente en las comidas de los próximos días para evitar el desperdicio alimentario.
3. **Minimizar el gasto semanal**: Penaliza platos que requieren comprar ingredientes caros no disponibles en casa y compara el coste total del carro entre supermercados.
4. **Mantener la variedad semanal**: Evita repetir el mismo grupo proteico principal en tomas o días consecutivos.
5. **Garantizar el equilibrio nutricional**: Verifica diariamente el cumplimiento de:
   - **Proteína suficiente** adaptada al perfil (activo o deportista).
   - **Presencia diaria de verduras** en comidas y cenas.
   - **Fruta diaria** en desayunos y meriendas.
   - **Fibra adecuada** ($\ge 28\text{–}32\text{ g/día}$) mediante legumbres, cereales integrales, fruta y verdura.

---

## 🧩 Módulos principales

- **📋 Lista de Compra por Pasillos**: Agrupa automáticamente los productos faltantes según el recorrido físico del supermercado (Frutería, Carnicería, Pescadería, Lácteos, Aceites y Despensa, Congelados, etc.).
- **🏠 Mi Despensa con Alertas de Caducidad**: Control de stock por categorías con fecha de compra, fecha de caducidad estimada y alertas visuales de consumo prioritario.
- **💶 Presupuesto y Comparador Multi-Supermercado (Castellón)**:
  - Compara en tiempo real el coste estimado de tu lista de compra entre **Mercadona**, **Carrefour** y **Alcampo** en Castellón de la Plana.
  - Incluye una **capa modular de precios (`SupermarketPricingLayer`)** preparada para conectarse en el futuro a archivos JSON actualizados automáticamente, APIs o sistemas de scraping.
- **🥗 Menú Semanal & Nutrición**: Generación automática de desayuno, comida, merienda saludable y cena, con semáforo de cumplimiento nutricional y volcado en un clic de los ingredientes faltantes a la lista de compra.
- **📲 Exportación y PWA Offline**:
  - Instalable como aplicación nativa en **Android (Chrome)** y **iOS (Safari)** desde GitHub Pages.
  - Exportación directa del plan y la lista de compra a **WhatsApp** o **Notas del móvil**.

---

## 🚀 Despliegue y Uso

La aplicación es 100% estática y no requiere compilación ni backend:

- [`index.html`](./index.html) — Interfaz, catálogo multi-supermercado y motor experto basado en reglas.
- [`manifest.json`](./manifest.json) — Configuración de instalación PWA.
- [`sw.js`](./sw.js) — Service Worker con estrategia *Cache First / Stale-While-Revalidate* para funcionamiento sin conexión.
