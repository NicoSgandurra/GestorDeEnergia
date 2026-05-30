# Product Requirements Document (PLD) - PicoCERO

## 1. Visión General del Producto
**PicoCERO** es un Sistema de Gestión de Energía diseñado para industrias. Su objetivo no es solo visualizar el consumo, sino gestionar de forma inteligente y automatizada la energía mediante "Load Shedding", simulación de baterías y paneles solares, y automatización predictiva. Todo esto bajo una interfaz de usuario extremadamente pulida, moderna y atractiva.

## 2. Arquitectura y Portabilidad
El proyecto me gustaria que siga una arquitectura PWA estática:
- **Frontend:** Vanilla JavaScript (ES6 Modules) o un framework ligero estático (Vite + React/Vue exportado a estático).
- **Estructura de Archivos:** Segmentación estricta (`/css`, `/js/components`, `/js/core`, `/assets`).
- **Persistencia:** Almacenamiento local (IndexedDB/localStorage) para mantener el estado entre sesiones, con posibilidad de exportar/importar configuraciones en formato JSON.
- **PWA:** `manifest.json` y Service Workers para uso offline y poder instalarse como aplicación nativa en móviles y escritorio.

En el caso de ser necesario modificar esto, estoy abierto a sugerencias para mejorar la escalabilidad del proyecto y el alcance.

## 3. Características "Al Siguiente Nivel" (Propuestas)
Además del monitoreo básico y "Load Shedding", esta versión incluirá:
1. **Simulación de Baterías (Powerwall):** Gestión de almacenamiento de energía. El sistema debe decidir si usar la energía solar para cargar la batería, alimentar la casa, o hacer deslastre.
2. **Integración de Tarifas Dinámicas:** Simulación de precios de electricidad por tramos horarios. El sistema priorizará encender cargas no críticas (ej. Lavadora) en las horas más baratas.
3. **Reglas Inteligentes (Motor Lógico):** Automatizaciones basadas en condiciones (Ej: "Si la batería > 80% Y el panel solar produce > 2000W, encender la bomba de la piscina").
4. **Motor Climático/Predictivo:** Simular clima a lo largo de los días (nublado, soleado) para predecir la curva solar y ajustar el deslastre de carga anticipadamente.
5. **Módulos Opcionales (Feature Flags):** Activar o desactivar características como "Paneles Solares" o "Baterías" desde la configuración para industrias que no posean esta infraestructura.

## 4. Diseño y UI/UX (Estética)
- **Layout Responsivo:** 
  - *Escritorio/Tablets:* Barra de navegación lateral izquierda (Sidebar).
  - *Móviles:* Barra de navegación inferior (Bottom Navigation Bar) con iconos grandes y fáciles de tocar a una mano.
- **Sensación amigable:** Evitar tablas densas y gráficos técnicos complejos de entrada (excepto qeu se busque esto dentro de su sección (detalles)). Usar tarjetas con esquinas muy redondeadas, tipografía amigable (ej. Rounded fonts) y lenguaje adecuado, por ejemplo:("Demanda global del sistema").
- **Temas:**
  - **Dark Mode (Cyber-Vercel):** Fondos negros profundos (`#000`), bordes muy sutiles (`#111` a `#333`), con acentos de color neón (cyan y rosa) brillando sutilmente (efecto glow) cuando hay actividad.
  - **Light Mode (Pastel/Cute):** Tonos lavanda, beige y blanco translúcido, sombras muy suaves y colores pastel vibrantes para los estados (verde menta, amarillo patito, rosa chicle).
- **Glassmorphism:** Efectos de desenfoque de fondo (`backdrop-filter`) en modales y barras de navegación para dar profundidad.

## 5. Especificaciones Técnicas (MVP de la Nueva Versión)
