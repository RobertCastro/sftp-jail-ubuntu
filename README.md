# sftp-jail-ubuntu

Este script crea un usuario con sus carpetas y con los permisos adecuados para que pueda subir y eliminar archivos. También añade el grupo especificado (www-data por ejemplo) para que php o cualquier otro pueda escribir.

Probado en Ubuntu 14.04.

##Editar configuración ssh

> sudo nano /etc/ssh/sshd_config

 Modificar esta línea (Subsystem)
> Subsystem sftp internal-sftp 

 Añadir el bloque al final del archivo
> Match Group sftp-users

>  ChrootDirectory %h

>  ForceCommand internal-sftp

> AllowTcpForwarding no

> PermitTunnel no

> X11Forwarding no

### Descargar y ejecutar.

wget https://raw.githubusercontent.com/RobertCastro/sftp-jail-ubuntu/master/sftp-jail

> sudo chmod +x sftp-jail

# Generar contraseña
> sudo ./sftp-jail -u testdomain.com -p

# Sin contraseña, asignar luego (sudo passwd testdomain.com). 
> sudo ./sftp-jail -u testdomain.com 
Si se ejecuta el script como en el ejemplo anterior, deberías ver algo similar a