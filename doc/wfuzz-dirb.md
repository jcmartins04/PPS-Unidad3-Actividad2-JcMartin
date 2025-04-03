# 🚀 **Uso de Wfuzz y Dirb para localizar recursos web ocultos**  

## 🔎 **1. Escaneo con Wfuzz**  
Wfuzz es una herramienta de fuerza bruta que permite buscar directorios y archivos ocultos en servidores web.  

---

### 📌 **1.1 Escaneo básico de directorios**
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 http://ejemplo.com/FUZZ
```
- `-c` → Muestra la salida en color.  
- `-z file,/usr/share/wordlists/dirb/common.txt` → Usa un diccionario de directorios comunes.  
- `--hc 404` → Oculta respuestas con código 404 (no encontrado).  
- `FUZZ` → Marcador que Wfuzz reemplaza por cada palabra del diccionario.  

---

### 📌 **1.2 Buscar archivos específicos (.php, .html, .txt)**
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 http://ejemplo.com/FUZZ.php
```
También puedes buscar varios tipos de archivos:
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 http://ejemplo.com/FUZZ.{php,html,txt}
```

---

### 📌 **1.3 Fuerza bruta en parámetros GET**
Si el sitio tiene parámetros en la URL:
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 "http://ejemplo.com/index.php?pagina=FUZZ"
```

---

### 📌 **1.4 Escaneo con múltiples hilos (más rápido)**
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 -t 50 http://ejemplo.com/FUZZ
```
- `-t 50` → Usa 50 hilos para acelerar el escaneo.

---

## 🔎 **2. Escaneo con Dirb**  
Dirb es una herramienta similar a Wfuzz, pero más sencilla de usar.  

---

### 📌 **2.1 Escaneo básico de directorios**  
```bash
dirb http://ejemplo.com/
```
Por defecto, usa un diccionario predefinido en `/usr/share/dirb/wordlists/common.txt`.

---

### 📌 **2.2 Especificar un diccionario personalizado**  
```bash
dirb http://ejemplo.com/ /usr/share/wordlists/rockyou.txt
```

---

### 📌 **2.3 Escanear un sitio HTTPS**  
```bash
dirb https://ejemplo.com/
```

---

### 📌 **2.4 Buscar archivos específicos (.php, .html, .txt)**  
```bash
dirb http://ejemplo.com/ -X .php,.html,.txt
```
- `-X` → Extensiones de archivo a buscar.

---

## 🔥 **Ejemplo de flujo completo**
1️⃣ **Escanear directorios con Dirb:**  
```bash
dirb http://ejemplo.com/
```
2️⃣ **Escanear directorios con Wfuzz y filtrar respuestas 404:**  
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 http://ejemplo.com/FUZZ
```
3️⃣ **Buscar archivos PHP ocultos:**  
```bash
wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --hc 404 http://ejemplo.com/FUZZ.php
```

---

## ⚠️ **Consideraciones Éticas y Legales**  
🔴 **No escanees sitios sin permiso**. Estas herramientas deben usarse solo en entornos de prueba o con autorización.  


