# ObligatorioTaller 2024

## Descripcion proyecto taller

## Introducción
Esta instrucciones detallan cómo esta construido el codigo y la aplicación.

## Requisitos:

Disponer 3 maquinas virtuales conectadas en red y con acceso a internet
Disponer de las iso de Rocky9 linux, ubuntu 24.04
Tareas que se van a realizar:

## Instalacion minima de los servidores

Generacion de llaves ssh (llave secreta y llave publica)
Generacion de playbook
Habilitar y Configurar firewall
Configuracion de servidor apache
Configuracion de tomcat
Configuracion de base de datos
Darle permisos de sudo a ansible

## Estrutura del playbook

Collection - Se guardan las colleciones requeridas de los playbook
Files - Se guardan los archivos que se van a usar para copiar, mover o ejecutar como (archivos .sql, .war o configuraciones)
Inventory - Se van a guardar los grupos de servidores y variables 
README - Descripsion del proyecto
ansible.cfg configuracion especificas del proyecto
task_ssh.yml - configuraciones de ssh (generaciones de clave de los equipos se especifica en la documentacion)
task_database.yml - Configuraciones de la base de datos
task_tomcat.yml o task_tomcat33.yml  - Configuraciones del tomcat

## Comando instalacion para ansible:

(En caso de no contar con pip) Sudo dnf install python3-pip 
pipx install pipx 
pipx ensurepath 
pipx install ansible-core argcomplete 
pipx install ansible-core ansible-lint 
Activate-global-python-argcomplete –user 
. /home/sysadmin/ .bash_completion 
source /home/

## Comando instalacion de colleciones: 
ansible-galaxy collection install -r Collections/requirements.yml

## Comando ejecucion de playbook: 
Validacion de sintaxis:
ansible-playbook -i Inventory/servidores task_ssh.yml --syntax-check

Modo de prueba:
ansible-playbook -i Inventory/servidores task_ssh.yml --become --ask-pass -C

Ejecucion:
ansible-playbook -i Inventory/servidores task_ssh.yml --become --ask-pass

# Observaciones:
En caso de no contar con descompresores de archivos debe instalar gzip y tar:
sudo dnf install tar
sudo dnf install gzip

En caso de querer chequear si se cuenta con java o si quedo correctamente instalado se puede usar:
java -version
 
