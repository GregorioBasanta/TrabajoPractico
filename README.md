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

Documentación Actualizada: Proyecto de Gestión de Venta de Entradas - Sala de Teatro

Objetivo
  Desarrollar un sistema para gestionar la venta de entradas de una sala de teatro independiente, que incluya:
    •	Registro de espectáculos
    •	Gestión de salas y disponibilidad
    •	Venta de entradas
    •	Visualización de espectáculos próximos y pasados

Tecnologías
  •	Node.js (v18+)
  •	TypeScript
  •	NestJS (framework backend)
  •	TypeORM (ORM para base de datos)
  •	PostgreSQL
  •	Docker
  •	npm/yarn (gestor de dependencias)

Testing
  •	Jest (tests unitarios)
  • Supertest (pruebas de endpoints)
  • Postman o Thunder Client (pruebas manuales de la API REST)

Arquitectura del Proyecto
  •	API RESTful: Desarrollada con NestJS
  •	Modelo de entidades: TypeScript + TypeORM
  •	Base de datos: PostgreSQL
  •	Separación en capas: Controller, Service, Repository, DTOs y Entities

Diagrama de Clases
![image](https://github.com/user-attachments/assets/16ab8bac-7125-4d6b-a407-10c5a20f6305)

  Entidades principales
    •	Usuario: Se lo asocia con una entrada. Es como si la sacara, pero no es el que maneja la logica del negocio.
    •	Sala (abstracta): Representa un espacio físico donde se realizan espectáculos
    •	SalaCerrada: Sala cerrada con distintos tipos de precio
    •	Anfiteatro: Sala abierta con precio único
    •	Show: Representa un show en una sala, con fecha, hora y precio. Esta se carga sin ningun usuario administrador.
    •	Entrada: Representa la compra de una entrada para un espectáculo.

Modelo de Datos (Base de Datos)
  Tablas principales  
    •	usuario { id, nombre, email }
    •	sala { id }
    •	espectaculo { id, nombre, artista, fecha, hora, duracion, tipo_show, capacidadDisponible, sala_id }
    •	entrada { id, fecha_compra, tiop, precio, show_id, usuario_id }
  
  Diagrama Entidad-Relación
    •	usuario (1) ------ (N) entrada
    •	sala (1) ------ (N) show
    •	show (1) ------ (N) entrada
  
Endpoints principales de la API
  •	POST /api/shows: Registrar un nuevo espectáculo
  •	GET /api/shows: Listar espectáculos disponibles
  •	POST /api/entradas: Comprar una entrada para un espectáculo
  •	GET /api/entradas: Listar las entradas disponibles
  •	POST /api/usuarios: Registrar un nuevo usuario
  •	GET /api/usuarios: Listar usuarios disponibles
  •	GET /api/salas: Listar salas disponibles

Endpoints secundarios de la API 
  •	GET /api/shows/{id}: Listar un espectáculo por id
  •	GET /api/entradas/{id}: Listar una entrada por id 
  •	GET /api/usuarios/{id}: Listar un usuario por id

Endpoints terciaros de la API
  Le pongo endpoints terciarios, aunque en realidad son importantes, pero estos se utilizan dentro de los service para actualizar la base de datos con la lógica del negocio.
  •	PUT /api/shows: Actualiza un show 
  •	GET /api/show/{id}/disponibilidad: Verifica la disponibilidad de un show con el id.

Testing
  •	Pruebas unitarias de servicios con Jest
  •	Pruebas de endpoints con Supertest
  •	Pruebas manuales mediante Postman o Thunder Client

Justificación de Tecnologías
  •	NestJS: Framework estructurado con arquitectura limpia, ideal para APIs escalables
  •	TypeORM: ORM que permite mapeo objeto-relacional con decorators, integración fácil con NestJS y soporte a múltiples bases relacionales
  •	PostgreSQL: Base de datos robusta, gratuita y ampliamente usada en producción
  •	Docker: Para empaquetar y desplegar fácilmente la aplicación
  •	TypeScript: Permite tipado fuerte y una experiencia de desarrollo más robusta en el ecosistema JS

Cambios conceptuales importantes
  •	De JPA a TypeORM: TypeORM ofrece un mapeo declarativo mediante decorators, integración nativa con TypeScript y NestJS, y soporte para repositorios que facilita la manipulación de la base de datos.
  •	De Spring Boot a NestJS: NestJS está muy inspirado en la arquitectura de Spring (inyección de dependencias, controladores, servicios, etc.), lo cual da una transición suave para desarrolladores Java.
  •	De Maven a npm/yarn: npm o yarn se usan como gestor de paquetes y scripts de build en lugar de Maven.
  •	De JUnit + Mockito a Jest + Supertest: Jest unifica pruebas unitarias y mocks fácilmente, mientras que Supertest permite pruebas programadas de endpoints HTTP.

**Instrucciones**
API para la gestion de salas, shows y venta de entradas de teatro, desarrollada con NestJS y PostgreSQL.

Indicaciones:
  •	Para bajar la imagen de docker y poder correr la API tenes que:
      Clonar el repositorio: 
        git clone https://github.com/tu-usuario/teatro-api.git
        cd teatro-api
  • Configurar las variables del entorno:
      Copiar el archivo .env.example a .env y completar los valores necesarios, solo falta DB_PASSWORD
        cp .env.example .env
  •	Ejecutar con Docker Compose:
      npm run docker:up
  • Para ver que se hayan creado correctamente la imagen y los contenedores esten corriendo: 
      npm run docker:ps
  •	La API se ecnuentra en el puerto 3000, link:
      http://localhost:3000

Comandos útiles

      Comando                                               Descripción
      npm run docker:down                                   Detener y eliminar contenedores
      npm run docker:up                                     Arrancar y crear o recrear contenedores
      npm run docker:ps                                     Para ver si arrancaron correctamente los contenedores
      docker-compose logs -f api                            Ver logs de la API
      docker-compose exec db psql -U postgres -d teatro-db      Acceder a la base de datos
      docker-compose restart api                            Reiniciar solo el servicio API
      npm run test                                          Para realizar los testeos unitarios.
      docker-compose exec api npm run test:e2e              Para realizar un testeo e2e.

JSON utiles para probar los POST
Para empezar aclarar que solo existen dos salas, estas las cargue manualmente ya que solo existen dos. Esto lo deberia haber echo con un metodo POST para hacerlo mas escalable, me di cuenta cuando cargue la base de datos. Tambien junto con salas cometi el error de hacer poco escalable, que estas tienen su dato de capacidad y de precio de las entradas fijo.
Las demas clases se cargan con los siguientes JSON.

•	JSON para Usuarios:
    {
  "nombre": "Lucía González",
  "email": "lucia@example.com"
    }

•	JSON para shows:
    {
      "nombre": "Stand Up Night",
      "artista": "Juan Pérez",
      "fecha": "2025-06-15",
      "hora": "21:00",
      "duracion": 90,
      "tipo": "musical",
      "salaId": 1
    }
•	JSON para entradas:
    {
      "usuarioId": 2,
      "showId": 1,
      "tipoEntrada": 1
    }

Al cargar los datos hay que tener en cuenta varios puntos:
  • Los id son autoincrementales.
  •	En show, la fecha y la hora se puede superponer con otro show, ademas, hay una hora de limpieza antes de cada show. Habria que agregar un horario de trabajo por ejemplo de 08:00hs a 24:00hs.
  •	En show, el tipo solo puede ser "infantil", "musical", "obra de teatro".
  •	En show, la salaId sera 1 o 2. Son las unicas salas creadas.
  •	En entradas, se debera pasar un id de usuario y show valido, se puede pasar un id de show que exista pero la obra ya haya pasado, en este caso se devolvera un error. Se podria agregar que si el usuario ya tiene una funcion en ese horario no pueda sacar otra.
  •	En entradas, el parametro de tipoEntrada solo puede ser 1 o 2, sino arrojara un error. Esto es para cuando el show se lleva en la sala cerrada, ya que el costo sera distinto. Si la sala en el anfiteatro, es indiferente que numero se pase ya que no se tendra en cuenta el dato. Habria que mejorar el sistema de entradas entre tipo 1 o 2, como por ejemplo, poner que cantidad habria de cada una. En este programa se trabaja de la misma forma que tipo de entrada sea, lo unico que cambia es el valor.

Puntos a mejorar en un futuruo.
  •	Se podria crear un sistema de login para que el usuario final sea el que saca las entradas, o que el usuario administrador solo pueda crear shows o nuevas salas.
  •	Como ya fue mencionado, que las salas puedan crearse con mas o menos espacio, o este se pueda actualizar, por si se remodala la sala por ejemplo. Y que los precios sean modificables.
  •	Tambien fue mencionado, pero que los shows tengan horarios limites, para que no se puedan cargar falsos shows en los horarios donde el teatro esta cerrado.
  •	Un sistema de gestion de dinero para realmente realizar el pago de la entrada.
  •	Un sistema de eleccion de asientos. Aca tambien se podria agregar el metodo de tipo de entrada antes mencionado, para que haya x cantidad de cada una.
  •	Un sistema de gestion de puntos para los usuarios. Como si fuera un beneficio.
  •	Que filtre la busqueda para los shows que solo estan en cartelera o son proximos y que no se muestren todos.
