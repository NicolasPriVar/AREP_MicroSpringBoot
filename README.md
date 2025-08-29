# 📘 MiniSpark Framework

Este proyecto es una implementación ligera de un framework inspirado en **Spring Boot y SparkJava**, que permite definir controladores, rutas y manejar peticiones HTTP de manera sencilla usando anotaciones y reflexión en Java.  

---

## 🚀 ¿Qué hace este framework?

- Permite crear aplicaciones web ligeras en Java.  
- Expone controladores con anotaciones como `@RestController` y `@GetMapping`.  
- Resuelve parámetros de métodos mediante anotaciones como `@RequestParam`.  
- Soporta archivos estáticos (HTML, CSS, JS, imágenes).  
- Implementa un servidor HTTP básico con Java Sockets.  

---

## 📂 Explicación de las clases y anotaciones

### `App`
Clase principal que inicia la aplicación. Se encarga de:
- Cargar los componentes (controladores y rutas anotadas).  
- Iniciar el servidor HTTP embebido.  

---

### `GetMapping`
Anotación personalizada usada para marcar métodos en un controlador que responden a una ruta HTTP **GET**.  
- Su valor (`value`) define la URL del endpoint.  

---

### `HelloController`
Ejemplo de un controlador REST que:
- Usa la anotación `@RestController`.  
- Define métodos mapeados a rutas (`/`, `/hello`, `/pi`) usando `@GetMapping`.  
- Responde con mensajes o valores calculados.  

---

### `MiniSpark`
El núcleo del framework. Sus responsabilidades incluyen:  
- Iniciar el servidor HTTP en un puerto fijo.  
- Manejar peticiones y respuestas a través de **sockets**.  
- Servir archivos estáticos desde un directorio.  
- Registrar rutas dinámicas (GET).  
- Cargar automáticamente controladores anotados con `@RestController` y sus métodos `@GetMapping`.  
- Resolver parámetros de entrada usando `@RequestParam`.  

En resumen: es el motor que conecta las peticiones entrantes con el código del usuario.  

---

### `Request`
Representa la información de una petición HTTP. Contiene:  
- Método (GET, POST, etc.).  
- Ruta solicitada.  
- Parámetros de consulta (`queryParams`).  
- Cuerpo (`body`).  

---

### `RequestParam`
Anotación usada en parámetros de métodos de un controlador para mapear valores desde la query string de la URL.  
Ejemplo: `?name=Nico` se inyecta en un parámetro con `@RequestParam("name")`.  

---

### `Response`
Representa la respuesta HTTP generada por un endpoint. Contiene:  
- Tipo de contenido (`Content-Type`).  
- Cuerpo de la respuesta.  

---

### `RestController`
Anotación que marca una clase como controlador REST.  
- Es necesaria para que `MiniSpark` la detecte y registre sus métodos anotados.  

---

### `Route`
Interfaz funcional que define cómo se maneja una ruta.  
- Recibe un `Request` y un `Response`.  
- Devuelve un `String` que corresponde al contenido de la respuesta HTTP.  

