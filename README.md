# Computación Aplicada - Universidad de Palermo - 2024
# Trabajo Práctico de Configuración de Servidor SSH

## Integrantes:

1. Sofia Francia
2. Milena Mastronardi
3. Susana Beatriz Martin
4. Ariel Delgue
5. Facundo Nedic

## Condiciones Generales

Este trabajo práctico se ha desarrollado en una máquina virtual con GNU/Linux Debian.

## Armado de Entorno

1. **Blanqueo de Clave de Root**: Se realizó el blanqueo de la clave de root y se cambió a "palermo".
2. **Nombre de la Máquina**: La máquina virtual fue nombrada como `TPServer`.

## Servicios Configurados

1. **SSH**: Se instaló y configuró un servicio SSH para permitir el acceso al usuario root mediante clave pública.
2. **Web**: Se instaló Apache con soporte para PHP (versión 7.3 o superior) y se configuró para servir el archivo `index.php`.
3. **MySQL**: Se instaló y configuró MariaDB, y se cargó el script `db.sql` proporcionado.

## Storage

1. **Nuevo Disco de 10 GB**: Se agregó un disco nuevo con dos particiones:
   - `/www_dir` de 3 GB
   - `/backup_dir` de 6 GB
   - ** Se edito el archivo fstab y se incluyeron ambas particiones en los directorios correspondientes para su montado automático. 

2. **Configuración de Directorios**:
   - `index.php` se movió a `/www_dir` y se configuró Apache para servir desde este directorio.
   - `/backup_dir` se configuró para almacenar los archivos de backup y se monta automáticamente al inicio del sistema.

## Redes

La interfaz de red `enp0s3` se configuró con una IP estática correspondiente al rango de la máquina anfitriona, incluyendo `ADDRESS`, `NETMASK` y `GATEWAY`.

## Backup

Se desarrolló un script de backup (`backup_full.sh`) ubicado en `/opt/scripts`, que realiza las siguientes tareas:
- **Diariamente a las 0:00**: Backup de `/var/logs`
- **Lunes, Miércoles y Viernes a las 23:00**: Backup de `/www_dir`

El script genera archivos de backup con nombres que incluyen la fecha en formato ANSI (YYYYMMDD) y los almacena en `/backup_dir`. 
El script también verifica la disponibilidad de los sistemas de archivos de origen y destino y maneja opciones de ayuda `-h`.

## Entregables

Los siguientes directorios fueron comprimidos en formato tar.gz y subidos al repositorio de GitHub:
- `/root`
- `/etc`
- `/opt`
- `/var`
- `/www_dir`
- `/backup_dir`

Además, se entregó un diagrama topológico de la infraestructura configurada.

---

¡Éxitos!
