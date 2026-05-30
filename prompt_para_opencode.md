Actúa como un desarrollador experto. Necesito que desarrolles desde cero una aplicación web tipo PWA (Progressive Web App) llamada "PicoCERO". El objetivo del sistema es gestionar la energía de una instalación, simular generación solar y hacer "Load Shedding" (deslastre de carga automático) para no superar un límite de potencia establecido.

A continuación, te detallo los requisitos y funcionalidades que debes implementar:

1. Stack Tecnológico:
- Dale profundidad y funciones avanzadas pero me gustaria que pueda ser subible a github pages para facilitar la portabilidad y testeo de la interfaz durante el desarrollo. segmenta bien los archivos para que sea facilmente mantenible. más su manifest.json y sw.js para la PWA.
- Tailwind CSS (vía CDN) para los estilos.
- Phosphor Icons (vía CDN) para la iconografía.
- Chart.js (vía CDN) para los gráficos.
- SortableJS (vía CDN) para el Drag & Drop de las tarjetas.

2. Diseño y UI/UX:
- Debe tener dos temas: Claro (estilo pastel/cute con fondos claros y detalles rosas/morados) y Oscuro (estilo OLED/Cyberpunk con fondos negros puros, detalles cyan y rosa neón. similar al estilo visual de Vercel pero personalizado para la aplicación y un poco mas oscuro, sin perder la estética de neón).
- Interfaz tipo "Dashboard" moderno, con un Header superior, barra de navegación por pestañas (Tiempo Real, Histórico, Configuración, recomendar posibles adiciones) y área de contenido principal. No debe parecer un dashboard de empresa, debe sentirse mas hogareño y amigable.
- En versión mobile (Pantallas verticales) agrupar los logos debajo y hacerlo mas facil de utilizar para una persona desde un telefono. En vista de escritorio la barra de navegación debe ser vertical en el lateral izquierdo.
- Uso de modales para interacciones, toasts para notificaciones y efectos visuales de "glassmorphism".

3. Funcionalidad Principal - Tiempo Real:
- Mostrar el consumo total actual (Demanda Actual en Watts).
- Mostrar la generación solar actual simulada (Producción Solar en Watts). y agregar la opción de eliminar esta funcionalidad desde los settings para las empresas que no tengan generacion solar
- Permitir ajustar un límite dinámico de potencia general en kW.
- Gráfico en tiempo real (Chart.js) que muestre la evolución del consumo vs el límite y la generación solar.
- Selector de modo: AUTO (el sistema apaga cargas automáticamente si se pasa el límite) o MANUAL (permite sobrepasar el límite bajo la responsabilidad del usuario). y avisa claramente cuando se produce esto o cuando se apaga algo y el por que se apaga
- Barra de progreso que cambie de color (verde, amarillo, rojo) según la cercanía al límite de potencia.

4. Gestión de Cargas (Dispositivos):
- Mostrar tarjetas individuales para cada dispositivo o contactor (ej. Nevera, Servidores, Bomba de Agua).
- Cada tarjeta debe tener un botón de encendido/apagado, su potencia en W, su icono y categoría.
- Para cada item, al cabo de un tiempo, la aplicación me debe de decir el consumo promedio en W o kW segun corresponda y el consumo pico en el arranque. para esto quiero agregar el consumo de los primeros 15 segundos de encendido.
- Drag & Drop: Las tarjetas se deben poder arrastrar para cambiar su orden de prioridad. La tarjeta en primera posición es la más prioritaria y la última será la primera en apagarse en caso de sobrecarga.
- para poder agregar cargas, estaria bien qeu la aplicación pida una ip para enviar el input para entrar o salir de la red, el consumo promedio esperado el cual despues se actualizara con el real, por ahora hasta que sea definitivo la posible variación de carga a traves del tiempo 
- Funcionalidad de Load Shedding: Un bucle principal debe calcular constantemente el consumo total. Si el consumo es mayor al límite (y el modo es AUTO), debe apagar las cargas de menor prioridad hasta que el consumo sea menor al límite.
- Opción de programar horarios (encendido a una hora, apagado a otra) para cada dispositivo. y que sea facil de modificar o automatizar.
- Botón para abrir un modal que permita añadir nuevos dispositivos o editar los existentes.
que la lista de dispositivos se pueda colocar como tarjetas o como una lista literalmente para que sea fecil llevar el control de muchos componentes a la vez si modificamos la organización del sitio. y que se pueda filtrar por categoria y por estado (encendido/apagado)

5. Simulación Solar y Límite Ecológico:
- La generación solar no es fija. Debe calcularse basándose en la hora del día (simulando un amanecer a las 6:00, pico a las 12:00 y atardecer a las 18:00 usando una onda senoidal) sumándole un "ruido" o variabilidad que simule nubes. (Debe incorporar una ip para que el sistema inversor de los paneles solares, envien el dato de la cantidad de potencia generada en ese instante, similar a los sistemas para casa offgrid que tiene huawei cuando se coloca con baterias, paneles y consumo aislado)
- "Límite Ecológico": Un interruptor que, al activarse, hace que el límite de consumo de todo el sistema no sea el valor manual en kW, sino el valor exacto de la generación solar en ese instante.

6. Logs y Notificaciones:
- Un panel de "Registro del Sistema" (Log de Eventos) que muestre de forma textual con la hora cada acción importante (ej: apagado de carga por sobrecarga, encendido automático por horario, cambio de modo).
- Notificaciones flotantes tipo Toast en una esquina de la pantalla para avisar al usuario.
- un aviso claro de en que modo esta, modificando sutilmente la interfaz, por ejemplo cuando esta en modo manual o override que se note claramente dentro de la aplicación para evitar estar en este modo por accidente.

7. Otras pestañas:
- Histórico: Mostrar KPIs estáticos (ej: Consumo mensual, ahorro) y un gráfico histórico de Chart.js.
- Configuración: Sliders para ajustar el pico de generación solar máxima y el porcentaje de variabilidad (nubes). Botones para restaurar dispositivos por defecto y borrar datos.

Por favor, genera el código completo siguiendo exactamente estos requisitos. trabaja dentro de la carpeta rev2.0 para evitar modificar la aplicacion ya existente la cual sera la legacy version

