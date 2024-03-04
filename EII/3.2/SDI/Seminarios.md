## Seminario 1:

### Protocolo HTTP:

#### Métodos:
- GET: Para recuperar un recurso. La información viaja en la URL.
- POST: Para crear un nuevo recurso La información viaja en la petición.
- PUT: Para modificar completamente el recurso
- DELETE: Para eliminar un recurso

#### Versiones
- 1.0 Se crean y cierran conexiones por cada petición
- 1.1 Conexiones persistentes. Peticiones paralelas
- 2.0 

## Seminario 2 - Repaso primer parcial:

### ¿Qué elementeo de una aplicación JEE se engarga de recibir las peticiones HTTP y redireccionarlas a servlets específicos?
- El contenedor de Servlets.

### Nombra dos métodos includios en la interfaz Servlet, explica muy brevemente para qué sirven
- doGet()
- doPost()
- ...
- ...

### En un ciclo de vida de un servlet cuantas veces se podría ejecutas la función init() y doGet()
- 1-1
- 0-inf

### Desde un servlet, explica la diferencia funcional entre obtener un valor "nombre" con A) request.getParameter("nombre) B) request.getSession(true).getAttribute("nombre"):
- Ámbito diferente:
  - A) petición actual
  - B) sesión del cliente

### Falta una

### ¿Cuál es la principal ventaja de las JSP sobre tecnologías anteriores?
- Mayor separación entre lógica y ...

### ¿Qué tres tipos de elementos puede contener una JSP?

- JSP
  - Elementos de secuencia
    - Scriptlets
    - Expresiones
    - Declaraciones
  - Directivas
  - Acciones

### Otra que falta

### En una arquitectura MVC en JEE que elemento se utilizaría para implementar el modelo(lógica de negocio y datos)

### ¿En qué consiste el patrón **Facha**da? ¿Cuál es su principal ventaja?
- Interaz único, simple y que reduce el acoplamiento

### ¿Con qué patrón se reduce el acoplamiento?
**Facha**da

### Otra que falta que tiene foto

### Otra que falta que es demasiado larga

### ¿Quién recibe antes una petición, un controlador o un interceptor?

### ¿Cuál es la función del LocaleChangeInterceptor en los sistemas de internacionalización?

### Otra demasiado larga(también la puso en teoría): ¿Según la siguiente configuración que se...?
- Que esté autenticado

### ¿Qué dos tipos de validaciones de datos de entrada podríamos aplicar? Nómbralos...

### Completa el siguiente validador para que se incluya un error en el campo "nombre" del formulario (se puede poner cualquier mensaje de error).
```java

```

### ¿Qué es el objeto Session? Por un ejemplo de uso común.

### ...

### El siguiente servicio debería permitir que un usuario vea los detalles 

### Crea una versión equivalente del método "findAllByUsuario" (implementado en un respositorio) para que pase a...

### Haz las modificicaciones oportunas para que el...