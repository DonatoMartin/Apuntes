
# SDI

| Criterios de calificación | Porcentaje    |
| -                         | -             |
| Teoría                    | 40 %          |
| Práctica                  | 60%           |

Sistemas Distribuidos e Internet es una asignatura enfocada en el desarrollo software avanzado, a través de técnicas clásicas y/o ágiles como pueden ser JEE, Spring Boot, Selenium, NodeJs o servicios REST/SOAP, a parte del uso de patrones de diseño en los que se profundizarán más adelante.

| Información general sobre la asignatura                           |
| -                                                                 |
| CV: https://www.campusvirtual.uniovi.es/course/view.php?id=1313   |

## Tabla de contenidos
- [SDI](#sdi)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Plataformas Java](#plataformas-java)
  - [Tema 1 - JEE y Patrones](#tema-1---jee-y-patrones)
    - [Arquitectura Web Básica](#arquitectura-web-básica)
    - [Servlets](#servlets)
    - [Contenedor de servlets/Web container](#contenedor-de-servletsweb-container)
    - [Ciclo de vida](#ciclo-de-vida)
    - [Métodos doGet y doPost](#métodos-doget-y-dopost)
    - [Registro de un servlet](#registro-de-un-servlet)
    - [JSP](#jsp)
  - [Tema 2: Arquitectura MVC con Spring Boot](#tema-2-arquitectura-mvc-con-spring-boot)
  - [Tema 3: Acceso a datos, Autenticación - Control de acceso - Validación en el servidor](#tema-3-acceso-a-datos-autenticación---control-de-acceso---validación-en-el-servidor)
      - [Tipos de patrones:](#tipos-de-patrones)
    - [Introducción a Patrones](#introducción-a-patrones)
    - [Spring Boot](#spring-boot)
      - [Framework Spring](#framework-spring)
      - [Maven](#maven)
  - [Tema 4: Sesión - Roles - Consultas - Búsqueda - Paginación](#tema-4-sesión---roles---consultas---búsqueda---paginación)
    - [Fragmentos](#fragmentos)
      - [Controladores](#controladores)
      - [Cliente](#cliente)
    - [Configuración](#configuración)
      - [@Configuration](#configuration)
      - [@Bean](#bean)
    - [Internacionalización(i18n)](#internacionalizacióni18n)
      - [Configuración](#configuración-1)
      - [Interceptores](#interceptores)
        - [LocaleChangeInterceptor](#localechangeinterceptor)
      - [LocaleResolver](#localeresolver)
      - [Mensajes](#mensajes)
    - [Spring Security](#spring-security)
      - [Autenticación](#autenticación)
      - [Encriptación](#encriptación)
      - [Configuración //TODO](#configuración-todo)
      - [Autorización (HTTPSecurity)](#autorización-httpsecurity)
      - [](#)
  - [Tema 5: Web testing con Selenium](#tema-5-web-testing-con-selenium)
  - [Tema 6: Desarrollo web con Nodejs 1](#tema-6-desarrollo-web-con-nodejs-1)
  - [Tema 7: Desarrollo web con Nodejs 2](#tema-7-desarrollo-web-con-nodejs-2)
  - [Tema 8: Servicios web REST](#tema-8-servicios-web-rest)
  - [Tema 9: Servicios web SOAP](#tema-9-servicios-web-soap)
  - [Glosario](#glosario)

## Plataformas Java

| Plataformas Java          | Características   |
| -                         | -                 |
| Java Standard Edition     | - Para applets    |
|                           | - VM              |
|                           | - Desarrollo y despliegue de aplicaciones Java en escritorios y servidores |
|                           | - Interfaz de usuario rica, rendimiento, versatilidad, portabilidad y seguridad |
| Java Enterprise Edition   | - Se apoya en SE 
|                           | - Servlets, JSP, JSF, Beans
|                           | - Estándar en software empresarial impulsado por la comunidad <br> - Desarrollo de aplicaciones distribuidas y servicios web |
| Java Micro Edition        | - Proporciona un entorno robusto y flexible para aplicaciones en dispositivos móviles y empotrados
|                           | - Incluye perfiles para dispositivos móviles y televisores |
| JavaFX Script             | - Lenguaje de scripting para JavaFX <br> - Desarrollo de interfaces de usuario ricas para aplicaciones de escritorio, móviles, TV y web |

## Tema 1 - JEE y Patrones

### Arquitectura Web Básica

Un cliente (Navegador) envía una petición de un recurso (URL) a un servidor (Servidor HTTP) y éste le responde vía HTTP

Cuando el navegador solicita una página web, recibe la página y desencadena una petición para cada uno de los
recursos asociados a la misma.

### Servlets

Un servlet es una clase Java que hereda de la clase JEE HTTPServlet y que:

- Acepta peticiones de cualquier método HTTP (get, post, put, delete, head, trace, …)
- Responde también usando el protocolo HTTP
- Se ejecuta dentro de un contenedor de Servlets que a su vez está dentro de un servidor de aplicaciones JEE

### Contenedor de servlets/Web container

- Un contenedor define un ambiente estandarizado de ejecución que provee servicios
específicos a los servlets. Por ejemplo, dan servicio a las peticiones de los clientes, realizando
un procesamiento y devolviendo el resultado
- Los servlets tienen que cumplir un contrato con el contenedor para obtener sus servicios.
- Los contratos son interfaces Java.Por ejemplo, la interfaz Servlet.

### Ciclo de vida

**INICIALIZACIÓN**: Una única llamada al metodo “init” por parte del contenedor de servlets
public void init(ServletConfig config) throws ServletException. Se pueden recoger unos
parametros concretos con “getInitParameter” de “ServletConfig”. Estos parámetros se
especifican en el descriptor de despliegue de la aplicación: web.xml
**PETICIONES**: Primera petición a init se ejecuta en un thread que invoca a service. El resto de
peticiones se invocan en un nuevo hilo mapeado sobre service
**DESTRUCCIÓN**: Cuando todas las llamadas desde el cliente cesen o un temporizador del
servidor así lo indique. Se deben liberar recursos retenidos desde init() public void destroy()

### Métodos doGet y doPost
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

### Registro de un servlet

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

### JSP

Java Server Pages es una tecnología para crear páginas web dinámicas. Estas páginas están construidas sobre servlets y vienen a resolver el problema de presentación de los mismos.
Permiten generar HTML directamente por código.

## Tema 2: Arquitectura MVC con Spring Boot
- Spring Boot: es una forma fácil de desarrollar aplicaciones en Spring.

## Tema 3: Acceso a datos, Autenticación - Control de acceso - Validación en el servidor

#### Tipos de patrones:
- Arquitectónicos: Relacionados con el diseño a gran escala y de granularidad gruesa. (Capas)
- Diseño: Relacionados con el diseño de objetos y frameworks de pequeña y mediana escala. (Fachada)
- Estilos: Soluciones de diseño de bajo nivel orientadas a la implementación o al lenguaje (Singleton)

### Introducción a Patrones

**Model-1.5**: JSPs para presentación y control, y JavaBeans para la lógica.
![Model-1.5 diagram](image.png)

**Model-2**: Model-View-Controller = JavaBeans-JSPs-Servlet

![Model-2 diagram](image-1.png)

**Modelo N-capas**: Modelo de Brown n-capas, contiene un patrón fachada entre capas, no permitiendo dependencias a través de estas. 
![Model-layers diagram](image-2.png)
Layers y Tiers:
- Layer: capa arquitectónica (presentación, lógica, persistencia...)
- Tier: capa física (servidor web, servidor de aplicaciones, servidor BBDD)

![Ejemplo layers tiers](image-3.png)

En la asignatura se usarán los siguientes patrones

| Presentación  | Negocio   | Persistencia  |
| -             | -         | -             |
| MVC           | Fachada   | DAO           |
|               | Factoría  | DTO           |
|               |           | Factoría      |
|               |           | Active Record |

### Spring Boot

Spring Boot aumenta la agilidad del desarrollo de aplciaciones en spring.
- Provee opciones de configuración por defecto
- uso opcional de POMS
- Evita generación de código y configuraciones XML presentes en Spring

#### Framework Spring
- Aplicaciones basadas en el patrón MVC
- Soporte completo al desarrollo de ap,licaciones empresariales basadas en POJOs
- Sistema de inyección de dependencias basadas en el IoC container (inversion of Control)
  - Menor consumo de recursos que los EJB
- Gran cantidad de módilos con funcionalidad reutilizable
- Traducción de instrucciones específicas a genéricas

#### Maven
Dominio: http://maven.apache.org
- Permite especificar procesos para muchas acciones 
relativas al desarrollo de software
   Validaciones, compilación, despliegue, pruebas, etc.
- Gestión de dependencias / artefactos (“superlibrerias”) 
  
SpringBoot utiliza Maven con ficheros POM


## Tema 4: Sesión - Roles - Consultas - Búsqueda - Paginación

### Fragmentos
- El uso por defecto de Thymeleaf consiste en retornar una vista correspondiente a una plantilla

- Para ganar fluidez y eficiencia en ocasiones no se retorna una plantilla/página completa
- Una alternativa es retornar una/varias partes de fragmentos de la plantilla/página

- Se suele dar un id al fragmento

#### Controladores
- Referencian frangmentos con \<ruta plantilla> :: \<nombre fragmento>

#### Cliente
- Con JQuery: $(\<selector>).load(\<url>)

### Configuración

#### @Configuration
- No sé

#### @Bean
- Muchas implementan Beans.
- Definen:
  - Funcionalidad necesaria para la propia configuración
  - Funcionalidad común que será utilizada en otras partes de la aplicación
- Se registran al iniciar la aplicación

### Internacionalización(i18n)

#### Configuración
- Hacemos uso de **WebMvcConfigurerAdapter**, una de las clases más genéricas de configuración para añadir **interceptores**

#### Interceptores
- Servlets que ...
- Suelen(o igual siempre) heredar de un interceptor básico(**HandlerInterceptorAdapter**).
- Retornan un Bean.
- El Bean se registra a través del método **addInterceptors()** 
  
##### LocaleChangeInterceptor
- **LocaleChangeInterceptor** es un interceptor *implementado en el framework* relativo a la internacionalización.
  
#### LocaleResolver
- Es un objeto del framework que permite hacer cambios automáticos de idioma.
- Basado en sesiones, cookies y ... accept-language
  
#### Mensajes
- Las cadenas de texto internacionalizadas se definen en ficheros de propiedades(.properties)
- Desde **Thymeleaf** usamos las claves para obtener los mensajes.

### Spring Security
#### Autenticación
- Proceso para validar la identidad del usuario
- Dependencia **spring-boot-starter-security**

#### Encriptación
- **BCryptPasswordEncoder** soporta la encriptación de forma ágil
  - Puede usarse como un bean

#### Configuración //TODO

#### Autorización (HTTPSecurity)
- Sobreesceibimos el método **configure(HttpSecurity http)**
- Permite configurar ...
- 

####






## Tema 5: Web testing con Selenium
## Tema 6: Desarrollo web con Nodejs 1
## Tema 7: Desarrollo web con Nodejs 2
## Tema 8: Servicios web REST
## Tema 9: Servicios web SOAP
## Glosario

| Término | Definición |
|---------|------------|
| URL     | Unique Resource Locator. |
| HTTP    | HyperText Transfer Protocol. protocolo de aplicación utilizado para el intercambio de información en la Web mediante el paso de mensajes. |
| Patrón  | 
| Spring  | Framework basado en JEE que usa el patrón MVC para el desarrollo de aplicaciones  web. Usa un modelo POJO
| POJO    | Modelo basado en clases planas sin herencia de otras 
| Interceptores | Servlets que ...







