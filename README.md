# 🍏 Fedora GNOME - macOS Desktop Transformation Guide

Un repositorio con la configuración, extensiones, scripts y ajustes necesarios para transformar **Fedora Workstation (GNOME + Wayland)** en un entorno de trabajo visualmente inspirado en macOS, manteniendo la estabilidad, ligereza y rendimiento nativos.

---

## 💻 Entorno probado

* **SO:** Fedora Linux Workstation
* **Entorno de escritorio:** GNOME Shell (Wayland)
* **Gestor de ventanas:** Mutter (Wayland)

---

## 🎨 Características principales

* **Dock flotante:** Posicionado abajo, centrado, con auto-ocultado, ampliación de iconos y efecto cristal.
* **Transparencias & Blur:** Desenfoque tipo *Liquid Glass* mediante el algoritmo *Dual Kawase*.
* **Botones de ventana:** Estilo macOS alineados a la izquierda (`Cerrar`, `Minimizar`, `Maximizar`).
* **Ventanas redondeadas:** Bordes con radio uniforme (14 px) y sombras suaves.
* **Animaciones:** Transiciones fluidas tipo *Glide* al abrir, minimizar y cerrar ventanas.
* **Tema e Iconos:** Estética visual uniforme con la suite WhiteSur.

---

## 🧩 Extensiones de GNOME empleadas

Instala y activa las siguientes extensiones desde la aplicación **Extensiones de GNOME** o via DNF:

| Extensión | Función en el sistema |
| :--- | :--- |
| **Blur my Shell** | Efecto de desenfoque *Liquid Glass* en el panel y dock. |
| **Dash to Dock** | Dock flotante, centrado y personalizable. |
| **Just Perfection** | Limpieza de UI, visibilidad de elementos y retoques del Shell. |
| **Burn My Windows** | Animaciones de apertura y cierre de ventanas (*Glide*). |
| **Rounded Window Corners Reborn** | Radio de esquinas redondeadas y sombras en aplicaciones. |

---

## 🚀 Pasos de instalación y configuración

### 1. Botones de ventana a la izquierda
Aplica la disposición clásica de los botones de macOS mediante `gsettings`:

```bash
gsettings set org.gnome.desktop.wm.preferences button-layout 'close,minimize,maximize:'
