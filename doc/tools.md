Para obtener información pública sobre un dominio o una dirección IP, se pueden usar varias herramientas y servicios. Explico cómo hacerlo con **Whois**, **DomainTools** y **dnsrecon**.

### 🔍 1. **Whois**  
Whois es un protocolo que permite consultar bases de datos de registro de dominios y obtener información como el propietario, la fecha de creación, el estado y los servidores DNS asociados.

#### 📌 **Uso en Linux y Windows**:
- En **Linux** y **macOS**, puedes usar el comando:
  ```bash
  whois ejemplo.com
  ```
- En **Windows**, necesitarás instalar una herramienta de terceros como `whois.exe` de Sysinternals o usar:
  ```powershell
  nslookup -type=any ejemplo.com
  ```

#### 🔹 ¿Qué información puedes obtener?
- Propietario del dominio (en algunos casos puede estar oculto por privacidad).
- Servidores DNS.
- Fecha de registro y expiración.
- Información del registrador.

---

### 🌐 2. **DomainTools** (https://whois.domaintools.com)  
DomainTools ofrece una interfaz web para hacer consultas Whois, además de:
- **Historial de WHOIS** (si el dominio ha cambiado de propietario).
- **Historial de IPs** (qué IPs ha usado en el pasado).
- **Registro de subdominios**.

Para usarlo:
1. Ve a [whois.domaintools.com](https://whois.domaintools.com).
2. Escribe el dominio y revisa la información obtenida.

**⚠️ Nota:** Algunas funcionalidades avanzadas requieren una cuenta de pago.

---

### 🕵️‍♂️ 3. **dnsrecon**  
`dnsrecon` es una herramienta de **reconocimiento de DNS** que permite obtener información sobre un dominio realizando diferentes tipos de consultas.

#### 📌 **Instalación en Kali Linux**:
Viene preinstalado, pero si necesitas instalarlo:
```bash
sudo apt install dnsrecon
```

#### 🔹 **Ejemplo de uso**:
1. **Consulta básica de registros DNS:**
   ```bash
   dnsrecon -d ejemplo.com
   ```
2. **Enumeración de subdominios con fuerza bruta:**
   ```bash
   dnsrecon -d ejemplo.com -D subdominios.txt -t brt
   ```
3. **Búsqueda de registros de transferencia de zona (Zone Transfer):**
   ```bash
   dnsrecon -d ejemplo.com -t axfr
   ```
   *Si el servidor DNS permite transferencia de zona, puede revelar todos los subdominios y hosts registrados.*

---

### 📌 **Conclusión**
- **Whois** es útil para obtener información de registro de dominios.
- **DomainTools** amplía la información con historial de cambios y subdominios.
- **dnsrecon** permite analizar registros DNS y descubrir subdominios.

📌 **Recuerda**: La información obtenida es pública, pero su uso debe cumplir con las normativas de privacidad y ética en ciberseguridad.
