<div align="center">

🌐 **Idioma / Language:** **🇪🇸 Español** | [🇺🇸 Read in English](README_EN.md)

# 🚀 NativoPy Studio PRO
### Entorno Integrado de Compilación Nativa Python a C/C++ (`.exe` / `.pyd`), Empaquetado NSIS y Firma Digital

[![Versión](https://img.shields.io/badge/Versión-2.8.0_Global-blue?style=for-the-badge)](https://github.com/adsdres/NativoPy/releases)
[![Plataforma](https://img.shields.io/badge/Plataforma-Windows_10_%7C_11_(x64_%2F_x86)-0078D6?style=for-the-badge&logo=windows)](https://github.com/adsdres/NativoPy)
[![Motor](https://img.shields.io/badge/Backend-Nuitka_%2B_MSVC_%2B_NSIS-27ae60?style=for-the-badge&logo=python)](https://github.com/adsdres/NativoPy)
[![Idiomas](https://img.shields.io/badge/Idiomas-ES_%7C_EN_%7C_FR_%7C_PT_%7C_ZH-8e44ad?style=for-the-badge)](https://github.com/adsdres/NativoPy)

**Transforma tus proyectos de Python en ejecutables nativos de alto rendimiento (`.exe`), módulos binarios protegidos (`.pyd`) e instaladores profesionales de Windows (`Setup.exe`) firmados criptográficamente.**

[⬇️ Descargar Última Versión (Releases)](https://github.com/adsdres/NativoPy/releases) · [📖 Documentación](#flujo-de-trabajo-en-6-pasos) · [❓ Preguntas Frecuentes (FAQs)](#preguntas-frecuentes-faqs)

</div>

---

## ✨ Características Principales

### 🛠️ 1. Compilación Nativa en C/C++ (Protección de Propiedad Intelectual)
* **Traducción Real a Código Máquina:** A diferencia de empaquetadores tradicionales que solo comprimen el bytecode `.pyc` en un archivo ZIP autoextraíble, **NativoPy Studio** orquesta **Nuitka + Microsoft Visual C++ (MSVC)** para traducir tu código Python a C/C++ nativo.
* **Doble Modo de Salida:**
  * **Ejecutable Independiente (`.exe`):** En modo *Standalone* (carpeta optimizada de arranque instantáneo) o *Onefile* (ejecutable único portable).
  * **Módulo Binario Protegido (`.pyd`):** Compila librerías o algoritmos críticos en extensiones C nativas imposibles de descompilar, importables desde cualquier otro script Python.
* **Arquitectura Dual (64-bit y 32-bit):** Conmutación inmediata entre entornos de 64 bits y 32 bits con aislamiento automático de entornos virtuales (`venv` / `venv32`) y dependencias (`requirements.txt` / `requirements_32.txt`).

### 🔍 2. Auto-Analizador Inteligente AST y Prevención de Errores Críticos
* **Escaneo Estático de Código (AST):** Detecta automáticamente los frameworks gráficos y librerías utilizadas en tu proyecto (`PySide6`, `PyQt6`, `PyQt5`, `PySide2`, `Tkinter`/`CustomTkinter`, `NumPy`, `Pandas`, `SciPy`, `Pillow`, `Cryptography`, `Google GenAI`, etc.) e inyecta los plugins necesarios sin configuración manual.
* **Diagnóstico Preventivo de Memoria Qt/Shiboken:** Identifica conexiones `.connect(lambda...)` propensas a causar violaciones de acceso (`0xC0000005`) en binarios compilados.
* **Mitigación Automática del Error MSVC `C1002` (Out of Heap Space):** Incluye el asistente de 1 clic para aplicar el **Parche `/Od`** en modo `--low-memory` y carga nativa del toolchain de 64 bits (`vcvars64.bat`), permitiendo compilar librerías masivas (como `google.genai` con más de 160.000 líneas C) en segundos sin agotar la memoria del compilador.

### 📦 3. Generador de Instaladores Profesionales (NSIS MUI2)
* **Asistente `Setup.exe` en 1 Clic:** Genera automáticamente el instalador comercial de Windows con compresión sólida **LZMA de alta densidad**.
* **Integración Completa con Windows:**
  * Creación de accesos directos en **Escritorio** y **Menú Inicio**.
  * Registro oficial en *Programas y Características* (Panel de Control) con cálculo de tamaño estimado y desinstalador limpio (`Uninstall.exe`) que preserva las licencias del usuario en `%APPDATA%`.
  * Soporte de ejecución estándar o con elevación administrativa **UAC (`RequestExecutionLevel admin`)**.
  * **Inyección Automática de EULA:** Detecta automáticamente tu archivo `EULA.txt` o `LICENSE.txt` e incorpora la página de aceptación de términos (`MUI_PAGE_LICENSE`).

### 🔐 4. Firma Digital Multi-Modo (`SignTool`) + Sello de Tiempo RFC 3161 + SHA-256
* **Firma Criptográfica de Binarios e Instaladores:** Firma automáticamente el `.exe` y el `Setup.exe` final para evitar alertas de *Windows Defender SmartScreen*.
* **3 Modos de Certificado Soportados:**
  1. **Archivos PKCS#12 (`.pfx` y `.p12`)** con contraseña.
  2. **Huella Digital SHA1 (40 caracteres hex)** directamente desde tu **Token USB Criptográfico** o Almacén de Certificados de Windows (`/s MY /sha1`).
  3. **Nombre del Titular (Subject Name)** desde el Almacén de Certificados de Windows (`/s MY /n`).
* **Sello de Tiempo RFC 3161 (`http://timestamp.digicert.com`):** Garantiza que la firma digital siga siendo válida indefinidamente incluso después de que expire tu certificado, con **modo de respaldo offline automático** si compilas sin internet.
* **Checksum SHA-256 Automático:** Calcula y exporta el hash criptográfico de integridad al finalizar cada compilación.

---

## 📊 Comparativa de Ediciones (FREE vs PRO)

| Característica | Edición FREE | Prueba TRIAL (7 Días) | Edición PRO (Comercial) |
| :--- | :---: | :---: | :---: |
| Gestión de Entornos Virtuales (`venv`) y Dependencias | ✅ | ✅ | ✅ |
| Compilación Básica *Standalone* (`.exe`) | ✅ | ✅ | ✅ |
| Auto-Analizador AST de Dependencias | ✅ | ✅ | ✅ |
| Empaquetado en Un Solo Archivo (`--onefile`) | ❌ | ✅ | ✅ |
| Ocultar Consola de Comandos (`--windows-console-mode=disable`) | ❌ | ✅ | ✅ |
| Compilación de Módulos Protegidos (`.pyd`) | ❌ | ✅ | ✅ |
| Modo Lote (Compilación secuencial de carpetas completas) | ❌ | ✅ | ✅ |
| Personalización de Ícono (`.ico`) y Metadatos de Windows | ❌ | ✅ | ✅ |
| Optimización LTO (`--lto=yes`), MSVC Nativo y Parche `/Od` | ❌ | ✅ | ✅ |
| Uso Completo de Núcleos CPU (`--jobs`) y Prioridad de Proceso | Máx. 4 núcleos | ✅ Ilimitado | ✅ Ilimitado |
| Generador de Instalador `Setup.exe` (NSIS + EULA) | ❌ | ✅ | ✅ |
| Firma Digital (`SignTool` `.pfx`/`.p12`/Token USB + Timestamp) | ❌ | ❌ | ✅ |
| Equipos por Licencia (con reinstalación ilimitada en el mismo PC) | — | 1 Equipo | **1 Equipo (Individual)** |

---

## 🔄 Flujo de Trabajo en 6 Pasos

1. **Aislar (`1. ✨ Crear venv`):** Crea un entorno virtual limpio de 64 o 32 bits para tu proyecto.
2. **Generar Dependencias (`2. 📝 Generar reqs`):** Escanea las importaciones reales de tu proyecto y genera el archivo `requirements.txt`.
3. **Instalar (`3. 📦 Instalar`):** Instala las librerías requeridas y el motor Nuitka dentro del entorno virtual aislado.
4. **Auto-Analizar (`🔍 Auto-Analizar`):** El motor AST detecta automáticamente los plugins gráficos (`PySide6`, `PyQt6`, `Tkinter`) y banderas óptimas.
5. **Recursos y Metadatos (Pestaña 2):** Asigna el ícono `.ico`, adjunta carpetas de recursos (`assets`, `db`, `img`) con rutas relativas automáticas y define la versión/compañía del ejecutable.
6. **Compilar, Empaquetar y Firmar (Pestañas 3 y 4):** Configura el rendimiento de CPU, activa la generación del instalador NSIS + Firma Digital y presiona **`¡Compilar Proyecto!`**.

---

## 💻 Requisitos del Sistema

* **Sistema Operativo:** Windows 10 o Windows 11 (64 bits; soporta compilación cruzada a 32 bits si se cuenta con un intérprete Python x86).
* **Memoria RAM:** 8 GB mínimo (16 GB recomendados para proyectos grandes).
* **Espacio en Disco:** 3 GB libres para caché temporal de compilación C.
* **Compilador C/C++:** [Microsoft Visual Studio Build Tools 2022](https://visualstudio.microsoft.com/visual-cpp-build-tools/) (Carga de trabajo: *Desarrollo para el escritorio con C++*).
* **Empaquetador de Instaladores (Opcional):** [NSIS (Nullsoft Scriptable Install System) 3.x](https://nsis.sourceforge.io/Download).

---

## 🌐 Idiomas Soportados Nativamente

La interfaz gráfica, el Centro de Ayuda integrado y los instaladores generados con NSIS soportan 5 idiomas de forma nativa:
* 🇪🇸 **Español** (`es`)
* 🇺🇸 **English** (`en`)
* 🇫🇷 **Français** (`fr`)
* 🇧🇷 **Português** (`pt`)
* 🇨🇳 **简体中文** (`zh`)

---

## ❓ Preguntas Frecuentes (FAQs)

<details>
<summary><b>¿Por qué SignTool muestra "After Private Key filter, 0 certs were left" al firmar?</b></summary>
<br>
Ese mensaje indica que SignTool encontró el certificado pero no su Clave Privada:
<ol>
  <li>Asegúrate de seleccionar un archivo <b><code>.p12</code> o <code>.pfx</code></b> (con clave privada y contraseña), nunca un archivo <code>.cer</code> o <code>.crt</code> (que solo contiene la clave pública).</li>
  <li>Si tu certificado está en un <b>Token USB Criptográfico</b> o en el Almacén de Certificados de Windows, pega directamente la <b>Huella SHA1 de 40 caracteres</b> o el <b>Nombre del Titular</b> en el campo de certificado.</li>
</ol>
</details>

<details>
<summary><b>¿Cómo evito el error "fatal error C1002: el compilador no tiene espacio en el montón en el paso 2"?</b></summary>
<br>
En la <b>Pestaña 3 (Rendimiento Avanzado)</b>, haz clic en el botón <b><code>⚡ Parche /Od (C1002)</code></b>, activa la casilla <b><code>Baja memoria RAM (--low-memory)</code></b> y marca <b><code>Forzar MSVC (Native Tools)</code></b>. Esto evita que el optimizador de Microsoft sature su tabla de flujo de control al compilar módulos masivos.
</details>

<details>
<summary><b>¿Cómo incluyo mis Términos y Condiciones (EULA) en el instalador Setup.exe?</b></summary>
<br>
Coloca un archivo llamado <code>EULA.txt</code> o <code>LICENSE.txt</code> en la carpeta de tu script Python antes de compilar. NativoPy Studio lo detectará e insertará automáticamente la página de licencia en el instalador NSIS.
</details>

---

## ⚖️ Aviso Legal y Propiedad Intelectual

**NativoPy Studio PRO** es un software comercial protegido por leyes de propiedad intelectual y tratados internacionales de derechos de autor.

> *NativoPy Studio is an independent graphical frontend and orchestration tool for Nuitka and NSIS. It is not affiliated with, sponsored, or endorsed by the Nuitka project or the Python Software Foundation.*

© 2026 **Adsdres** (`Adsdres@gmail.com`). Todos los derechos reservados.
