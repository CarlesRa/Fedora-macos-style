# 🍏 # Fedora GNOME - macOS Desktop Transformation Guide

Guía de configuración, extensiones, temas y ajustes para transformar **Fedora Workstation (GNOME + Wayland)** en un entorno de trabajo visualmente inspirado en macOS, manteniendo la estabilidad, ligereza y rendimiento del sistema.

---

## 💻 Entorno

- **SO:** Fedora Linux Workstation
- **Escritorio:** GNOME Shell
- **Sesión gráfica:** Wayland
- **Gestor de ventanas:** Mutter
- **Tema visual:** WhiteSur-Dark
- **Inspiración:** macOS

---

## 🎨 Objetivos visuales

- **Dock flotante:** Posicionado abajo, centrado, con auto-ocultado y ampliación de iconos.
- **Transparencias y Blur:** Efecto cristal tipo Liquid Glass.
- **Botones de ventana:** Estilo macOS, alineados a la izquierda (rojo, amarillo y verde).
- **Ventanas redondeadas:** Esquinas uniformes y sombras suaves.
- **Animaciones:** Transiciones fluidas al abrir, minimizar y cerrar ventanas.
- **Tema e iconos:** Estética uniforme basada en WhiteSur.

---

## 🧩 Extensiones de GNOME

Extensiones previstas para completar la transformación:

| Extensión | Función |
|---|---|
| **Blur my Shell** | Desenfoque del panel y dock. |
| **Dash to Dock** | Dock flotante, centrado y personalizable. |
| **Just Perfection** | Limpieza y personalización de GNOME Shell. |
| **Burn My Windows** | Animaciones de apertura y cierre. |
| **Rounded Window Corners Reborn** | Esquinas redondeadas y sombras. |

**Nota:** Comprobar compatibilidad con la versión instalada de GNOME antes de instalar o actualizar extensiones.

---

## 🚀 Configuración realizada

### 1. Botones de ventana a la izquierda

Se ha aplicado la disposición clásica de macOS:

```bash
gsettings set org.gnome.desktop.wm.preferences button-layout 'close,minimize,maximize:'
```

### 2. Instalación de WhiteSur GTK Theme

Repositorio descargado en:

```text
~/Downloads/WhiteSur-gtk-theme
```

Instalación realizada con:

```bash
cd ~/Downloads/WhiteSur-gtk-theme
./install.sh -c dark -a alt -l
```

Parámetros utilizados:

- `-c dark`: variante oscura.
- `-a alt`: variante alternativa de los botones de ventana.
- `-l`: integración para aplicaciones GTK4/libadwaita.

### 3. Temas instalados

Ubicación:

```text
~/.themes/
```

Variantes presentes:

- WhiteSur-Dark
- WhiteSur-Dark-hdpi
- WhiteSur-Dark-solid
- WhiteSur-Dark-solid-hdpi
- WhiteSur-Dark-solid-xhdpi

### 4. Configuración mediante Retoques (GNOME Tweaks)

En la aplicación **Retoques** se ha seleccionado:

- **Legacy Applications:** WhiteSur-Dark
- **Shell:** WhiteSur-Dark

La extensión **User Themes** está instalada para permitir la personalización de GNOME Shell.

### 5. Integración GTK4 / libadwaita

Directorio:

```text
~/.config/gtk-4.0/
```

Archivos y enlaces creados por el instalador:

```text
assets/
cosmic/
gtk.css
gtk-dark.css
gtk-Dark.css
gtk-Light.css
settings.ini
windows-assets/
```

Los enlaces simbólicos apuntan a:

```text
gtk.css      -> gtk-Dark.css
gtk-dark.css -> gtk-Dark.css
```

### 6. Verificación de los botones de colores

Se han comprobado los tres archivos PNG:

```text
~/.config/gtk-4.0/windows-assets/
```

Imágenes:

- `titlebutton-close-dark.png`
- `titlebutton-maximize-dark.png`
- `titlebutton-minimize-dark.png`

Las tres imágenes son válidas, de 16 × 16 píxeles, y contienen los colores esperados:

| Botón | Color |
|---|---|
| Cerrar | Rojo |
| Minimizar | Amarillo |
| Maximizar | Verde |

Para comprobarlas:

```bash
identify ~/.config/gtk-4.0/windows-assets/titlebutton-{close,maximize,minimize}-dark.png
```

Para generar una imagen ampliada de los tres botones:

```bash
magick montage ~/.config/gtk-4.0/windows-assets/titlebutton-{close,maximize,minimize}-dark.png -tile 3x1 -geometry 64x64+15+15 /tmp/botones-whitesur.png
```

Abrir la imagen:

```bash
xdg-open /tmp/botones-whitesur.png
```

---

## ✅ Estado actual comprobado

| Aplicación / elemento | Estado |
|---|---|
| WhiteSur-Dark | Instalado |
| User Themes | Instalado |
| Botones a la izquierda | Configurado |
| Integración GTK4 | Instalada |
| Archivos (Nautilus) | Botones de colores visibles |
| Chrome | Sigue mostrando decoración propia/gris |
| Terminal | Pendiente de identificar y configurar |
| Dock flotante | Pendiente de completar |
| Blur y transparencias | Pendiente de completar |
| Animaciones | Pendiente de completar |
| Esquinas redondeadas | Pendiente de completar |

### Importante: Chrome y Terminal

Los botones de colores funcionan correctamente en Archivos.

Chrome y algunas terminales pueden utilizar decoraciones propias o mecanismos distintos de GTK. Por tanto, no hay que asumir que el tema GTK controla todas las aplicaciones.

No modificar los archivos PNG ni el CSS de WhiteSur para intentar corregir Chrome sin haber identificado primero qué sistema de decoración utiliza.

---

## 🔧 Comandos útiles de diagnóstico

### Comprobar sesión gráfica

```bash
echo $XDG_SESSION_TYPE
```

Resultado esperado:

```text
wayland
```

### Comprobar disposición de botones

```bash
gsettings get org.gnome.desktop.wm.preferences button-layout
```

### Comprobar enlaces GTK4

```bash
ls -l ~/.config/gtk-4.0/gtk.css ~/.config/gtk-4.0/gtk-dark.css
```

### Comprobar imágenes WhiteSur

```bash
ls -lh ~/.config/gtk-4.0/windows-assets/
```

---

## 📌 Próximas tareas

1. Completar la configuración del Dock con Dash to Dock.
2. Conseguir el efecto de transparencia y desenfoque con Blur my Shell.
3. Configurar las animaciones con Burn My Windows.
4. Configurar las esquinas redondeadas.
5. Identificar la aplicación de Terminal instalada y estudiar sus decoraciones.
6. Investigar si Chrome permite utilizar las decoraciones de ventana del sistema.
7. Ajustar iconos, cursores, fuentes y detalles visuales para completar la estética macOS.

---

## 🛡️ Filosofía del proyecto

- Priorizar extensiones compatibles con GNOME y Wayland.
- Evitar modificaciones innecesarias en archivos del sistema.
- Realizar copias de seguridad antes de modificar configuraciones.
- Preferir ajustes reversibles en el directorio personal.
- No sacrificar estabilidad ni rendimiento por conseguir una apariencia visual.

**Objetivo final:** conseguir una experiencia visual inspirada en macOS sobre Fedora Workstation, conservando GNOME, Wayland y la estabilidad del sistema.

## ❤️ Soporte técnico

- Primo principal: ChatGPT.
- Especialidad: Fedora, GNOME y macOS.
- Método de trabajo: paso a paso y sin romper nada.
- Lema: ¡Esos semáforos tienen que quedar bonitos!
- Nivel de paciencia: infinito (casi).