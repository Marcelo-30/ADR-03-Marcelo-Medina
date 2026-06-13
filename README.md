ADR-03: Estilo arquitectónico de CatalogoAPP
Campo	Valor
Autor	Marcelo Medina
Fecha	12/06/2026
Estado	Aceptado

Contexto

CatalogoAPP es una aplicación web para pequeños vendedores y revendedores de ropa. El sistema busca permitir la administración y visualización de productos como prendas, categorías, tallas, colores, precios e imágenes, evitando que el vendedor dependa únicamente de redes sociales, notas o archivos separados para mostrar su catálogo.

En decisiones anteriores se aceptó usar C#, ASP.NET Core MVC, Entity Framework Core, SQL Server y GitHub como base tecnológica del proyecto. Además, en el ADR-02 se documentaron las vistas arquitectónicas iniciales del sistema: vista lógica, vista física, vista de despliegue y vista de procesos.

La decisión actual consiste en definir el estilo arquitectónico principal que guiará la construcción de CatalogoAPP. Esta decisión debe ayudar a mantener el sistema organizado, entendible y fácil de defender en clase, considerando que el proyecto se desarrollará durante el cuatrimestre y que todavía no requiere una infraestructura distribuida compleja.
