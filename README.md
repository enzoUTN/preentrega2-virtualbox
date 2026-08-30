# Reporte Técnico de Configuración de Laboratorio

## 1 - VirtualBox y Red Aislada

Se crearon dos máquinas virtuales con la herramienta VirtualBox. Una que tiene el sistema operativo Linux (específicamente Kali Linux) y otra con Windows 10.

Antes de la instalación, a las dos máquinas virtuales se eligió la red en modo NAT (por lo menos por el momento), para que estas mismas vean al host como si fuera un modem, así no se pone en riesgo la red del hogar ni el host (la computadora que está corriendo las máquinas virtuales) y a la vez estos dos sistemas tienen acceso a internet. 

En tal caso que se quiera probar algún tipo de virus o malware, se podría descargar el archivo en modo NAT y antes de ejecutarlo, cambiar la Red en modo red interna. En este modo las máquinas virtuales quedan aisladas sin perjudicar al host, pero podrían tener comunicación entre ellas. 

![Red asilada](https://github.com/user-attachments/assets/345be234-9073-40dd-96b0-48c15e3e89fd)

También en la configuración de la máquina virtual se deshabilitaron los controladores de USB, para aislarlas aún más del host.

![USB controladores](https://github.com/user-attachments/assets/390a91d3-114c-4a34-92ed-8998e8092a55)

## 2 - Capa Windows: Usuarios y Actualizaciones

Una vez instalada la máquina virtual con Windows 10, se creó un usuario estándar. La razón de crear este usuario fue para que los posibles virus o malware que pueda descargar un usuario cotidiano (alguien que solo usa el navegador web u office) no tengan permisos de administrador, así impedimos que la amenaza no pueda ser ejecutada por este tipo de usuarios. 

![Nuevo usuario](https://github.com/user-attachments/assets/0d34ae0d-6e1b-4af1-a1f2-fd1b15af2d6a)

![Usuario sin administrador](https://github.com/user-attachments/assets/493f934d-566f-4207-8490-1764bd1c42d4)

También se desactivó ciertos servicios como SMB 1.0, que viene por defecto activado en Windows. Esta acción se debe a que el protocolo es muy viejo y tiene historial de ser culpable de propagación de algunos virus (como WannaCry). Actualmente, utilizamos otros protocolos más seguros y modernos para compartir archivos (como SMB 3.1.1).

![SMB](https://github.com/user-attachments/assets/7f91e475-40b6-4dfe-ae4b-af6887dc9d6e)

Como las amenazas día a día buscan vulnerabilidades en el código de Windows, es necesario mantener actualizado el sistema operativo. Para poder proteger o solucionar esas vulnerabilidades, Microsoft lanza parches de seguridad. Por esta razón siempre es recomendable actualizar lo antes posible con Windows update.

![Windows update](https://github.com/user-attachments/assets/6dd8f111-cd42-4f80-af13-00e1fc82c681)

## 3 - Capa Linux: Permisos y Gestión

Una vez instalado Kali Linux, es importante usar un usuario estándar sin privilegios, ya que Linux es más restrictivo con los permisos que Windows. El único con control total es root (equivalente al Administrador), y si un usuario estándar quiere hacer cambios relevantes, el sistema le pedirá su contraseña para darle privilegios temporalmente.

Además, los permisos no dependen solo del archivo ni solo del usuario, sino de la relación entre ambos: cada archivo o directorio define qué puede hacer su propietario, su grupo y el resto de usuarios (lectura, escritura y ejecución), y estos permisos se pueden consultar con comandos como ls -l.

Se creó un usuario nuevo llamado usuarioSeguro sin permisos de sudo, de esta forma este usuario se puede usar como usuario cotidiano, sin perjudicar la seguridad del sistema. Para eso se abrió una terminal en Kali Linux y se uso el comando sudo adduser usuarioSeguro, este mismo comando para ser ejecutado te pide una contraseña maestra. 

![Usuario seguro](https://github.com/user-attachments/assets/250b605a-ab1c-4108-9d82-53be6cade4e0)

A continuación se observa que el usuario creado no tiene permisos de sudo (privilegios) en el sistema operativo.

![Usuario seguro 2](https://github.com/user-attachments/assets/2adc40d8-0ae8-4f04-858d-cdb6ad900a7f)

Proseguimos a crear un archivo en el escritorio llamado prueba.txt con este mismo vamos a ver los permisos que puede llegar a tener ese archivo. Como podemos observar en la siguiente imagen, se generó un archivo con el usuario Kali, y se cambió el permiso de escritura de ese archivo para que otros puedan editarlo (chmod o+w prueba.txt), de esta forma el usuario llamado usuarioSeguro tiene la posibilidad de poder editarlo sin ser el creador del archivo. Esto es solo un ejemplo de como modificar el acceso al archivo, tanto para su ejecución (x), lectura (r) y escritura (w). Dependiendo de la necesidad de los usuarios y de la seguridad que requiera el sistema se puede ir modificando esos permisos. 

![Archivo prueba](https://github.com/user-attachments/assets/bb46c65c-b51c-4ccc-9de7-baaf376a7e2a)

Finalmente, vamos a actualizar el sistema operativo para protegerlo de posibles vulnerabilidades y estar al día con el parche de seguridad. En caso de linux la actualización funciona por paquetes y comandos en la terminal. 

![Update](https://github.com/user-attachments/assets/a4cdc143-5d78-4277-8483-e4eb9556152a)

![Upgrade](https://github.com/user-attachments/assets/92ccefe2-8650-49ea-a7e4-4f09aec06383)

![Upgrade end](https://github.com/user-attachments/assets/e64289b7-061b-4afb-8120-dd164950d2f6)

## 4 - Snapshot Inicial

Por último, se creará un snapshot inicial de cada máquina virtual del laboratorio. Esta instantánea actúa como punto de control para devolver el sistema a su estado original no modificado ante cualquier infección, alteración de archivos de sistema o fallo durante los ejercicios de ciberseguridad.

![Snapshot linux](https://github.com/user-attachments/assets/05c7f22b-a11c-4772-afa1-65d5c7a125d4)

![Snapshot windows](https://github.com/user-attachments/assets/d34121f9-0821-41f3-938a-d94c6bceb0e0)
