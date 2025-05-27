# Cliente Frontend para Integración API Rappi

Este proyecto es una aplicación web frontend de una sola página (SPA) diseñada para interactuar con la API de Rappi. Permite a los usuarios gestionar su catálogo de productos, manejar pedidos y realizar otras operaciones relacionadas con la integración de Rappi, todo a través de una interfaz gráfica.

La aplicación está construida puramente con HTML, CSS y JavaScript vainilla (utilizando módulos ES6).

## Funcionalidades Principales

### Autenticación y Configuración
* **Autenticación:** Permite ingresar Client ID y Client Secret para obtener un token de acceso.
* **Selección de País:** Configura las URLs base correctas de la API según el país seleccionado (PER, COL, MEX, etc.).
* **Gestión de Token:** Muestra el token de acceso y un temporizador estimado de expiración.

### Gestión de Catálogo
* **Visualización de Productos:** Carga y muestra productos del catálogo con paginación y búsqueda por SKU o nombre.
* **Creación de Productos:**
    * Formulario para crear nuevos productos, especificando SKU, nombre, descripción, EAN, categoría, presentación, etc.
    * Soporte para productos con y sin variaciones.
    * Árbol de categorías interactivo para seleccionar la categoría del producto.
    * Carga y asignación de atributos específicos de la categoría.
* **Edición de Productos:** Modifica productos existentes (nota: la API de Rappi a menudo requiere eliminar y recrear el producto para "editarlo").
* **Eliminación de Productos:** Elimina productos del catálogo de Rappi.
* **Asociación/Desasociación con Tiendas:**
    * Permite asociar productos del catálogo a tiendas específicas, definiendo precio y stock.
    * Permite desasociar productos de tiendas.
* **Gestión de Categorías:** Visualiza categorías principales y un árbol completo de categorías.
* **Listado de Tiendas:** Muestra una lista de las tiendas configuradas.

### Gestión de Pedidos
* **Visualización de Pedidos:**
    * Carga y muestra pedidos pendientes o recientes.
    * Búsqueda de pedidos por ID.
    * **Polling Automático:** Actualiza periódicamente la lista de pedidos (frecuencia configurable).
* **Detalles del Pedido:** Muestra información detallada de un pedido, incluyendo productos, cliente, precios, y estado.
* **Acciones sobre Pedidos:**
    * **Iniciar Picking:** Marcar un pedido como en proceso de preparación.
    * **Reportar Factura:** Enviar información de la factura del pedido.
    * **Solicitar Mensajero (RT):** Pedir un RappiTendero para el despacho.
    * **Handshake con RT:**
        * Solicitar códigos de handshake.
        * Validar el código proporcionado por el RT para confirmar la entrega.
    * **Cancelar Pedido:** Enviar una solicitud de cancelación.
    * **Eliminar Producto del Pedido:** Remover un ítem específico de un pedido en curso.
    * **Sustituir Producto:**
        * Proponer la sustitución de un producto no disponible.
        * Buscar productos sustitutos en el catálogo.
        * Visualizar el estado de las propuestas de sustitución.

### Utilidades
* **Visor JSON:** Muestra la última URL solicitada, el cuerpo de la solicitud y la respuesta de la API en formato JSON para facilitar la depuración.
* **Notificaciones Toast:** Informa al usuario sobre acciones exitosas o errores.
* **Copiar al Portapapeles:** Botones para copiar fácilmente URLs, cuerpos de solicitud/respuesta.

## Tecnologías Utilizadas
* **HTML5**
* **CSS3** (estilos embebidos en el HTML)
* **JavaScript Vainilla** (ECMAScript 6+ Modules)

## Configuración y Uso

1.  **Credenciales API:** Necesitarás un `Client ID` y `Client Secret` válidos proporcionados por Rappi para el entorno que deseas utilizar (producción o sandbox, según corresponda a las URLs base).
2.  **Abrir en el Navegador:** Simplemente abre el archivo `index.html` (o el nombre que le hayas dado) en un navegador web moderno.
3.  **Autenticación:**
    * Selecciona el país correspondiente.
    * Ingresa tu `Client ID` y `Client Secret`.
    * Haz clic en "Autenticar".
4.  **Operar:** Una vez autenticado, podrás utilizar las diferentes secciones para gestionar tu catálogo y pedidos. El visor JSON en la parte inferior te ayudará a entender las interacciones con la API.

## Notas Importantes
* **Seguridad de Credenciales:** Dado que es una aplicación puramente frontend, el Client ID y Client Secret se manejan en el lado del cliente. Para un entorno de producción real, estas credenciales sensibles deberían manejarse a través de un backend (BFF - Backend For Frontend) para mayor seguridad.
* **Límites de API:** Ten en cuenta los límites de tasa de la API de Rappi al usar la aplicación, especialmente con la función de polling de pedidos.
* **Flujo de Edición de Productos:** La "edición" de productos en Rappi a menudo implica un flujo de eliminar el producto existente y crear uno nuevo con los datos actualizados. Esta aplicación sigue ese paradigma.

## Estructura del Código
El código está contenido en un único archivo HTML:
* `<style>`: Contiene todos los estilos CSS.
* `<body>`: Define la estructura de la aplicación y los contenedores para los modales y el visor JSON.
* `<script type="module">`: Contiene toda la lógica de JavaScript, incluyendo:
    * Variables de estado de la aplicación.
    * Referencias a elementos del DOM.
    * URLs base de la API por país.
    * Funciones para realizar llamadas a la API (`makeApiCall`).
    * Funciones de renderizado para cada sección y modal.
    * Manejadores de eventos para la interacción del usuario.
    * Lógica de negocio para cada funcionalidad (catálogo, pedidos, etc.).
