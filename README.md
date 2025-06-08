# Lab 04 - Testing con Jest 🧪

Este repositorio contiene las pruebas unitarias desarrolladas con **Jest y Testing Library** para el proyecto **RoomieYA**, como parte del curso **Ingeniería de Software II (2025-1)**.

## 👤 Autor

- Jefferson Ricardo De La Cruz Villa

---

## 📌 Historia de Usuario (Sprint 2)

**HU:** Como usuario del sistema, quiero enviar solicitudes de mantenimiento para reportar problemas en el alojamiento y recibir alertas sobre el estado de dichas solicitudes.

### ✅ Tareas completadas

| ID_TAREA | Tarea                         | Rol       | Descripción técnica |
|----------|-------------------------------|-----------|---------------------|
| TA001    | Diseñar formulario de solicitud | Frontend  | Crear formulario para que los usuarios ingresen detalles del mantenimiento. |
| TA002    | Crear API para enviar solicitud | Backend   | Programar endpoint para registrar solicitudes de mantenimiento. |

---

## ✅ Escenarios de prueba – HU: Enviar solicitud de mantenimiento

### 🟢 Happy Paths

**Se visualiza correctamente el formulario de solicitud**  
- **Precondición**: El usuario ha iniciado sesión correctamente.  
- **Acción**: Navega a la sección de “Mantenimiento” y accede al botón "Enviar solicitud".  
- **Resultado esperado**: Se muestra un formulario con campos: descripción, tipo de problema y botón de envío.

**Se permite escribir en el campo de descripción**  
- **Acción**: El usuario escribe una descripción válida (por ejemplo: "fuga de agua en el baño").  
- **Resultado esperado**: El valor escrito aparece en pantalla y es editable.

**El botón de envío se habilita con datos válidos**  
- **Acción**: Se completan todos los campos obligatorios del formulario.  
- **Resultado esperado**: El botón "Enviar solicitud" se habilita correctamente.

**La solicitud se envía correctamente al backend**  
- **Acción**: El usuario hace clic en "Enviar solicitud".  
- **Resultado esperado**:  
  - Se realiza una petición POST al endpoint `/api/solicitudes-mantenimiento`.  
  - Se recibe una confirmación de éxito.  
  - El formulario se limpia y se muestra un mensaje de éxito.

**El sistema responde con confirmación visual**  
- **Acción**: Luego de enviar, se visualiza una alerta como: “Solicitud registrada correctamente”.  
- **Resultado esperado**: El usuario tiene certeza de que su solicitud fue recibida.

---

### 🔴 Unhappy Paths

**El usuario intenta enviar sin completar los campos**  
- **Acción**: Hace clic en “Enviar solicitud” sin ingresar datos.  
- **Resultado esperado**:  
  - No se envía nada al backend.  
  - Se muestran mensajes de error bajo los campos vacíos: “Este campo es obligatorio”.

**La descripción contiene solo espacios**  
- **Acción**: El usuario escribe `"   "` como descripción.  
- **Resultado esperado**:  
  - El botón permanece deshabilitado o se bloquea el envío.  
  - Se muestra mensaje de validación: “Ingrese una descripción válida”.

**El servidor falla al recibir la solicitud**  
- **Simulación**: El backend responde con un error 500.  
- **Resultado esperado**:  
  - Se muestra mensaje de error: “No se pudo enviar la solicitud. Intente más tarde”.  
  - El formulario no se borra.

**Error de conexión con el servidor**  
- **Simulación**: Se desconecta el backend o el usuario pierde conexión.  
- **Resultado esperado**:  
  - Se captura el error.  
  - Se muestra mensaje: “Error de red. Verifique su conexión”.

---

## 🧪 Cómo ejecutar las pruebas

1. Clona el repositorio:
   ```bash
   git clone https://github.com/Jefferson062615/lab-04-test-frontend.git
   cd lab-04-test-frontend
