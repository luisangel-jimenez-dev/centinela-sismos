# 🧰 Guía de instalación: prepara tu computadora

Antes de la práctica necesitas **5 programas**. Esta guía te dice cómo instalar cada uno y
cómo comprobar que funciona. ⏱️ Si no tienes ninguno, calcula unos **20 a 30 minutos**.

| # | Programa | ¿Para qué lo usamos? | ¿Obligatorio? |
|---|---|---|---|
| 1 | **Git** | Guardar versiones del código y subirlo a GitHub | ✅ Sí |
| 2 | **Node.js** (incluye **npm**) | Correr y compilar el tablero en React | ✅ Sí |
| 3 | **Terraform** | Crear la infraestructura en AWS con código | ✅ Sí |
| 4 | **AWS CLI** | Conectar tu computadora con AWS | ✅ Sí |
| 5 | **GitHub CLI** (`gh`) | Iniciar sesión en GitHub desde la terminal | 🟡 Recomendado |
| ➕ | **VS Code** | Editar el código cómodamente | 🟡 Opcional |

> ¿Ya tienes alguno? Sáltate a **[✅ Comprueba que todo funciona](#-comprueba-que-todo-funciona)**
> y solo instala lo que te falte.

---

## 🪟 Windows

### ⚡ Opción rápida: todo con un comando (Windows 10/11)

1. Abre el menú Inicio, escribe **cmd** y abre **Símbolo del sistema**.
2. Copia y pega este comando y presiona Enter:

```bat
winget install --id Git.Git -e && winget install --id OpenJS.NodeJS.LTS -e && winget install --id Hashicorp.Terraform -e && winget install --id Amazon.AWSCLI -e && winget install --id GitHub.cli -e
```

3. Acepta los mensajes que aparezcan (escribe `Y` si te pregunta y da **Sí** a las ventanas de permisos).
4. **Cierra CMD y vuelve a abrirlo** (¡importante!).
5. Ve a **[✅ Comprueba que todo funciona](#-comprueba-que-todo-funciona)**.

> ¿Dice que `winget` no se reconoce como un comando? Usa la opción paso a paso de abajo.

### 🐢 Opción paso a paso (con instaladores)

#### 1. Git
1. Descarga: https://git-scm.com/download/win (empieza solo; si no, elige **64-bit Git for Windows Setup**).
2. Abre el instalador y da **Next** en todo (las opciones que trae están bien).
3. Comprueba en una CMD **nueva**: `git --version`

#### 2. Node.js (trae npm)
1. Descarga: https://nodejs.org. Elige el botón de la versión **LTS** (debe ser 22 o mayor).
2. Abre el instalador → **Next** en todo → **Install**.
   (Si te pregunta por "Tools for Native Modules", **no** hace falta marcarlo.)
3. Comprueba: `node --version` y `npm --version`

#### 3. Terraform
Terraform no tiene instalador con "Siguiente, Siguiente". Hay dos formas:

**Forma fácil** (en CMD):
```bat
winget install --id Hashicorp.Terraform -e
```

**Forma manual** (si no tienes winget):
1. Descarga: https://developer.hashicorp.com/terraform/install → **Windows** → **AMD64** (un `.zip`).
2. Crea la carpeta `C:\terraform` y descomprime ahí el archivo `terraform.exe`.
3. Agrega esa carpeta al **PATH**, para que Windows encuentre el comando:
   - Inicio → escribe **variables de entorno** → **Editar las variables de entorno del sistema**.
   - Botón **Variables de entorno…**
   - En la parte de arriba (variables de tu usuario) selecciona **Path** → **Editar** → **Nuevo** → escribe `C:\terraform` → **Aceptar** en todas las ventanas.
4. Comprueba en una CMD **nueva**: `terraform version`

#### 4. AWS CLI
1. Descarga: https://awscli.amazonaws.com/AWSCLIV2.msi
2. Abre el instalador → **Next** → **Next** → **Install** → **Finish**.
3. Comprueba en una CMD **nueva**: `aws --version`

#### 5. GitHub CLI (recomendado)
1. Descarga: https://cli.github.com → botón **Download for Windows**.
2. Instala con **Next** en todo.
3. Comprueba: `gh --version`

#### ➕ VS Code (opcional)
https://code.visualstudio.com → **Download for Windows** → instala.
Marca la casilla **"Agregar a PATH"** para poder abrir carpetas con `code .`

---

## 🍎 Mac

1. Abre la app **Terminal** (búscala con `Cmd + Espacio`).
2. Instala **Homebrew** (el "instalador de programas" de Mac) si no lo tienes:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
   Al terminar, **sigue las instrucciones que te muestra** (te pide copiar 2 líneas para agregarlo al PATH).
3. Instala todo:
   ```bash
   brew install git node awscli gh
   brew tap hashicorp/tap
   brew install hashicorp/tap/terraform
   ```
4. Cierra y vuelve a abrir la Terminal.

---

## 🐧 Linux (Ubuntu / Debian)

```bash
sudo apt update && sudo apt install -y git curl unzip

# Node.js 22 (LTS)
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt install -y nodejs

# Terraform
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install -y terraform

# AWS CLI
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o awscliv2.zip
unzip awscliv2.zip && sudo ./aws/install

# GitHub CLI
sudo apt install -y gh
```

---

## ✅ Comprueba que todo funciona

Abre una terminal **nueva** (CMD en Windows, Terminal en Mac/Linux) y corre uno por uno:

```bash
git --version
node --version
npm --version
terraform version
aws --version
gh --version
```

Debes ver algo parecido a esto (los números pueden ser más nuevos, no importa):

```
git version 2.47.0
v22.11.0               ← debe empezar con v22 o mayor
10.9.0
Terraform v1.10.0      ← debe ser 1.10 o mayor
aws-cli/2.22.0 ...     ← debe empezar con aws-cli/2
gh version 2.63.0
```

🎉 **¡Si todos responden con un número, estás listo!**

---

## 🔗 Último paso: conecta Git con tu GitHub (una sola vez)

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "el-correo-de-tu-github@ejemplo.com"
git config --global init.defaultBranch main

gh auth login
```

En `gh auth login` elige: **GitHub.com** → **HTTPS** → **Yes** → **Login with a web browser**.
Copia el código que aparece y pégalo en la página que se abre.

✅ Comprueba con `gh auth status`: debe decir **Logged in to github.com**.

---

## 🆘 Si algo sale mal

| Problema | Solución |
|---|---|
| `"xxx" no se reconoce como un comando interno o externo` | **Cierra y vuelve a abrir la terminal.** Si sigue igual, reinicia la computadora. Si aun así no, reinstala ese programa. |
| `node --version` dice v18, v20 o menor | Tienes una versión vieja: instala la **LTS** de https://nodejs.org encima |
| `terraform` no se reconoce (instalación manual) | Revisa que `terraform.exe` esté en `C:\terraform` y que esa carpeta esté en el **Path** (paso 3 de Terraform) |
| `aws --version` dice `aws-cli/1...` | Tienes la versión 1 (vieja). Instala la versión 2 con el `.msi` de arriba |
| PowerShell dice que *la ejecución de scripts está deshabilitada* | Usa **CMD**, o en PowerShell corre una vez: `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` |
| El instalador pide contraseña de administrador | En computadoras de la escuela o del trabajo, pídele ayuda a quien la administra |
| `winget` no se reconoce | Actualiza **App Installer** desde la Microsoft Store, o usa la opción paso a paso |

¿Listo? 👉 Sigue con la **[GUIA.md](GUIA.md)**.
