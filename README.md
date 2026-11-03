
# ✚ Farmacia Cruz Verde
## Sistema de Control de Inventario

Aplicación web para administrar y controlar el stock de mercadería de Farmacia Cruz Verde.

El sistema permite registrar productos, controlar las cantidades disponibles en el depósito y en el local, y detectar automáticamente los artículos que necesitan reposición.

---

## 🚀 Funcionalidades

- **Carga de productos:** permite agregar artículos con nombre y descripción.
- **Stock del depósito:** registra las unidades disponibles en depósito.
- **Stock del local:** registra las unidades disponibles en el local.
- **Stock total automático:** suma las cantidades de ambas ubicaciones.
- **Alerta de reposición:** marca en rojo los productos cuyo stock total sea igual o inferior a 3 unidades.
- **Buscador:** permite encontrar productos por nombre mientras se escribe.
- **Edición de productos:** permite modificar nombres, descripciones y cantidades.
- **Eliminación:** permite quitar productos del inventario.
- **Guardado automático:** conserva los datos en el navegador.
- **Exportación CSV:** permite descargar el inventario para abrirlo con Excel.

---

## 📱 Diseño adaptable

El sistema está preparado para funcionar en:

- Computadoras de escritorio (PC).
- Notebooks.
- Celulares Android.
- iPhone.
- Tablets.

La interfaz se adapta automáticamente al tamaño de pantalla.

---

## 🛠️ Tecnologías utilizadas

- HTML5
- CSS3
- JavaScript
- LocalStorage
- GitHub Pages

No requiere instalar programas adicionales.

---

## 📦 Instalación y publicación

### 1. Crear el repositorio

Ingresar a GitHub y crear un repositorio nuevo con el nombre:

`inventario-cruz-verde`

### 2. Subir los archivos

Subir el archivo principal:

`index.html`

Y este archivo:

`README.md`

Ambos deben estar en la raíz del repositorio.

### 3. Activar GitHub Pages

1. Entrar en Settings.
2. Seleccionar Pages.
3. En Build and deployment elegir Deploy from a branch.
4. Seleccionar la rama `main`.
5. Seleccionar la carpeta `/ (root)`.
6. Presionar Save.

### 4. Acceder al sistema

Una vez publicado, GitHub proporcionará una dirección web similar a:

`https://TU-USUARIO.github.io/inventario-cruz-verde/`

---

## 🔴 Sistema de reposición

El inventario calcula automáticamente:

**Stock total = Stock depósito + Stock local**

| Stock total | Estado |
|---|---|
| 0 a 3 unidades | 🔴 REPOSICIÓN |
| 4 unidades o más | 🟢 EN STOCK |

---

## ⚠️ Importante: almacenamiento

Esta versión utiliza LocalStorage.

Esto significa que los productos quedan guardados en el navegador y dispositivo donde se cargan.

Los datos no se sincronizan automáticamente entre diferentes computadoras o celulares.

Se recomienda exportar periódicamente el inventario mediante el botón CSV para conservar una copia de seguridad.

---

## 🏥 Proyecto

**Farmacia Cruz Verde**

Sistema interno de control y administración de mercadería.

Desarrollado para facilitar el seguimiento del inventario y mejorar el control de reposición de productos.
