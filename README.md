# ADR-03: Estilo arquitectónico de CatalogoAPP

| Campo  | Valor          |
| ------ | -------------- |
| Autor  | Marcelo Medina |
| Fecha  | 12/06/2026     |
| Estado | Aceptado       |

---

## Contexto

CatalogoAPP es una aplicación web para pequeños vendedores y revendedores de ropa. El sistema busca permitir la administración y visualización de productos como prendas, categorías, tallas, colores, precios e imágenes, evitando que el vendedor dependa únicamente de redes sociales, notas o archivos separados para mostrar su catálogo.

En decisiones anteriores se aceptó usar C#, ASP.NET Core MVC, Entity Framework Core, SQL Server y GitHub como base tecnológica del proyecto. Además, en el ADR-02 se documentaron las vistas arquitectónicas iniciales del sistema: vista lógica, vista física, vista de despliegue y vista de procesos.

La decisión actual consiste en definir el estilo arquitectónico principal que guiará la construcción de CatalogoAPP. Esta decisión debe ayudar a mantener el sistema organizado, entendible y fácil de defender en clase, considerando que el proyecto se desarrollará durante el cuatrimestre y que todavía no requiere una infraestructura distribuida compleja.

---

## Decisión

Se decidió utilizar un estilo arquitectónico **cliente-servidor con arquitectura en capas basada en MVC**.

El sistema funcionará como una aplicación web donde el usuario accede desde un navegador y realiza acciones como consultar productos o administrar el catálogo. Del lado del servidor, ASP.NET Core MVC se encargará de recibir las peticiones, procesarlas y devolver las vistas correspondientes.

La aplicación se organizará por responsabilidades en capas principales:

* **Capa de presentación:** contiene las vistas Razor, archivos CSS, imágenes y elementos visuales del catálogo.
* **Capa de control:** contiene los controladores, que reciben las solicitudes del navegador y coordinan la respuesta.
* **Capa de dominio o aplicación:** contiene los modelos principales del sistema, como productos, categorías, tallas, colores y precios.
* **Capa de acceso a datos:** utiliza Entity Framework Core para comunicarse con SQL Server y guardar la información del catálogo.

### ¿Por qué?

Este estilo resuelve mejor el problema de CatalogoAPP porque el sistema necesita ser una aplicación web sencilla de usar, centralizada y mantenible. El vendedor puede administrar sus productos desde el navegador y los clientes pueden consultar el catálogo sin instalar una aplicación adicional.

La arquitectura cliente-servidor permite separar claramente el navegador del usuario y la aplicación que se ejecuta en el servidor. Esto facilita que el sistema pueda ser consultado desde distintos dispositivos mientras los datos permanecen centralizados.

La organización en capas basada en MVC ayuda a separar responsabilidades. Las vistas se enfocan en mostrar la información, los controladores manejan las solicitudes, los modelos representan los datos del catálogo y la capa de acceso a datos se encarga de la persistencia.

Esta separación hace que sea más fácil agregar funcionalidades como filtros por categoría, carga de imágenes, gestión de inventario o edición de productos sin mezclar toda la lógica en un solo lugar.

También es una decisión adecuada para el alcance actual del proyecto, ya que permite construir una primera versión funcional sin agregar complejidad innecesaria como microservicios, eventos distribuidos o funciones serverless.
