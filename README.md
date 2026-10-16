# wikiopen

Habilitación de cockpit
systemctl enable --now cockpit.socket

Hardening ssh
#ssh cambio de puerto
vim /etc/ssh/sshd_config
Port 29547

#Agregar puerto
firewall-cmd --permanent --add-port=29547/tcp

#Selinux
sudo semanage port -a -t ssh_port_t -p tcp 29547

#Cerrar puerto ssh por defecto
firewall-cmd --permanent --remove-service=ssh
firewall-cmd --reload

Instalación Sophos y TrenMicro Agente
copiar a /opt/Sophos
SophosSetupLinux.sh
Ejecutar
sh SophosSetupLinux.sh


Validar
 ps -aux | grep sophos



Crear una carpeta en /opt/TM
copiar el archivo TMServerAgent_Linux_auto_x86_64_Municipio_de_Quito.tar y descomprimir
./tmxbc install

ps –aux | grep ds_agent

# AGREGAR UNA CARPETA DE FILESERVER

sudo mount -t cifs "\\filedmq02\Respaldos Logs\LINUX\2026\172.30.1.59\2026" /mnt/pruebalogs -o credentials=/etc/smbcredentialsmg,vers=3.0

root@srv11contenedores03:/mnt/pruebalogs/LINUX/2026/172.30.1.59/2026# cat /etc/smbcredentialsmg 
username=mgallardo
password=Argon171425$#
domain=dmq.quitodm.inst

 
 

