Implementación inicial de cliente frontend para API Rappi

Cliente frontend completo para interactuar con varios endpoints de la API de Rappi.
Incluye funcionalidades para:

- Autenticación y gestión de token.
- Selección de país para URLs base de API.
- Gestión de Catálogo:
  - CRUD de productos (con y sin variaciones).
  - Visualización de árbol de categorías y atributos.
  - Asociación/Desasociación de productos a tiendas.
- Gestión de Pedidos:
  - Visualización y búsqueda de pedidos.
  - Polling para actualizaciones de pedidos.
  - Acciones de pedido: iniciar picking, reportar factura, solicitar RT, cancelar, handshake (solicitar/validar códigos).
  - Eliminación de productos de un pedido.
  - Sustitución de productos en un pedido (con búsqueda en catálogo).
- Gestión de Tiendas: Visualización de lista de tiendas.
- Utilidades: Visor JSON para depuración de API, notificaciones toast.

Todo implementado con HTML, CSS embebido y JavaScript vainilla (módulo ES).
