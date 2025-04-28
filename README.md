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
