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

[root@apimanager mnt]# mount -t cifs "\filedmq02.isilon-dmi.dmq.quitodm.inst\Respaldos Logs\LINUX\2026\172.30.1.142\
2026" /mnt/logs -o credentials=/etc/smbcredentialsmg,vers=3.0

root@srv11contenedores03:/mnt/pruebalogs/LINUX/2026/172.30.1.59/2026# 

cat /etc/smbcredentialsmg 
username=mgallardo
password=xxxxxxxxxxxxxxxxxxxxxxxxxxx
domain=dmq.quitodm.inst


# COMPRIMIR ARCHIVOS
 Compresion  del 172.30.1.142

gzip -c /var/lib/docker/containers/9a62bc47dd5c8652d69df51439ec6e5876cefb3fb8c4f530aea75bfa1fa814e2/9a62bc47dd5c8652d69df51439ec6e5876cefb3fb8c4f530aea75bfa1fa814e2-json.log \
> /var/RespaldoLogs/log_contenedores/mdmq_vehiculos_api-mdmq_vehiculos_api-1_2026-09-16.log.gz

gzip -c /var/lib/docker/containers/c4e4683e14816467da7ae64c1e7c076e7e45cd6a106b9f49dbbb2d9bf7a0005c/c4e4683e14816467da7ae64c1e7c076e7e45cd6a106b9f49dbbb2d9bf7a0005c-json.log \
> /var/RespaldoLogs/log_contenedores/nginx_2026-09-16.log.gz

gzip -c /var/lib/docker/containers/2b40ab996b5327520d88d671903d249c55335cd159e5b4550a3ebc8847495b74/2b40ab996b5327520d88d671903d249c55335cd159e5b4550a3ebc8847495b74-json.log \
> /var/RespaldoLogs/log_contenedores/mdmq_bienes_inmuebles-backend-1_2026-09-16.log.gz

Verificacion 

gzip -t /opt/RespaldoLogs/log_contenedores/nginx_2026-09-16.log.gz
gzip -t
gzip -t


Truncado


truncate -s 0 /var/lib/docker/containers/9a62bc47dd5c8652d69df51439ec6e5876cefb3fb8c4f530aea75bfa1fa814e2/9a62bc47dd5c8652d69df51439ec6e5876cefb3fb8c4f530aea75bfa1fa814e2-json.log
truncate -s 0 /var/lib/docker/containers/c4e4683e14816467da7ae64c1e7c076e7e45cd6a106b9f49dbbb2d9bf7a0005c/c4e4683e14816467da7ae64c1e7c076e7e45cd6a106b9f49dbbb2d9bf7a0005c-json.log
truncate -s 0 /var/lib/docker/containers/2b40ab996b5327520d88d671903d249c55335cd159e5b4550a3ebc8847495b74/2b40ab996b5327520d88d671903d249c55335cd159e5b4550a3ebc8847495b74-json.log
 

