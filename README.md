Proyecto de Gestión de Venta de Entradas - Sala de Teatro

Objetivo:
  Desarrollar un sistema para gestionar la venta de entradas de una sala de teatro independiente, incluyendo:
    •	Registro de espectáculos.
    •	Gestión de salas y disponibilidad.
    •	Venta de entradas.
    •	Visualización de espectáculos próximos y pasados.
  
Tecnologías
  •	Java 17+
  •	Spring Boot
  •	Hibernate / JPA
  •	PostgreSQL
  •	Maven
  •	Docker 
  
Testing
  •	JUnit (tests unitarios)
  •	Mockito (mocks y pruebas de servicios)
  •	Postman (pruebas de la API REST manualmente)
  Arquitectura del Proyecto
  •	API RESTful: desarrollada en Spring Boot.
  •	Modelo de entidades: Java + JPA.
  •	Base de datos: PostgreSQL.
  •	Separación en capas: Controller, Service, Repository, Model.
  
Diagrama de Clases. Entidades principales:

  ![image](https://github.com/user-attachments/assets/880bbfb4-5efb-49b8-9339-e5447119e345)

•	Usuario: puede registrar espectáculos.
  •	Sala (abstracta): representa un espacio físico donde se realizan espectáculos.
    o	SalaCerrada: sala cerrada con distintos tipos de precio.
    o	Anfiteatro: sala abierta con precio único.
  •	Espectáculo: representa un show en una sala, con fecha, hora y precio.
  •	Entrada: representa la compra de una entrada para un espectáculo.

Modelo de Datos (Base de Datos)
Tablas principales:

  usuario {
    id,
    nombre,
    email
  }
  sala {
    id,
    nombre,
    capacidad,
    tipo_precio
  }
  espectaculo {
    id,
    artista,
    fecha,
    hora,
    precio_entrada,
    duracion,
    tipo_show,
    sala_id,
    usuario_id
  }
  
  entrada {
    id,
    fecha_compra,
    precio,
    espectaculo_id
  }

Diagrama Entidad-Relación
  •	usuario (1) ------ (N) espectaculo
  •	sala (1) ------ (N) espectaculo
  •	espectaculo (1) ------ (N) entrada

Endpoints principales de la API
  •	GET /api/espectaculos → Listar espectáculos disponibles.
  •	POST /api/espectaculos → Registrar un nuevo espectáculo.
  •	POST /api/entradas → Comprar una entrada para un espectáculo.
  •	GET /api/entradas/{id} → Consultar los datos de una entrada comprada.

Testing
  •	Pruebas unitarias de servicios usando JUnit.
  •	Mocks de dependencias usando Mockito.
  •	Pruebas de endpoints manuales mediante Postman.

Justificación de Tecnologías
  •	Spring Boot: permite crear rápidamente servicios REST bien estructurados.
  •	Hibernate / JPA: facilita la persistencia de objetos Java en la base de datos.
  •	PostgreSQL: base de datos robusta, gratuita y ampliamente usada en producción.
  •	Docker (opcional): para empaquetar y desplegar fácilmente la aplicación.



NUEVA DOCUMENTACION:

Proyecto de Gestión de Venta de Entradas - Sala de Teatro

Objetivo:
  Desarrollar un sistema para gestionar la venta de entradas de una sala de teatro independiente, incluyendo:
    •	Registro de espectáculos.
    •	Gestión de salas y disponibilidad.
    •	Venta de entradas.
    •	Visualización de espectáculos próximos y pasados.
  
Tecnologías
  •	Node.js (v18+)
  • TypeScript
  • NestJS (framework backend)
  • Prisma ORM
  • PostgreSQL
  • Docker
  • npm/yarn (gestor de dependencias)
  
Testing
  • Jest (tests unitarios)
  • Supertest (pruebas de endpoints)
  • Postman o Thunder Client (pruebas manuales de la API REST)

Arquitectura del Proyecto
  • API RESTful: desarrollada con NestJS.
  • Modelo de entidades: TypeScript + Prisma ORM.
  • Base de datos: PostgreSQL.
  • Separación en capas: Controller, Service, Repository, DTOs y Entities.

Diagrama de Clases. Entidades principales:

  ![image](https://github.com/user-attachments/assets/880bbfb4-5efb-49b8-9339-e5447119e345)

•	Usuario: puede registrar espectáculos.
  •	Sala (abstracta): representa un espacio físico donde se realizan espectáculos.
    o	SalaCerrada: sala cerrada con distintos tipos de precio.
    o	Anfiteatro: sala abierta con precio único.
  •	Espectáculo: representa un show en una sala, con fecha, hora y precio.
  •	Entrada: representa la compra de una entrada para un espectáculo.

Modelo de Datos (Base de Datos)
Tablas principales:

  usuario {
    id,
    nombre,
    email
  }
  sala {
    id,
    nombre,
    capacidad,
    tipo_precio
  }
  espectaculo {
    id,
    artista,
    fecha,
    hora,
    precio_entrada,
    duracion,
    tipo_show,
    sala_id,
    usuario_id
  }
  
  entrada {
    id,
    fecha_compra,
    precio,
    espectaculo_id
  }

Diagrama Entidad-Relación
  •	usuario (1) ------ (N) espectaculo
  •	sala (1) ------ (N) espectaculo
  •	espectaculo (1) ------ (N) entrada

Endpoints principales de la API
  •	GET /api/espectaculos → Listar espectáculos disponibles.
  •	POST /api/espectaculos → Registrar un nuevo espectáculo.
  •	POST /api/entradas → Comprar una entrada para un espectáculo.
  •	GET /api/entradas/{id} → Consultar los datos de una entrada comprada.

Testing
  •	Pruebas unitarias de servicios con Jest
  • Pruebas de endpoints con Supertest
  • Pruebas manuales mediante Postman o Thunder Client

Justificación de Tecnologías
  •	NestJS: framework estructurado con arquitectura limpia, similar a Spring Boot, ideal para APIs escalables.
  • Prisma: ORM moderno, tipado y con autocompletado, simplifica el trabajo con bases de datos relacionales.
  • PostgreSQL: base de datos robusta, gratuita y ampliamente usada en producción.
  • Docker: para empaquetar y desplegar fácilmente la aplicación.
  • TypeScript: permite tipado fuerte y una experiencia de desarrollo más robusta en el ecosistema JS.

Cambios conceptuales importantes:
  •De JPA a Prisma:
    Prisma ofrece una forma moderna y declarativa de manejar bases de datos, generando tipos TypeScript automáticamente. No necesitás escribir tantos mapeos a mano como con JPA.
  
  •De Spring Boot a NestJS:
    NestJS está muy inspirado en la arquitectura de Spring (inyección de dependencias, controladores, servicios, etc.), lo cual te da una transición más suave si vienes de Java.
  
  •De Maven a npm/yarn:
    npm o yarn se usan como gestor de paquetes y scripts de build en lugar de Maven.
  
  •De JUnit + Mockito a Jest + Supertest:
    Jest unifica pruebas unitarias y mocks fácilmente, mientras que Supertest permite pruebas de endpoints HTTP de manera programada (en vez de solo manual con Postman).
