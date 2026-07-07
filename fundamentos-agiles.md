# Resolución: Práctica 1 - Metodologías de Desarrollo en Cascada

**Alumno:** Jerónimo Laborda
**Materia:** Metodologías Ágiles (2026)
**Contexto de Práctica:** Ciclo de vida estructurado (Cascada) aplicado a un Sistema de Gestión de Inventario.

---

## 1. Análisis de Requerimientos

### Ejercicio 1: Requisitos Funcionales y No Funcionales

#### Requisitos Funcionales (RF)
1. **RF-01 (Autenticación):** El sistema debe permitir el inicio de sesión y cierre de sesión seguro para usuarios administradores y operadores.
2. **RF-02 (Alta de Productos):** El sistema debe permitir registrar un nuevo producto capturando: Nombre, Código de Barra (SKU), Categoría, Stock Inicial, Precio Unitario y Proveedor.
3. **RF-03 (Modificación y Baja):** El sistema debe permitir editar los datos de un producto existente y realizar la baja lógica del mismo.
4. **RF-04 (Control de Stock):** El sistema debe registrar las entradas (compras) y salidas (ventas/mermas) de mercadería, actualizando el inventario en tiempo real.
5. **RF-05 (Alertas de Stock Mínimo):** El sistema debe listar y emitir una alerta visual cuando un producto alcance su punto de reposición configurado.

#### Requisitos No Funcionales (RNF)
1. **RNF-01 (Disponibilidad):** La aplicación web debe mantener una disponibilidad del 99.5% durante el horario comercial operativo.
2. **RNF-02 (Rendimiento):** El tiempo de respuesta para las consultas de stock y la renderización de las tablas de inventario no debe superar los 2 segundos.
3. **RNF-03 (Seguridad):** Todas las contraseñas en la base de datos deben almacenarse cifradas mediante un algoritmo robusto (ej. BCrypt).
4. **RNF-04 (Portabilidad/Compatibilidad):** El sistema debe ser una aplicación web completamente responsiva y compatible con los navegadores modernos (Chrome, Firefox, Safari, Edge).

---

### Ejercicio 2: Caso de Uso "Agregar un nuevo producto"

* **ID:** CU-01
* **Nombre:** Agregar un nuevo producto.
* **Actor Principal:** Operador de Inventario / Administrador.
* **Precondición:** El usuario debe estar autenticado en el sistema y posicionado en el panel de inventario.
* **Flujo Básico (Felicidad):**
  1. El actor hace clic en el botón "Agregar Producto".
  2. El sistema despliega un formulario solicitando los datos del producto (Nombre, SKU, Categoría, Stock, Precio).
  3. El actor completa todos los campos obligatorios y presiona "Guardar".
  4. El sistema valida que el SKU no esté duplicado y que los valores numéricos sean positivos.
  5. El sistema persiste el nuevo registro en la base de datos.
  6. El sistema muestra un mensaje de éxito: "Producto registrado correctamente" y refresca la grilla de inventario.
* **Flujos Alternativos / Excepciones:**
  * **4.a. SKU Duplicado:** El sistema detecta que el código ya existe, detiene la persistencia, marca el campo en rojo y muestra el mensaje: "Error: El SKU ingresado ya pertenece a otro producto".
  * **4.b. Campos Vacíos:** El sistema detecta que faltan datos obligatorios, bloquea el envío y muestra el mensaje: "Por favor, complete todos los campos marcados con asterisco (*) ".
* **Postcondición:** El nuevo producto queda disponible en el catálogo y su stock inicial impacta en los totales.

---

## 2. Diseño del Sistema

### Ejercicio 3: Diagrama de Flujo de Datos (DFD - Nivel 1)

```mermaid
graph TD
    User([Operador/Admin]) -->|1. Datos del Producto| Form[Formulario Web Frontend]
    Form -->|2. Petición POST /api/productos| Controller[Controlador de Productos Backend]
    
    subgraph Servidor de Aplicación Backend
        Controller -->|3. Validar Datos y SKU| Service[Servicio de Lógica de Negocio]
    end
    
    subgraph Capa de Datos
        Service -->|4. INSERT INTO productos| DB[(Base de Datos SQL)]
        DB -->|5. Confirmación de Persistencia| Service
    end
    
    Service -->|6. Respuesta HTTP 201 Created| Controller
    Controller -->|7. Mensaje de Éxito e Inventario Actualizado| Form
    Form -->|8. Renderiza Alerta y Refresca Tabla| User
