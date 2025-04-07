# 🛠️ Solución: VirtualBox no permite habilitar VT-x/AMD-V en Windows

## 🧠 Problema  
VirtualBox no permite habilitar VT-x/AMD-V, aunque esté activado en BIOS/UEFI.

---

## 🔍 Diagnóstico  
Ejecuta en CMD:

```cmd
systeminfo
```

Si ves:

Se detectó un hipervisor.

Entonces Windows está ejecutando un hipervisor (como Hyper-V o VBS) que bloquea VT-x.
✅ Soluciones
1. Desactivar Memory Integrity (Aislamiento del núcleo

```

    Ir a:
    Inicio > Seguridad de Windows > Seguridad del dispositivo > Aislamiento del núcleo

    Desactiva “Integridad de memoria”

    Reinicia el equipo.
```

2. Desactivar Hyper-V y Virtualization-Based Security (VBS)
Comandos CMD / PowerShell como administrador:

```cmd
bcdedit /set hypervisorlaunchtype off

dism /online /disable-feature /featurename:Microsoft-Hyper-V-All /norestart
dism /online /disable-feature /featurename:VirtualMachinePlatform /norestart
dism /online /disable-feature /featurename:WindowsHypervisorPlatform /norestart
```

## 🔄 Reinicia después de ejecutar estos comandos.

3. Eliminar DeviceGuard y CredentialGuard
Crea un archivo llamado **desactivar_vbs.reg**con este contenido:

Windows Registry Editor Version 5.00

```
[-HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\DeviceGuard]

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa]
"LsaCfgFlags"=dword:00000000

```
Guarda el archivo y ejecútalo con doble clic.

Acepta los cambios y reinicia.

4. (Opcional) Quitar características de Windows si tienes acceso a optionalfeatures

**Desde Inicio > Ejecutar > optionalfeatures, desactiva:**

```
    Hyper-V
    Plataforma de máquina virtual
    Subsistema de Windows para Linux
    Windows Sandbox
    Contenedores
```

5. ⚠️ En **Windows Home** puede que no tengas acceso a esta herramienta.

--- 
## 🔁 Verificación final

Ejecuta en CMD:

```
systeminfo
```

Asegúrate de que NO diga: Se detectó un hipervisor.

**Abre VirtualBox > Configuración de la VM > Sistema > Aceleración**
    
Ya deberías poder marcar:

✅ Habilitar VT-x/AMD-V

✅ Paginación anidada

---
📌 Notas

 ⚠️ **Advertencia:** Estas instrucciones aplican a Windows 10/11.

 En **Windows Home**, gpedit.msc y optionalfeatures pueden no estar disponibles.

Algunos portátiles MSI pueden traer políticas preactivadas que activan VBS automáticamente.

   
