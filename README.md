# MS-APIGATEWAY
"Puerta de enlace (API Gateway) construida con Spring Cloud para el proyecto AutoMaster. Gestiona el tráfico, centraliza las rutas y protege el acceso a los distintos microservicios de la concesionaria."


🚪 API Gateway (Puerta de Enlace)

Este repositorio contiene el API Gateway basado en Spring Cloud Gateway. Actúa como el único punto de entrada (Single Point of Entry) para toda nuestra arquitectura de microservicios de la concesionaria AutoMaster.

🎯 ¿Cuál es su función?

En lugar de que los clientes (Postman, Frontend web, aplicaciones móviles) tengan que conocer y recordar los puertos individuales de cada microservicio (8079,8080,8081,8082,8083,8084,8085,8086,8087,8088,8089,), envían todas sus peticiones directamente aquí. El API Gateway recibe la solicitud, consulta con Eureka para saber a dónde debe ir, y redirige el tráfico de forma automática e invisible para el usuario.

⚙️ Características principales

Enrutamiento Centralizado (Routing): Redirige las peticiones a su destino correcto basándose en la ruta de la URL (por ejemplo, todo lo que entra por /api/v1/modelos se envía automáticamente al ms-modelos).

Integración nativa con Eureka: No utiliza direcciones IP estáticas. Resuelve las rutas de forma dinámica preguntándole al servidor Eureka dónde están alojados los microservicios en ese momento.

Seguridad y Filtros Globales: Es el lugar ideal para configurar políticas globales como el manejo de CORS, validación de tokens de seguridad (JWT) y bloqueos, protegiendo a los microservicios para que no reciban peticiones no autorizadas.

Balanceo de Carga (Load Balancing): Si existen múltiples instancias de un mismo microservicio levantadas, el Gateway reparte el tráfico equitativamente entre ellas para evitar saturaciones.

