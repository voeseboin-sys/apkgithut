# 🏭 Gestión Fábrica v2.0 - GitHub Actions

[![Build Android APK v2.0](https://github.com/voeseboin-sys/vbn/actions/workflows/build.yml/badge.svg)](https://github.com/voeseboin-sys/vbn/actions/workflows/build.yml)

Aplicación de gestión de fábrica desarrollada con Python, KivyMD y compilada automáticamente usando **GitHub Actions**.

---

## 📋 Información del Proyecto

| Campo | Valor |
|-------|-------|
| **Usuario** | voeseboin-sys |
| **Repositorio** | vbn |
| **Email** | voeseboin@gmail.com |
| **Versión** | 2.0.0 |

---

## ✨ Características v2.0

- 📱 **Modo Landscape**: Diseño optimizado para visualización horizontal
- 🎨 **Tema Oscuro Moderno**: UI con KivyMD Material Design 3
- 💰 **Moneda Guaraníes**: Formato `Gs. 1.000.000`
- 🗄️ **Base de Datos SQLite**: Datos persistentes localmente
- 📊 **6 Módulos**: Panel, Inventario, Producción, Ventas, Gastos, Reportes
- 📄 **PDF + Share Intent**: Genera PDF y abre menú de compartir Android

### 🐛 Correcciones v2.0

- ✅ Compatibilidad con **Ubuntu 24.04** (libtinfo6)
- ✅ **KivyMD 1.2.0** (versión corregida, 2.0.0 no existía)
- ✅ **Android SDK Build-Tools** instalado correctamente
- ✅ **GitHub Actions v4** (sin deprecaciones)

---

## 🚀 Cómo Usar (Método Rápido)

### 1. Extraer y Configurar

```bash
# Extraer el archivo
cd ~/Descargas
tar -xzvf apkgithut-2.0.tar.gz
cd apkgithut-2.0

# Ejecutar script de configuración
chmod +x setup-github.sh
./setup-github.sh vbn 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
```

### 2. Esperar y Descargar APK

1. Ve a: https://github.com/voeseboin-sys/vbn/actions
2. Espera 10-20 minutos (primera compilación)
3. Descarga la APK desde **Artifacts** → `apk-debug-v2.0`

---

## 📝 Cómo Usar (Método Manual)

### Paso 1: Configurar Git

```bash
cd apkgithut-2.0

git config --global user.email "voeseboin@gmail.com"
git config --global user.name "voeseboin-sys"

git init
git remote add origin https://voeseboin-sys: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@github.com/voeseboin-sys/vbn.git
```

### Paso 2: Subir Código

```bash
git add .
git commit -m "Gestión Fábrica v2.0"
git branch -M main
git push -u origin main
```

### Paso 3: Descargar APK

- Ve a: https://github.com/voeseboin-sys/vbn/actions
- Espera a que termine (badge verde)
- Descarga desde **Artifacts** → `apk-debug-v2.0`

---

## 📁 Estructura del Proyecto

```
apkgithut-2.0/
├── .github/
│   └── workflows/
│       └── build.yml           # Workflow GitHub Actions v2.0 ⭐
├── modules/
│   ├── __init__.py
│   └── pdf_generator.py        # PDF + Share Intent
├── scripts/
│   └── check-environment.sh    # Verificación de entorno
├── main.py                      # Aplicación principal
├── factory.kv                   # Interfaz de usuario
├── buildozer.spec               # Configuración Android
├── requirements.txt             # Dependencias corregidas
├── setup-github.sh              # Script de configuración
├── .gitignore                   # Archivos ignorados
└── README.md                    # Este archivo
```

---

## 🔧 Verificación del Entorno

Antes de compilar, verifica que todo esté correcto:

```bash
./scripts/check-environment.sh
```

Este script verifica:
- ✅ Python 3.8+ instalado
- ✅ Java JDK 17 instalado
- ✅ Dependencias del sistema
- ✅ Dependencias Python
- ✅ Buildozer instalado
- ✅ Archivos del proyecto

---

## 🔄 Actualizar la App

Para hacer cambios y recompilar:

```bash
# Hacer cambios en los archivos (main.py, factory.kv, etc.)

# Subir cambios
git add .
git commit -m "Descripción de cambios"
git push origin main

# Esperar 5-10 minutos y descargar nueva APK
```

---

## 📥 Descargar la APK

### Opción 1: Desde GitHub Actions (Artifacts)

1. Ve a la pestaña **Actions** en tu repositorio
2. Selecciona el workflow más reciente
3. Desplázate hacia abajo a **Artifacts**
4. Descarga `apk-debug-v2.0`

### Opción 2: Desde Releases

Cada push a `main` crea automáticamente un Release con la APK:

1. Ve a **Releases** en tu repositorio
2. Descarga la última versión

---

## 📱 Instalar en Android

1. Transfiere el archivo APK a tu teléfono
2. Abre el archivo (necesitas permitir "Fuentes desconocidas")
3. Concede permisos de almacenamiento
4. ¡Listo!

---

## 🐛 Solución de Problemas

### Error: "Permission denied" al hacer push

```bash
git remote set-url origin https://voeseboin-sys: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@github.com/voeseboin-sys/vbn.git
```

### Error: "Build failed" en GitHub Actions

1. Ve a **Actions** → Seleccionar workflow fallido
2. Revisa los logs de error
3. Errores comunes:
   - **Timeout**: Aumentar `timeout-minutes` en build.yml
   - **Dependencias faltantes**: Verificar requirements.txt
   - **Error de sintaxis**: Revisar main.py y factory.kv

### Verificar estado del entorno local

```bash
./scripts/check-environment.sh
```

---

## 📊 Flujo de Trabajo

```
┌─────────────┐    ┌─────────────────┐    ┌─────────────┐
│  git push   │───→│ GitHub Actions  │───→│  APK Lista  │
│   a main    │    │  (10-20 min)    │    │  en Artifacts│
└─────────────┘    └─────────────────┘    └─────────────┘
```

---

## 📋 Dependencias (requirements.txt)

```
kivy==2.2.1
kivymd==1.2.0          # ← CORREGIDO: 2.0.0 no existía
fpdf2==2.7.5
plyer==2.1.0
pillow==10.0.0
buildozer==1.5.0
Cython==0.29.36
```

---

## 🔗 Enlaces Útiles

| Recurso | URL |
|---------|-----|
| **Repositorio** | https://github.com/voeseboin-sys/vbn |
| **GitHub Actions** | https://github.com/voeseboin-sys/vbn/actions |
| **Releases** | https://github.com/voeseboin-sys/vbn/releases |
| **Crear Token** | https://github.com/settings/tokens |

---

## 📝 Notas Importantes

- **Primera compilación**: Toma más tiempo (15-20 min) por descarga de SDK/NDK
- **Compilaciones posteriores**: Más rápidas (5-10 min) gracias al caché
- **Tamaño de APK**: Aproximadamente 15-25 MB
- **Requisitos Android**: API 21+ (Android 5.0+)

---

## 🤝 Contribuir

1. Fork el repositorio
2. Crea una rama: `git checkout -b feature/nueva-funcion`
3. Commit tus cambios: `git commit -am 'Agregar nueva función'`
4. Push a la rama: `git push origin feature/nueva-funcion`
5. Crea un Pull Request

---

## 📄 Licencia

Proyecto de uso libre para fines comerciales y personales.

---

**Desarrollado por voeseboin** | [voeseboin@gmail.com](mailto:voeseboin@gmail.com)

**Versión 2.0** - Compatible con Ubuntu 24.04 y GitHub Actions v4
