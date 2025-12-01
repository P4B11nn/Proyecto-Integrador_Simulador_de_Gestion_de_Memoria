# 🖥️ Simulador de Memoria Virtual con Paginación y Swap

## 👥 Integrantes del Proyecto

| Nombre | Matrícula |
|--------|-----------|
| Zamora Camacho Adal Mauricio | A2213332218 |
| Mendez Guerrero Pablo Daniel | a2223330178 |
| Ortega Resendiz Luis Fernando | a2183330150 |
| Sanchez Morales Jesus | a2223339020 |
| Vergara Gonzalez Magnus Henrich | a2143222011 |

## 🚀 Cómo Compilar y Ejecutar

### ⚡ Forma más fácil (para el profesor)

1. **Descargar** `simulador.exe` y `config.ini` desde Moodle
2. **Colocar** ambos archivos en la misma carpeta
3. **Ejecutar** haciendo doble clic en `simulador.exe`
   
   ➡️ *El programa arranca automáticamente y muestra toda la simulación*

#### 🔧 Cambiar algoritmo de reemplazo:
- Abrir `config.ini`
- Cambiar la línea `replacement_algorithm clock` por:
  - `fifo` (First In, First Out)
  - `lru` (Least Recently Used)
  - `clock` (Algoritmo del Reloj)
- Guardar y ejecutar nuevamente el `.exe`

### 💻 En VS Code
1. Abrir la carpeta del proyecto
2. Presionar **F5**
3. Se compila y ejecuta automáticamente

### 🔨 Desde terminal (compilación manual)
```bash
g++ -std=c++17 src/*.cpp -o simulador.exe
./simulador.exe
```

## 🏗️ Diseño del Programa

### 📋 Estructura de Datos
- **RAM**: Dos vectores (`ram_owner` y `ram_page_in_ram`) para determinar en tiempo constante qué proceso ocupa cada marco
- **Swap**: Un vector `swap_owner` para búsqueda rápida de slots libres
- **Tabla de páginas**: Cada proceso tiene su propio `vector<PageEntry>` con campos:
  - `present` (página en RAM)
  - `frame` (marco asignado)
  - `swap_frame` (posición en swap)

### ⚙️ Implementación
- **Procesos activos**: Almacenados en `unordered_map<PID, Process*>` para acceso O(1)
- **TLB**: Vector simple con política FIFO (el más antiguo sale primero)
- **Algoritmos de reemplazo**: 
  - Clase abstracta `ReplacementAlgorithm`
  - Tres implementaciones: `FIFO`, `LRU` y `Clock`
  - Selección dinámica mediante `config.ini`

### 🛠️ Tecnología
- **Lenguaje**: C++17
- **Plataforma**: Windows (ejecutable standalone)
- **Interfaz**: Consola
- **Dependencias**: Ninguna (no requiere instalaciones adicionales)