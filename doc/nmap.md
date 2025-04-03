## 🔍 **Scripts de Nmap (NSE) para la búsqueda de vulnerabilidades**  

Nmap tiene un motor de scripts llamado **NSE (Nmap Scripting Engine)** que permite ejecutar scripts avanzados para escanear vulnerabilidades, detectar versiones de servicios, enumerar usuarios y más.

📌 **Para listar los scripts disponibles en Nmap:**  
```bash
ls /usr/share/nmap/scripts/
```
O usa:
```bash
nmap --script-help=default
```

---

## 🔹 **1. Escaneo de vulnerabilidades con `vuln`**  
El siguiente comando ejecuta múltiples scripts relacionados con vulnerabilidades conocidas:  
```bash
nmap --script=vuln -p 80,443 192.168.1.10
```
🔎 **Ejemplo de detección de vulnerabilidades en un servidor web:**
```bash
nmap --script=http-vuln* -p 80,443 ejemplo.com
```

---

## 🔹 **2. Detección de servicios y versiones vulnerables**
Escaneo detallado de servicios:
```bash
nmap -sV --script=version 192.168.1.10
```
*Útil para comparar versiones de software con bases de datos de vulnerabilidades (CVE).*

---

## 🔹 **3. Scripts específicos para detectar vulnerabilidades**  

### 🔥 **Vulnerabilidades en SMB (Windows)**
1️⃣ **Buscar equipos con SMB habilitado:**  
```bash
nmap --script=smb-os-discovery -p 445 192.168.1.10
```
2️⃣ **Detectar si un sistema es vulnerable a EternalBlue (MS17-010):**  
```bash
nmap --script=smb-vuln-ms17-010 -p 445 192.168.1.10
```
3️⃣ **Detectar vulnerabilidades en SMBv2:**  
```bash
nmap --script=smb2-security-mode.nse -p 445 192.168.1.10
```

---

### 🌐 **Vulnerabilidades en servidores web**  
1️⃣ **Descubrir archivos y directorios ocultos:**  
```bash
nmap --script=http-enum -p 80,443 ejemplo.com
```
2️⃣ **Detectar vulnerabilidades en Apache, Nginx, IIS:**  
```bash
nmap --script=http-vuln-cve* -p 80,443 ejemplo.com
```
3️⃣ **Buscar fallos en configuración de SSL/TLS:**  
```bash
nmap --script=ssl-enum-ciphers -p 443 ejemplo.com
```

---

### 🔑 **Ataques de fuerza bruta**  
1️⃣ **Fuerza bruta en SSH:**  
```bash
nmap --script=ssh-brute -p 22 192.168.1.10
```
2️⃣ **Fuerza bruta en MySQL:**  
```bash
nmap --script=mysql-brute -p 3306 192.168.1.10
```
3️⃣ **Fuerza bruta en HTTP con autenticación básica:**  
```bash
nmap --script=http-brute -p 80,443 ejemplo.com
```

---

## 🚀 **Combinaciones útiles**  

### 🔹 **Escanear una red entera en busca de vulnerabilidades comunes:**  
```bash
nmap -p 21,22,80,445,3306,3389 --script=vuln 192.168.1.0/24
```

### 🔹 **Comprobar si un equipo tiene puertos abiertos y servicios vulnerables:**  
```bash
nmap -sV --script=vuln 192.168.1.10
```

---

## ⚠️ **Consideraciones éticas y legales**  
🔴 **No escanees sistemas sin permiso**. Usa estas técnicas solo en entornos de prueba o con autorización.  

---

