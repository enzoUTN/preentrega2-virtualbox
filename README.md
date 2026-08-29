# Reporte Técnico de Configuración de Laboratorio

## 1 - VirtualBox y Red Aislada
Se crearon dos máquinas virtuales con la herramienta VirtualBox. Una que tiene el sistema operativo Linux (específicamente Kali Linux) y otra con Windows 10.

A las dos máquinas virtuales se eligió la red en modo NAT (por lo menos por el momento), para que estas mismas vean al host como si fuera un modem, así no se pone en riesgo la red del hogar ni el host (la computadora que está corriendo las máquinas virtuales) y a la vez estos dos sistemas tienen acceso a internet. 

En tal caso que se quiera probar algún tipo de virus o malware, se podría descargar el archivo en modo NAT y antes de ejecutarlo, cambiar la Red en modo red interna. En este modo las máquinas virtuales quedan aisladas sin perjudicar al host, pero podrían tener comunicación entre ellas. 

![Red asilada](https://github.com/user-attachments/assets/345be234-9073-40dd-96b0-48c15e3e89fd)

## 2 - Capa Windows: Usuarios y Actualizaciones




