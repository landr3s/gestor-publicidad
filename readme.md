# Sistema de Gestión de Publicidad en Programas de Televisión

Este proyecto tiene como objetivo gestionar los programas de televisión, sus patrocinadores asociados, y calcular el costo total de la publicidad en cada programa basado en la duración del anuncio y el precio por segundo. Además, permite gestionar la información de cadenas de televisión, emisoras y empresas asociadas a la publicidad. El sistema permite registrar programas, asociar patrocinadores, calcular el costo de la publicidad y visualizarlos en tiempo real.

## Descripción del Sistema

### **Estructura Principal:**

El sistema consta de las siguientes partes:

1. **Gestión de Patrocinadores**: Permite registrar patrocinadores, especificando su número de contrato, nombre, duración del anuncio y precio por segundo.
2. **Gestión de Programas**: Permite registrar programas de televisión, asignarles una franja horaria, un responsable y asociar patrocinadores.
3. **Cálculo de Publicidad**: Permite calcular el costo total de la publicidad para un programa basado en los patrocinadores asociados, la duración de sus anuncios y el precio por segundo.
4. **Gestión de Cadenas**: Permite registrar las cadenas de televisión en las que los programas son transmitidos.
5. **Gestión de Emisoras**: Permite registrar emisoras de radio asociadas a las cadenas y a los programas.
6. **Gestión de Empresas**: Permite registrar las empresas que patrocinan los programas y gestionar sus contratos.

### **Flujo de Trabajo:**

1. **Registrar Patrocinador**: Se registran los patrocinadores con su número de contrato, nombre, duración del anuncio y precio por segundo.
2. **Registrar Programa**: Se crean programas de televisión donde se asocian los patrocinadores mediante su número de contrato.
3. **Registrar Cadenas**: Se registran las cadenas de televisión donde los programas serán transmitidos.
4. **Registrar Emisoras**: Se registran emisoras de radio asociadas a las cadenas.
5. **Registrar Empresas**: Se registran las empresas patrocinadoras, junto con los contratos y duración de la publicidad.
6. **Calcular Costo de Publicidad**: Se selecciona un programa y, basado en los patrocinadores asociados, se calcula el costo total de la publicidad sumando los costos de cada patrocinador.

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

3. **Cadenas**:
   - **Atributos**:
     - `nombre` (PK): Nombre de la cadena de televisión.
     - `emisora`: Emisora asociada a la cadena.
4. **Emisoras**:

   - **Atributos**:
     - `nombre` (PK): Nombre de la emisora.
     - `ubicacion`: Ubicación de la emisora.

5. **Empresas**:
   - **Atributos**:
     - `id_empresa` (PK): Identificador de la empresa.
     - `nombre`: Nombre de la empresa.
     - `direccion`: Dirección de la empresa.
     - `telefono`: Teléfono de contacto.

### **Esquema Relacional:**

| Tabla              | Atributos                                             |
| ------------------ | ----------------------------------------------------- |
| **Patrocinadores** | contrato (PK), nombre, duracion, precio               |
| **Programas**      | nombre (PK), responsable, franja, patrocinadores (FK) |
| **Cadenas**        | nombre (PK), emisora                                  |
| **Emisoras**       | nombre (PK), ubicacion                                |
| **Empresas**       | id_empresa (PK), nombre, direccion, telefono          |

## Clases para el Front-End

En el front-end, cada tabla de la base de datos será representada por una clase en JavaScript. A continuación, se describen las clases correspondientes:

### **Clase `Patrocinador`**:

- **Atributos**:
  - `contrato`: Número de contrato del patrocinador.
  - `nombre`: Nombre del patrocinador.
  - `duracion`: Duración del anuncio.
  - `precio`: Precio por segundo.

**Métodos**:

- `guardar()`: Guarda los datos del patrocinador en el localStorage.
- `eliminar()`: Elimina un patrocinador del localStorage.

### **Clase `Programa`**:

- **Atributos**:
  - `nombre`: Nombre del programa.
  - `responsable`: Responsable del programa.
  - `franja`: Franja horaria del programa.
  - `patrocinadores`: Array de contratos de patrocinadores asociados.

**Métodos**:

- `guardar()`: Guarda el programa en el localStorage.
- `eliminar()`: Elimina un programa del localStorage.
- `calcularCosto()`: Calcula el costo total de la publicidad del programa basado en los patrocinadores asociados.

### **Clase `Cadena`**:

- **Atributos**:
  - `nombre`: Nombre de la cadena de televisión.
  - `emisora`: Emisora asociada a la cadena.

**Métodos**:

- `guardar()`: Guarda los datos de la cadena en el localStorage.
- `eliminar()`: Elimina una cadena del localStorage.

### **Clase `Emisora`**:

- **Atributos**:
  - `nombre`: Nombre de la emisora.
  - `ubicacion`: Ubicación de la emisora.

**Métodos**:

- `guardar()`: Guarda los datos de la emisora en el localStorage.
- `eliminar()`: Elimina una emisora del localStorage.

### **Clase `Empresa`**:

- **Atributos**:
  - `id_empresa`: Identificador de la empresa.
  - `nombre`: Nombre de la empresa.
  - `direccion`: Dirección de la empresa.
  - `telefono`: Teléfono de contacto.

**Métodos**:

- `guardar()`: Guarda los datos de la empresa en el localStorage.
- `eliminar()`: Elimina una empresa del localStorage.

### **Diagrama de Clases**

- **Clase `Patrocinador`**:
  - Atributos: contrato, nombre, duracion, precio
  - Métodos: guardar(), eliminar()
- **Clase `Programa`**:

  - Atributos: nombre, responsable, franja, patrocinadores
  - Métodos: guardar(), eliminar(), calcularCosto()

- **Clase `Cadena`**:

  - Atributos: nombre, emisora
  - Métodos: guardar(), eliminar()

- **Clase `Emisora`**:

  - Atributos: nombre, ubicacion
  - Métodos: guardar(), eliminar()

- **Clase `Empresa`**:
  - Atributos: id_empresa, nombre, direccion, telefono
  - Métodos: guardar(), eliminar()

## Implementación Front-End

El front-end se estructura de la siguiente manera:

1. **HTML**:

   - Se incluyen formularios para registrar programas, patrocinadores, cadenas, emisoras y empresas.
   - Se utiliza una lista desplegable (`<select>`) para mostrar los programas, emisoras y cadenas disponibles.
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

3. Registra una cadena con los siguientes datos:

   - Nombre: "Cadena A", Emisora: "Emisora 1".

4. Registra una emisora con los siguientes datos:

   - Nombre: "Emisora 1", Ubicación: "Ciudad X".

5. Registra una empresa con los siguientes datos:

   - Id: 001, Nombre: "Empresa A", Dirección: "Calle Falsa 123", Teléfono: "123-456-7890".

6. Calcula el costo de publicidad del "Programa A". El cálculo será:
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
