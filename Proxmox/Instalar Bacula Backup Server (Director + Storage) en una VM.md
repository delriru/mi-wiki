🔹 PASO 1: Crear una VM Linux para Bacula en Proxmox

1.1. Sube la ISO de instalación a Proxmox

Si no tienes una ISO de Linux aún:

    Te recomiendo Ubuntu Server 22.04 LTS o Rocky Linux 9.

    Puedes descargar Ubuntu desde:
    👉 https://ubuntu.com/download/server

En Proxmox:

    Ve a Datacenter > Storage > local (pve) > Content > Upload

    Sube el archivo .iso.

1.2. Crear la VM

En la interfaz de Proxmox:

    Click en "Create VM"

    General:

        VM ID: 100 (o el que quieras)

        Name: bacula-server

    OS:

        ISO: elige la que subiste

        Type: Linux

    System:

        BIOS: UEFI o Default

        Machine: q35 o i440fx (ambos sirven)

    Hard Disk:

        Bus/Device: VirtIO SCSI

        Size: 30 GB (puedes ampliarlo después)

    CPU:

        Cores: 2

    Memory:

        RAM: 4096 MB (4 GB)

    Network:

        Bridge: vmbr0

        Model: VirtIO (para mejor rendimiento)

    Confirmar y Crear la VM

1.3. Instalar el sistema operativo

    Inicia la VM

    Sigue la instalación típica de Ubuntu Server o Rocky Linux

    Crea un usuario, habilita SSH, selecciona mínimo software

🔹 PASO 2: Preparar la VM para Bacula

Una vez instalado el SO:

    Inicia sesión con tu usuario

    Actualiza el sistema:

sudo apt update && sudo apt upgrade -y  # en Ubuntu

o

    sudo dnf update -y  # en Rocky

🔹 PASO 3: Instalar Bacula (Ubuntu ejemplo)
3.1. Instalar Bacula y dependencias:

sudo apt install bacula-server bacula-client -y

Esto instala:

    Bacula Director (cerebro del sistema)

    Bacula Storage Daemon

    Bacula File Daemon (agente en este servidor)

3.2. Verifica los servicios:

systemctl status bacula-director
systemctl status bacula-fd
systemctl status bacula-sd

🔹 ¿Qué sigue?

En el próximo paso configuraremos los archivos:

    bacula-dir.conf (plan de backup)

    bacula-sd.conf (dónde guardar)

    bacula-fd.conf (cliente local)

Pero primero dime: ✅ ¿Ya tienes la VM creada con Ubuntu o Rocky y Bacula instalado? Y te paso el siguiente bloque para configurar y lanzar tu primer backup. 🚀
