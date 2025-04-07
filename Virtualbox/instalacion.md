# 🖥️ Instalación de VirtualBox

Guía rápida para instalar VirtualBox en los sistemas operativos más comunes.

---

## 🔹 Requisitos previos

- Procesador con soporte de virtualización (VT-x / AMD-V)
- Acceso a Internet
- Usuario con permisos de instalación

---

## 🪟 Windows

1. Ir a la página oficial:  
   [https://www.virtualbox.org](https://www.virtualbox.org)

2. Descargar el instalador para Windows.

3. Ejecutar el archivo `.exe` y seguir el asistente:
   - Elegir ruta de instalación (opcional)
   - Confirmar la instalación del controlador de red

4. Finalizar y ejecutar VirtualBox.

---

## 🐧 Linux (Debian/Ubuntu)

```
sudo apt update
sudo apt install virtualbox -y
```
---

## 🍎 macOS

1. Descargar el archivo `.dmg` desde:  
   [https://www.virtualbox.org](https://www.virtualbox.org)

2. Abrir el `.dmg` y seguir los pasos de instalación.

3. Si macOS bloquea la extensión del kernel:
   - Ve a **Preferencias del Sistema → Seguridad y privacidad**
   - Permite la carga de software del desarrollador Oracle

---
### ✅ Verificar instalación
Abre VirtualBox y verifica que puedas crear una nueva máquina virtual sin errores.


