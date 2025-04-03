### 🔍 **Escaneo y detección con Nmap y Nikto**  
Nmap y Nikto son herramientas esenciales en ciberseguridad para descubrir equipos en la red, analizar servicios y buscar vulnerabilidades. Aquí explico cómo usarlas.

---

## 🔹 **1. Nmap: Escaneo de redes y detección de puertos abiertos**  

📌 **Instalación en Linux y Windows:**  
- En **Kali Linux** y muchas distros ya está instalado. Si no, puedes instalarlo con:  
  ```bash
  sudo apt install nmap
  ```
- En **Windows**, descárgalo desde [nmap.org](https://nmap.org/download.html).

📌 **Ejemplos de uso:**
1️⃣ **Descubrir equipos en una red local:**  
   ```bash
   nmap -sn 192.168.1.0/24
   ```
   *Muestra qué hosts están activos en la red.*  

2️⃣ **Escaneo de puertos abiertos en un objetivo:**  
   ```bash
   nmap -p- 192.168.1.10
   ```
   *Escanea todos los puertos (0-65535).*  

3️⃣ **Detectar servicios y versiones en ejecución:**  
   ```bash
   nmap -sV -p 22,80,443 192.168.1.10
   ```
   *Identifica qué servicios están corriendo y sus versiones.*  

4️⃣ **Detectar el sistema operativo:**  
   ```bash
   nmap -O 192.168.1.10
   ```
   *Intenta determinar el SO del objetivo.*  

5️⃣ **Escaneo de vulnerabilidades con scripts NSE:**  
   ```bash
   nmap --script=vuln 192.168.1.10
   ```
   *Ejecuta scripts de detección de vulnerabilidades comunes.*

---

## 🔹 **2. Nikto: Escaneo de vulnerabilidades web**  

📌 **Instalación en Linux:**  
Si no está instalado en Kali Linux:  
  ```bash
  sudo apt install nikto
  ```

📌 **Ejemplos de uso:**  
1️⃣ **Escanear un sitio web:**  
   ```bash
   nikto -h http://192.168.1.10
   ```
   *Busca vulnerabilidades en el servidor web.*  

2️⃣ **Especificar un puerto (por ejemplo, HTTPS en el 443):**  
   ```bash
   nikto -h https://192.168.1.10 -p 443
   ```
   
3️⃣ **Usar un proxy para anonimizar el escaneo:**  
   ```bash
   nikto -h http://192.168.1.10 -useproxy http://127.0.0.1:8080
   ```
   
4️⃣ **Guardar el reporte en un archivo:**  
   ```bash
   nikto -h http://192.168.1.10 -o reporte.txt
   ```

---

## 📌 **Combinación de Nmap y Nikto**
1. Usa **Nmap** para identificar qué puertos están abiertos y qué servicios están corriendo.  
2. Luego, usa **Nikto** para analizar vulnerabilidades en servidores web detectados.  

Ejemplo:  
```bash
nmap -p 80,443 --open -oG webservers.txt 192.168.1.0/24
cat webservers.txt | grep "80/open" | cut -d " " -f 2 | xargs -I{} nikto -h {}
```
*Este comando escanea la red, identifica servidores web y ejecuta Nikto en cada uno de ellos.*

---

## ⚠️ **Consideraciones Legales**
Antes de escanear equipos ajenos, asegúrate de **tener permiso**. El uso indebido de estas herramientas puede ser ilegal en muchas jurisdicciones.

