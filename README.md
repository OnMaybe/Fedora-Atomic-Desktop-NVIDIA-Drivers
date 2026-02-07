# Fedora-Atomic-Desktop-NVIDIA-Drivers
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| Listado de cosas propietaria que hay que instalar en fedora atomic desktop para que nvidia haga lo suyo, gracias Jensen Huang por amar linux.									                                                     |
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| akmod-nvidia (Recompilador de el modulo del kernel)							 													                                                                                                                         |	
| 																										                                                                                                                                                               |
| xorg-x11-drv-nvidia (Apis del userland)																                                                                                                                              					     |
|																										                                                                                                                                                                 |
| xorg-x11-drv-nvidia-libs (Aceleracion grafica)																				                                                                                                                             |
|																										                                                                                                                                                                 |
| xorg-x11-drv-nvidia-power (Fixes mediante trigers de systemd para gestion de energia y estados del sistema) 							                                                                        						     |
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
| Es imperativo aclarar que para la correcta instalacion de los componentes, debes de asegurarte activar los repositorios parciales suministrados por rpm-fusion mediante gnome software o por medio del comando     |  
| "fedora-third-party enable".																							                                                                                                                                         |
|																										                                                                                                                                                                 |
| Para desactivar el driver "nouveau/nova" requiere proporcionar estos argumentos del kernel, "rd.driver.blacklist=nouveau,nova_core" "modprobe.blacklist=nouveau,nova_core"			                          		     |
| "initcall_blacklist=simpledrm_platform_driver_init", argumentos extras no son necesarios en la actualidad gracias a las nuevas versiones del kernel suministrado por fedora.				                         	     |
|																									                                                                                                                                                            	     |
| El paquete "org-x11-drv-nvidia-power" requiere ser activado mediante "systemctl enable nvidia-{suspend,hibernate,resume}" y proporcionar este argumento al kernel "nvidia.NVreg_PreserveVideoMemoryAllocations=1". |
|																										                                                                                                                                                                 |
| Tecnologias como CUDA, HVENC y """VAAPI""" lo suministra runtimes de flatpak o por medio de contenedores de podman, no son necesarias desde el host al menos si usas este paradigma de manera ortodoxa.	           |
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Comandos Ostree:

"rpm-ostree update"
"rpm-ostree install"
"rpm-ostree kargs append=''"

Enlaces: 
Si tienes activo el SecureBoot, requieres de compilar tu propio paquete con las claves para que el sistema pueda validar la cadena de confianza: https://github.com/CheariX/silverblue-akmods-keys
Verifica si tu tarjeta de video es compatible con el driver Nova, proporcionado con la pila grafica estardar de linux Mesa 3D, las graficas compatibles requiere del firmware GSP: https://github.com/NVIDIA/open-gpu-kernel-modules?tab=readme-ov-file#compatible-gpus
Recopilacion sacada de: https://rpmfusion.org
