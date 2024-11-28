# Sistema de Gestión de Publicidad en Programas de Televisión

Este proyecto tiene como objetivo gestionar los programas de televisión y sus patrocinadores asociados, así como calcular el costo total de la publicidad en cada programa basado en la duración del anuncio y el precio por segundo. El sistema permite registrar programas, asociar patrocinadores, y calcular el costo de la publicidad en tiempo real.

## Descripción del Sistema

### **Estructura Principal:**

El sistema consta de tres partes principales:

1. **Gestión de Patrocinadores**: Permite registrar patrocinadores, especificando su número de contrato, nombre, duración del anuncio y precio por segundo.
2. **Gestión de Programas**: Permite registrar programas de televisión, asignarles una franja horaria, un responsable y asociar patrocinadores.
3. **Cálculo de Publicidad**: Permite calcular el costo total de la publicidad para un programa basado en los patrocinadores asociados, la duración de sus anuncios y el precio por segundo.

### **Flujo de Trabajo:**

1. **Registrar Patrocinador**: Se registran los patrocinadores con su número de contrato, nombre, duración del anuncio y precio por segundo.
2. **Registrar Programa**: Se crean programas de televisión donde se asocian los patrocinadores mediante su número de contrato.
3. **Calcular Costo de Publicidad**: Se selecciona un programa y, basado en los patrocinadores asociados, se calcula el costo total de la publicidad sumando los costos de cada patrocinador.

## Esquema Lógico Relacional

El esquema lógico relacional se basa en la siguiente estructura de base de datos:

### **Tablas**

1. **Patrocinadores**:

   - **Atributos**:
     - `contrato` (PK): Número de contrato del patrocinador.
     - `nombre`: Nombre del patrocinador.
     - `duracion`: Duración del anuncio en segundos por semana.
     - `precio`: Precio por segundo del anuncio.

   **Relación**: Cada patrocinador puede estar asociado a múltiples programas, pero un programa puede tener múltiples patrocinadores.

2. **Programas**:
   - **Atributos**:
     - `nombre` (PK): Nombre del programa.
     - `responsable`: Nombre del responsable del programa.
     - `franja`: Franja horaria del programa.
     - `patrocinadores`: Lista de contratos asociados a los patrocinadores (relación con la tabla Patrocinadores).

### **Esquema Relacional:**

| Tabla              | Atributos                                             |
| ------------------ | ----------------------------------------------------- |
| **Patrocinadores** | contrato (PK), nombre, duracion, precio               |
| **Programas**      | nombre (PK), responsable, franja, patrocinadores (FK) |

## Clases para el Front-End

En el front-end, cada tabla de la base de datos será representada por una clase en JavaScript. A continuación, se describen las clases correspondientes:

1. **Clase `Patrocinador`**:

   - **Atributos**:
     - `contrato`: Número de contrato del patrocinador.
     - `nombre`: Nombre del patrocinador.
     - `duracion`: Duración del anuncio.
     - `precio`: Precio por segundo.

   **Métodos**:

   - `guardar()`: Guarda los datos del patrocinador en el localStorage.
   - `eliminar()`: Elimina un patrocinador del localStorage.

2. **Clase `Programa`**:

   - **Atributos**:
     - `nombre`: Nombre del programa.
     - `responsable`: Responsable del programa.
     - `franja`: Franja horaria del programa.
     - `patrocinadores`: Array de contratos de patrocinadores asociados.

   **Métodos**:

   - `guardar()`: Guarda el programa en el localStorage.
   - `eliminar()`: Elimina un programa del localStorage.
   - `calcularCosto()`: Calcula el costo total de la publicidad del programa basado en los patrocinadores asociados.

### **Diagrama de Clases**

- **Clase `Patrocinador`**:

  - Atributos: contrato, nombre, duracion, precio
  - Métodos: guardar(), eliminar()

- **Clase `Programa`**:
  - Atributos: nombre, responsable, franja, patrocinadores
  - Métodos: guardar(), eliminar(), calcularCosto()

## Implementación Front-End

El front-end se estructura de la siguiente manera:

1. **HTML**:

   - Se incluyen formularios para registrar programas y patrocinadores.
   - Se utiliza una lista desplegable (`<select>`) para mostrar los programas disponibles.
   - El cálculo de costos se realiza con un formulario que al seleccionar un programa, muestra el costo total basado en los patrocinadores asociados.

2. **CSS**:

   - Se incluyen estilos básicos para la presentación del contenido en una interfaz amigable.

3. **JavaScript**:
   - Los datos se almacenan en el navegador utilizando `localStorage`.
   - Se utiliza JavaScript para manejar la interacción con los formularios y los cálculos.

## Ejemplo de Uso

1. Registra patrocinadores con los siguientes datos:
   - Contrato: 123, Nombre: "Patrocinador A", Duración: 10 segundos, Precio: $5 por segundo.
   - Contrato: 456, Nombre: "Patrocinador B", Duración: 20 segundos, Precio: $3 por segundo.
2. Registra un programa con los siguientes datos:
   - Nombre: "Programa A", Responsable: "Juan Pérez", Franja: "8:00 AM - 9:00 AM", Patrocinadores: "123, 456".
3. Calcula el costo de publicidad del "Programa A". El cálculo será:
   - **Patrocinador A**: 10 segundos × $5 = $50
   - **Patrocinador B**: 20 segundos × $3 = $60
   - **Costo total**: $50 + $60 = $110

Este cálculo será mostrado en la interfaz de usuario.

## Requisitos Técnicos

1. **Navegador Web**: Este sistema funciona en cualquier navegador moderno que soporte `localStorage`.
2. **Lenguajes**: HTML, CSS y JavaScript.

## Contribuciones

Si deseas contribuir a este proyecto, por favor realiza un **fork** y abre un **pull request**.

## Licencia

Este proyecto está bajo la Licencia MIT.
