## 🔍 **Uso de Wfuzz y Dirb para descubrir recursos web ocultos**  
Wfuzz y Dirb son herramientas diseñadas para descubrir directorios y archivos ocultos en servidores web mediante **fuerza bruta**. Esto es útil para detectar páginas de administración, archivos de configuración o rutas que podrían contener información sensible.

---

## 🔹 **1. Dirb: Escaneo básico y sencillo**  

📌 **Instalación (si no está en Kali Linux)**  
```bash
sudo apt install dirb
```

📌 **Ejemplos de uso**  

1️⃣ **Escanear un sitio web con la lista de palabras por defecto:**  
   ```bash
   dirb http://ejemplo.com
   ```
   *Busca directorios y archivos usando una lista predefinida.*

2️⃣ **Usar una lista de palabras personalizada:**  
   ```bash
   dirb http://ejemplo.com /usr/share/wordlists/dirb/common.txt
   ```
   *(Puedes usar listas como `rockyou.txt`, `big.txt`, etc.)*

3️⃣ **Escanear un sitio con HTTPS:**  
   ```bash
   dirb https://ejemplo.com
   ```

4️⃣ **Evitar respuestas 403 (prohibido):**  
   ```bash
   dirb http://ejemplo.com -X .php,.html,.txt
   ```
   *(Busca solo archivos con ciertas extensiones.)*

---

## 🔹 **2. Wfuzz: Escaneo más avanzado y personalizable**  

📌 **Instalación en Linux:**  
```bash
sudo apt install wfuzz
```

📌 **Ejemplos de uso**  

1️⃣ **Búsqueda de directorios ocultos con una lista de palabras:**  
   ```bash
   wfuzz -c -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt --hc 404 http://ejemplo.com/FUZZ
   ```
   - `-c`: Colorea la salida en la terminal.  
   - `-w`: Especifica la lista de palabras.  
   - `FUZZ`: Marcador donde se reemplazarán las palabras.  
   - `--hc 404`: Oculta respuestas con código 404 (página no encontrada).  

2️⃣ **Buscar archivos específicos (.php, .txt, .log):**  
   ```bash
   wfuzz -c -w /usr/share/wordlists/rockyou.txt --hc 404 http://ejemplo.com/FUZZ.php
   ```

3️⃣ **Fuerza bruta en subdominios:**  
   ```bash
   wfuzz -c -w /usr/share/wordlists/amass/subdomains-top1million-110000.txt -H "Host: FUZZ.ejemplo.com" --hc 404 http://ejemplo.com
   ```

4️⃣ **Forzar autenticación básica:**  
   ```bash
   wfuzz -c -w /usr/share/wordlists/rockyou.txt --hc 404 --basic "admin:FUZZ" http://ejemplo.com/admin
   ```
   *(Prueba contraseñas en autenticación básica.)*

---

## 📌 **Conclusión**
- **Dirb** es más fácil de usar y rápido, ideal para un escaneo básico.  
- **Wfuzz** ofrece más personalización y es más potente para ataques dirigidos.  

🔹 **Combinación recomendada**:  
Usar **Dirb** para un escaneo inicial y luego **Wfuzz** para ataques más detallados. 🚀  

