# 📋 CHANGELOG - Gestión Fábrica v2.0

## Resumen de Correcciones

Esta versión 2.0 corrige todos los errores críticos encontrados en la versión anterior para garantizar que la compilación con GitHub Actions funcione correctamente.

---

## 🐛 Errores Corregidos

### 1. DEPENDENCIAS DEL SISTEMA ❌ → ✅

**Problema:** `libtinfo5` no existe en Ubuntu 24.04

**Solución:** Reemplazado por `libtinfo6` y `ncurses-bin`

```diff
- libtinfo5
+ libtinfo6
+ ncurses-bin
```

**Archivo modificado:** `.github/workflows/build.yml`

---

### 2. DEPENDENCIAS PYTHON ❌ → ✅

**Problema:** `kivymd==2.0.0` NO EXISTE en PyPI

**Versiones disponibles:** 1.2.0, 1.1.1, 1.0.2

**Solución:** Usar versión existente `kivymd==1.2.0`

```diff
- kivymd==2.0.0
+ kivymd==1.2.0
```

**Archivos modificados:**
- `requirements.txt`
- `buildozer.spec`

---

### 3. ANDROID SDK ❌ → ✅

**Problema:** `aidl` no encontrado

**Causa:** Android SDK Build-Tools no estaba instalado correctamente

**Solución:** 
- Instalar Android SDK Command Line Tools manualmente
- Instalar Build-Tools 34.0.0 (incluye aidl)
- Aceptar licencias sin interacción (`yes | sdkmanager` fallaba)

```yaml
# Nuevo método sin interacción
mkdir -p android-sdk/licenses
echo "24333f8a63b6825ea9c5514f83c2829b004d1fee" > android-sdk/licenses/android-sdk-license
sdkmanager --sdk_root=$ANDROID_SDK_ROOT "build-tools;34.0.0"
```

**Archivo modificado:** `.github/workflows/build.yml`

---

### 4. GITHUB ACTIONS DEPRECADOS ❌ → ✅

**Problema:** Acciones v3 están deprecadas

**Solución:** Actualizar todas las acciones a v4

```diff
- uses: actions/checkout@v3
+ uses: actions/checkout@v4

- uses: actions/cache@v3
+ uses: actions/cache@v4

- uses: actions/upload-artifact@v3
+ uses: actions/upload-artifact@v4

- uses: actions/setup-python@v4
+ uses: actions/setup-python@v5
```

**Archivo modificado:** `.github/workflows/build.yml`

---

## 📁 Archivos Nuevos

### `scripts/check-environment.sh`
Script de verificación del entorno local antes de compilar.

### `.env.template`
Template para variables de entorno (seguridad).

### `INSTRUCCIONES.md`
Guía rápida de 2 pasos para configuración.

---

## 📁 Archivos Modificados

| Archivo | Cambios |
|---------|---------|
| `.github/workflows/build.yml` | Workflow completamente reescrito con todas las correcciones |
| `requirements.txt` | Versión de KivyMD corregida (1.2.0) |
| `buildozer.spec` | Requirements actualizados, versión 2.0.0 |
| `setup-github.sh` | Ahora acepta parámetros: `./setup-github.sh REPO TOKEN` |
| `README.md` | Documentación actualizada para v2.0 |
| `.gitignore` | Más completo, incluye android-sdk/ |

---

## 📁 Archivos Sin Cambios (Mantienen Funcionalidad)

- `main.py` - Lógica principal intacta
- `factory.kv` - Interfaz de usuario intacta
- `modules/__init__.py` - Sin cambios
- `modules/pdf_generator.py` - PDF + Share Intent intacto

---

## 🚀 Cómo Actualizar desde v1.0

### Opción 1: Reemplazo Completo (Recomendado)

```bash
# 1. Hacer backup de tu carpeta actual
cd ~/Descargas
mv apkgithut apkgithut-backup

# 2. Extraer nueva versión
tar -xzvf apkgithut-2.0.tar.gz

# 3. Configurar
cd apkgithut-2.0
chmod +x setup-github.sh
./setup-github.sh vbn GITHUB_TOKEN_AQUI
```

### Opción 2: Reemplazar Solo Archivos Críticos

```bash
cd ~/Descargas/apkgithut

# Reemplazar archivos críticos
cp ../apkgithut-2.0/.github/workflows/build.yml .github/workflows/build.yml
cp ../apkgithut-2.0/requirements.txt requirements.txt
cp ../apkgithut-2.0/buildozer.spec buildozer.spec

# Subir cambios
git add .
git commit -m "Actualizar a v2.0 - Correcciones GitHub Actions"
git push origin main
```

---

## ✅ Verificación Post-Actualización

Después de actualizar, verifica:

1. **GitHub Actions ejecutándose:** https://github.com/voeseboin-sys/vbn/actions
2. **Sin errores de deprecación:** Las acciones deben ser v4/v5
3. **APK generada:** Debe aparecer en Artifacts

---

## 📊 Comparación de Versiones

| Aspecto | v1.0 | v2.0 |
|---------|------|------|
| Ubuntu | 22.04 (libtinfo5) | 24.04 (libtinfo6) |
| KivyMD | 2.0.0 (❌ no existe) | 1.2.0 (✅ existe) |
| Android SDK | Instalación básica | Build-Tools 34.0.0 |
| GitHub Actions | v3 (deprecado) | v4/v5 (actual) |
| Scripts | setup-github.sh básico | Con parámetros + check-environment |

---

**Fecha de release:** 2024-02-07  
**Compatibilidad:** Ubuntu 22.04+, GitHub Actions, Android API 21+
