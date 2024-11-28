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
7. **Cálculo de Costos**: Permite calcular los costos de la publicidad basados en múltiples factores, incluyendo duración de los anuncios y tarifas por segundo.

### **Flujo de Trabajo:**

1. **Registrar Patrocinador**: Se registran los patrocinadores con su número de contrato, nombre, duración del anuncio y precio por segundo.
2. **Registrar Programa**: Se crean programas de televisión donde se asocian los patrocinadores mediante su número de contrato.
3. **Registrar Cadenas**: Se registran las cadenas de televisión donde los programas serán transmitidos.
4. **Registrar Emisoras**: Se registran emisoras de radio asociadas a las cadenas.
5. **Registrar Empresas**: Se registran las empresas patrocinadoras, junto con los contratos y duración de la publicidad.
6. **Calcular Costo de Publicidad**: Se selecciona un programa y, basado en los patrocinadores asociados, se calcula el costo total de la publicidad sumando los costos de cada patrocinador.
7. **Calcular Costos Adicionales**: El sistema permite calcular costos adicionales de la publicidad considerando otros factores como el tiempo de emisión, tipo de anuncio y tarifas específicas.

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

6. **Calculo**:
   - **Atributos**:
     - `id_calculo` (PK): Identificador único para cada cálculo.
     - `programa_id` (FK): Relacionado con el programa de televisión.
     - `patrocinador_id` (FK): Relacionado con el patrocinador.
     - `costo_total`: Costo total calculado para ese patrocinador en el programa.
     - `duracion`: Duración del anuncio en segundos.
     - `precio_por_segundo`: Precio por segundo del anuncio.

### **Esquema Relacional:**

| Tabla              | Atributos                                                                                          |
| ------------------ | -------------------------------------------------------------------------------------------------- |
| **Patrocinadores** | contrato (PK), nombre, duracion, precio                                                            |
| **Programas**      | nombre (PK), responsable, franja, patrocinadores (FK)                                              |
| **Cadenas**        | nombre (PK), emisora                                                                               |
| **Emisoras**       | nombre (PK), ubicacion                                                                             |
| **Empresas**       | id_empresa (PK), nombre, direccion, telefono                                                       |
| **Calculo**        | id_calculo (PK), programa_id (FK), patrocinador_id (FK), costo_total, duracion, precio_por_segundo |

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

### **Clase `Calculo`**:

- **Atributos**:
  - `id_calculo`: Identificador único para cada cálculo.
  - `programa_id`: Relacionado con el programa de televisión.
  - `patrocinador_id`: Relacionado con el patrocinador.
  - `costo_total`: Costo total calculado para ese patrocinador en el programa.
  - `duracion`: Duración del anuncio en segundos.
  - `precio_por_segundo`: Precio por segundo del anuncio.

**Métodos**:

- `guardar()`: Guarda el cálculo en el localStorage.
- `eliminar()`: Elimina un cálculo del localStorage.
- `calcularCostoTotal()`: Calcula el costo total de la publicidad basado en la duración y el precio por segundo.

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

- **Clase `Calculo`**:
  - Atributos: id_calculo, programa_id, patrocinador_id, costo_total, duracion, precio_por_segundo
  - Métodos: guardar(), eliminar(), calcularCostoTotal()

## Implementación Front-End

El front-end se estructura de la siguiente manera:

1. **HTML**:
   - Formularios para registrar programas, patrocinadores, cadenas, emisoras y empresas.
   - Un listado de programas con sus respectivos patrocinadores y costos.
2. **CSS**:

   - Estilos básicos para la presentación y organización de la interfaz.

3. **JavaScript**:
   - Los datos se almacenan en `localStorage`.
   - Manejo de la interacción con formularios y cálculos de costos.

## Ejemplo de Uso

1. Registra patrocinadores con los siguientes datos:
   - Contrato: 123, Nombre: "Patrocinador A", Duración: 10 segundos, Precio: $5 por segundo.
   - Contrato: 456, Nombre: "Patrocinador B", Duración: 20 segundos, Precio: $3 por segundo.
2. Registra un programa con los siguientes datos:
   - Nombre: "Programa A", Responsable: "Juan Pérez", Franja: "8:00 AM - 9:00 AM", Patrocinadores: "123, 456".
3. Registra una cadena y emisora.
4. Registra una empresa con los siguientes datos:
   - Id: 001, Nombre: "Empresa A", Dirección: "Calle Falsa 123", Teléfono: "123-456-7890".
5. Calcula el costo de publicidad del "Programa A" basado en los patrocinadores.

Este cálculo será mostrado en la interfaz de usuario.

## Requisitos Técnicos

1. **Navegador Web**: Este sistema funciona en cualquier navegador moderno que soporte `localStorage`.
2. **Lenguajes**: HTML, CSS y JavaScript.

## Contribuciones

Si deseas contribuir a este proyecto, por favor realiza un **fork** y abre un **pull request**.

## Licencia

Este proyecto está bajo la Licencia MIT.
