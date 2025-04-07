# 🧰 Instalación de Proxmox VE en VirtualBox

Guía paso a paso para instalar **Proxmox Virtual Environment** (VE) en **Oracle VirtualBox**, ideal para pruebas, laboratorios y aprendizaje.

---

## 📦 Requisitos

- VirtualBox (última versión recomendada)
- ISO de Proxmox VE:  
  Descargar desde: https://www.proxmox.com/en/downloads

---

## ⚙️ Crear la máquina virtual

1. **Nombre:** `Proxmox-VE`
2. **Tipo:** Linux
3. **Versión:** Debian (64-bit)
4. **RAM:** mínimo 4096 MB (recomendado: 8192 MB)
5. **CPU:** 2 o más núcleos
6. **Disco duro:** al menos 32 GB (dinámico)
7. **Red:** Adaptador puente o adaptador solo-anfitrión (según tu necesidad)
8. **Virtualización:** Asegúrate de que **VT-x/AMD-V** esté habilitado

---

## 💿 Montar la ISO

1. Ve a **Configuración > Almacenamiento** de la VM
2. En el controlador IDE, monta la ISO de Proxmox VE
3. Asegúrate de marcar **Iniciar desde unidad óptica (ISO)** en el orden de arranque

---

## 🚀 Instalación de Proxmox

1. Inicia la VM
2. En el menú de instalación, elige **Install Proxmox VE**
3. Acepta la licencia
4. Elige el disco (suele ser `sda`)
5. Configura:
   - Región / Zona horaria
   - Contraseña de root
   - Correo electrónico
   - Nombre del host
   - Red: usa una IP local (puede ser 192.168.x.x)

---

## 🌐 Acceder a la interfaz web

1. Una vez instalado, verás un mensaje como:
   
You can now connect to the Proxmox VE web interface:


3. Abre un navegador en tu máquina real y accede a esa IP:  
**https://192.168.1.100:8006** (por ejemplo)

4. Inicia sesión con:
- **Usuario:** `root`
- **Contraseña:** la que configuraste
- **Realm:** `Linux PAM standard authentication`

---

## 🧪 Notas importantes

- Puede que necesites **aceptar el certificado SSL no confiable**
- No es recomendable para producción, solo para **lab/test**
- Puedes agregar ISOs, LXC, o configurar clústeres de prueba desde aquí

---

## 🧰 Sugerencias

- Habilita red tipo **puente (bridge)** para poder acceder desde otras máquinas de tu red.
- Puedes simular clústeres usando múltiples VMs con Proxmox.
- Para mejorar el rendimiento: instala **VirtualBox Guest Additions** si es necesario (en Debian base).

---

> 📘 Para más información oficial: https://pve.proxmox.com/wiki/Installation

