# Reporte Técnico de Configuración de Laboratorio

## 1 - VirtualBox y Red Aislada
Se crearon dos máquinas virtuales con la herramienta VirtualBox. Una que tiene el sistema operativo Linux (específicamente Kali Linux) y otra con Windows 10.

Antes de la instalación, a las dos máquinas virtuales se eligió la red en modo NAT (por lo menos por el momento), para que estas mismas vean al host como si fuera un modem, así no se pone en riesgo la red del hogar ni el host (la computadora que está corriendo las máquinas virtuales) y a la vez estos dos sistemas tienen acceso a internet. 

En tal caso que se quiera probar algún tipo de virus o malware, se podría descargar el archivo en modo NAT y antes de ejecutarlo, cambiar la Red en modo red interna. En este modo las máquinas virtuales quedan aisladas sin perjudicar al host, pero podrían tener comunicación entre ellas. 

![Red asilada](https://github.com/user-attachments/assets/345be234-9073-40dd-96b0-48c15e3e89fd)

También en la configuración de la máquina virtual se deshabilitaron los controladores de USB, para aislarlas aún más del host.

![Red asilada](https://github.com/user-attachments/assets/390a91d3-114c-4a34-92ed-8998e8092a55)

## 2 - Capa Windows: Usuarios y Actualizaciones

Una vez instalada la máquina virtual de Windows, se creó un usuario estándar. La razón de crear este usuario fue para que los posibles virus o malware que pueda descargar un usuario cotidiano (alguien que solo usa el navegador web u office) no tengan permisos de administrador, así impedimos que la amenaza no pueda ser ejecutada por este tipo de usuarios. 

![Red asilada](https://github.com/user-attachments/assets/838d01b3-3bec-4e1b-859f-d02141bb4913)

![Red asilada](https://github.com/user-attachments/assets/5052b2af-767e-4450-a174-006b6c9ece90)

También se desactivó ciertos servicios como SMB 1.0, que viene por defecto activado en Windows. Esta acción se debe a que el protocolo es muy viejo y tiene historial de ser culpable de propagación de algunos virus (como WannaCry). Actualmente, utilizamos otros protocolos más seguros y modernos para compartir archivos (como SMB 3.1.1).

![Red asilada](https://github.com/user-attachments/assets/7d93d83b-6352-4ab3-b5d9-68c28d986493)

Como las amenazas día a día buscan vulnerabilidades en el código de Windows, es necesario mantener actualizado el sistema operativo. Para poder proteger o solucionar esas vulnerabilidades, Microsoft lanza parches de seguridad. Por esta razón siempre es
recomendable actualizar lo antes posible con Windows update. 

