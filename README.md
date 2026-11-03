
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
- **Guardado automático:** sincroniza productos entre dispositivos conectados a la misma cuenta.
- **Actualización en tiempo real:** refleja altas, cambios y eliminaciones en las sesiones abiertas.
- **Exportación CSV:** permite descargar el inventario para abrirlo con Excel.

- Supabase Auth
- Supabase Database y Realtime

## 📱 Diseño adaptable
## Configuración de sincronización
El sistema está preparado para funcionar en:
La página requiere un proyecto de Supabase para compartir el inventario. La URL y la clave `anon` son públicas; la protección de los datos depende de las políticas de acceso de la base.
- Computadoras de escritorio (PC).
### 1. Crear la tabla
- Celulares Android.
En Supabase, abrí **SQL Editor**, pegá y ejecutá:
- Tablets.
```sql
create table public.products (
	id uuid primary key default gen_random_uuid(),
	user_id uuid not null references auth.users(id) on delete cascade,
	name text not null,
	description text not null default '',
	depot integer not null default 0 check (depot >= 0),
	store integer not null default 0 check (store >= 0),
	created_at timestamptz not null default now()
);
La interfaz se adapta automáticamente al tamaño de pantalla.
alter table public.products enable row level security;
---
create policy "Users manage their own products"
on public.products
for all to authenticated
using ((select auth.uid()) = user_id)
with check ((select auth.uid()) = user_id);
## 🛠️ Tecnologías utilizadas
alter publication supabase_realtime add table public.products;
```
- HTML5
### 2. Crear la cuenta compartida
- JavaScript
En **Authentication → Users**, creá una cuenta para el inventario. Desactivá el registro público de usuarios. Iniciá sesión con esa misma cuenta en todos los dispositivos que deban compartir los productos.
- GitHub Pages
### 3. Conectar la página
No requiere instalar programas adicionales.
En **Project Settings → API**, copiá la Project URL y la clave publicable (`anon`). En `index.html`, completá estas constantes:
---
```js
const SUPABASE_URL = "https://tu-proyecto.supabase.co";
const SUPABASE_ANON_KEY = "tu-clave-publicable";
```

No pongas la clave `service_role` en la página. Esa clave permite saltarse las políticas de seguridad.

### 4. Publicar con GitHub Pages

En **Settings → Pages**, elegí **Deploy from a branch**, rama `main`, carpeta `/(root)` y guardá. La URL del proyecto es:

https://daanieelrp35-ops.github.io/Farmacia-Cruz-Verde/

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

## ⚠️ Datos existentes y acceso

Los productos guardados previamente en `localStorage` no se copian automáticamente a Supabase; permanecen en el navegador donde se cargaron. Exportalos a CSV antes de cambiar al modo compartido si necesitás conservarlos.

Sin la configuración de Supabase, la página funciona en modo local y los cambios no se comparten. No cargues datos personales ni información de pacientes en este sistema.

---

## 🏥 Proyecto

**Farmacia Cruz Verde**

Sistema interno de control y administración de mercadería.

Desarrollado para facilitar el seguimiento del inventario y mejorar el control de reposición de productos.
