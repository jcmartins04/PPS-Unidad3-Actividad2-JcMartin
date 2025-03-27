# PPS-Unidad3-Actividad2-JcMartin
## Detección de equipos, puertos, servicios,vulnerabilidades.


Obtención de información pública
whois dominio.com


Obtiene información sobre el registro de un dominio, incluyendo datos del propietario y servidores DNS.


dnsrecon -d dominio.com


Realiza una enumeración DNS para obtener subdominios, registros MX, TXT y otros datos relevantes.


dnsrecon -d dominio.com -D subdominios.txt -t brt


Usa fuerza bruta con una lista de palabras para descubrir subdominios ocultos.


dnsrecon -d dominio.com -t axfr


Intenta realizar una transferencia de zona DNS para obtener una lista completa de registros del dominio.



Búsqueda de equipos, puertos y vulnerabilidades
nmap -p- IP


Escanea todos los puertos de un objetivo para identificar los abiertos.


nmap -sV -sC -O IP


Detecta versiones de servicios, ejecuta scripts de reconocimiento y obtiene información del sistema operativo.


nmap --script=vuln IP


Ejecuta scripts de detección de vulnerabilidades en el objetivo.


*locate .nse | grep vuln


Busca scripts NSE de Nmap relacionados con la detección de vulnerabilidades.


nikto -h http://IP


Escanea un servidor web en busca de vulnerabilidades y configuraciones erróneas.


nikto -h http://IP -Tuning 1234567890


Realiza un escaneo más exhaustivo probando todas las técnicas disponibles.



Búsqueda de recursos en servidores web
wfuzz -c -z file,/usr/share/seclists/Discovery/Web-Content/common.txt --hc 404 http://IP/FUZZ


Fuerza bruta para encontrar directorios y archivos ocultos en un servidor web.


wfuzz -c -z file,wordlist.txt -z list,.php,.html,.txt --hc 404 http://IP/FUZZFUZ2Z


Busca archivos en el servidor con extensiones específicas.


dirb http://IP/


Escanea un servidor web en busca de directorios y archivos ocultos.


dirb http://IP/ wordlist.txt


Usa una lista de palabras personalizada para mejorar la búsqueda de recursos.



Búsqueda de vulnerabilidades con SearchSploit
searchsploit apache


Busca vulnerabilidades y exploits disponibles para Apache en la base de datos de Exploit-DB.


searchsploit -x 12345


Muestra detalles completos sobre un exploit específico identificado por su ID.


searchsploit -m 12345


Copia un exploit de la base de datos a tu directorio actual para su posterior análisis y prueba.


