

- [SDI](#sdi)
  - [Plataformas Java](#plataformas-java)
- [Tema 1 - JEE y Patrones](#tema-1---jee-y-patrones)
  - [Arquitectura Web Básica](#arquitectura-web-básica)
  - [Servlets](#servlets)
  - [Contenedor de servlets/Web container](#contenedor-de-servletsweb-container)
  - [Ciclo de vida](#ciclo-de-vida)
  - [Métodos doGet y doPost](#métodos-doget-y-dopost)
  - [Registro de un servlet](#registro-de-un-servlet)
  - [JSP](#jsp)
  - [Glosario](#glosario)


# SDI

Sistemas Distribuidos e Internet es una asignatura enfocada en el desarrollo software avanzado, a través de técnicas clásicas y/o ágiles como pueden ser JEE, Spring Boot, Selenium, NodeJs o servicios REST/SOAP, a parte del uso de patrones de diseño en los que se profundizarán más adelante.

| Información general sobre la asignatura |
| - |
| CV: https://www.campusvirtual.uniovi.es/course/view.php?id=1313 |
| Versión de Java utilizada: Java 17 |

## Plataformas Java

| Plataformas Java         | Características  |
|--------------------------|------------------|
| Java Standard Edition    | - Para applets <br> - VM <br> - Desarrollo y despliegue de aplicaciones Java en escritorios y servidores <br> - Interfaz de usuario rica, rendimiento, versatilidad, portabilidad y seguridad |
| Java Enterprise Edition  | - Se apoya en SE <br> - Servlets <br> - JSP <br> - JSF <br> - Beans <br> - Estándar en software empresarial impulsado por la comunidad <br> - Desarrollo de aplicaciones distribuidas y servicios web |
| Java Micro Edition       | - Proporciona un entorno robusto y flexible para aplicaciones en dispositivos móviles y empotrados <br> - Incluye perfiles para dispositivos móviles y televisores |
| JavaFX Script            | - Lenguaje de scripting para JavaFX <br> - Desarrollo de interfaces de usuario ricas para aplicaciones de escritorio, móviles, TV y web |

# Tema 1 - JEE y Patrones

## Arquitectura Web Básica

Un cliente (Navegador) envía una petición de un recurso (URL) a un servidor (Servidor HTTP) y éste le responde vía HTTP

Cuando el navegador solicita una página web, recibe la página y desencadena una petición para cada uno de los
recursos asociados a la misma.

## Servlets

Un servlet es una clase Java que hereda de la clase JEE HTTPServlet y que:

- Acepta peticiones de cualquier método HTTP (get, post, put, delete, head, trace, …)
- Responde también usando el protocolo HTTP
- Se ejecuta dentro de un contenedor de Servlets que a su vez está dentro de un servidor de aplicaciones JEE

## Contenedor de servlets/Web container

- Un contenedor define un ambiente estandarizado de ejecución que provee servicios
específicos a los servlets. Por ejemplo, dan servicio a las peticiones de los clientes, realizando
un procesamiento y devolviendo el resultado
- Los servlets tienen que cumplir un contrato con el contenedor para obtener sus servicios.
- Los contratos son interfaces Java.Por ejemplo, la interfaz Servlet.

## Ciclo de vida

**INICIALIZACIÓN**: Una única llamada al metodo “init” por parte del contenedor de servlets
public void init(ServletConfig config) throws ServletException. Se pueden recoger unos
parametros concretos con “getInitParameter” de “ServletConfig”. Estos parámetros se
especifican en el descriptor de despliegue de la aplicación: web.xml
**PETICIONES**: Primera petición a init se ejecuta en un thread que invoca a service. El resto de
peticiones se invocan en un nuevo hilo mapeado sobre service
**DESTRUCCIÓN**: Cuando todas las llamadas desde el cliente cesen o un temporizador del
servidor así lo indique. Se deben liberar recursos retenidos desde init() public void destroy()

## Métodos doGet y doPost
Son llamados desde el método service(). Reciben interfaces instanciada:

```java
protected void doGet(HttpServletRequest req, HttpServletResponse resp) 
    throws ServletException, IOException {
        . . .
}
protected void doPost(HttpServletRequest req, HttpServletResponse resp) 
    throws ServletException, IOException {
        . . .
}
```

## Registro de un servlet

**Opción 1**: Despliegue de web.xml
```xml
<servlet>
    <servlet-name>HolaMundo</servlet-name>
    <servlet-class>uo.sdi.servlet.HolaMundoServlet</servlet-class>
</servlet>
<!-- Standard Action Servlet Mapping -->
<servlet-mapping>
    <servlet-name>HolaMundo</servlet-name>
    <url-pattern>/HolaMundoCordial</url-pattern>
</servlet-mapping>
```

**Opción 2**: Usando anotaciones

```java
@WebServlet(name = "HolaMundo", urlPatterns = { "/HolaMundoCordial" })
public class HolaMundoServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;
    /**
    * @see HttpServlet#HttpServlet()
    */
    public HolaMundoServlet() {
        super();
        // TODO Auto-generated constructor stub
    }
}
```

## JSP

Java Server Pages es una tecnología para crear páginas web dinámicas. Estas páginas están construidas sobre servlets y vienen a resolver el problema de presentación de los mismos.
Permiten generar HTML directamente por código.

## Glosario

| Término | Definición |
|- | - |
| URL | Unique Resource Locator. |
| HTTP | HyperText Transfer Protocol. protocolo de aplicación utilizado para el intercambio de información en la Web mediante el paso de mensajes. |
