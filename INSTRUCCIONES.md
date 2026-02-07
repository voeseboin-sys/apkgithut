# 🚀 INSTRUCCIONES RÁPIDAS - Gestión Fábrica v2.0

## ⚡ MÉTODO ULTRA-RÁPIDO (2 comandos)

```bash
# 1. Extraer y entrar al directorio
cd ~/Descargas && tar -xzvf apkgithut-2.0.tar.gz && cd apkgithut-2.0

# 2. Ejecutar configuración automática
chmod +x setup-github.sh && ./setup-github.sh vbn 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
```

**Listo!** Ahora espera 10-20 minutos y descarga tu APK desde:
https://github.com/voeseboin-sys/vbn/actions

---

## 📋 Paso a Paso Detallado

### Paso 1: Extraer Archivos

```bash
cd ~/Descargas
tar -xzvf apkgithut-2.0.tar.gz
cd apkgithut-2.0
```

### Paso 2: Verificar Entorno (Opcional pero recomendado)

```bash
./scripts/check-environment.sh
```

### Paso 3: Configurar GitHub

```bash
chmod +x setup-github.sh
./setup-github.sh vbn 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
```

### Paso 4: Esperar Compilación

1. Abre: https://github.com/voeseboin-sys/vbn/actions
2. Espera 10-20 minutos (primera vez)
3. Busca el check verde ✅

### Paso 5: Descargar APK

1. Click en el workflow completado
2. Desplázate a **Artifacts**
3. Descarga `apk-debug-v2.0`

### Paso 6: Instalar en Android

1. Transfiere el APK a tu teléfono
2. Abre el archivo
3. Concede permisos
4. ¡Listo!

---

## 🔄 Para Actualizar la App

```bash
cd ~/Descargas/apkgithut-2.0

# Hacer cambios en main.py, factory.kv, etc.

# Subir cambios
git add .
git commit -m "Mis cambios"
git push origin main

# Esperar 5-10 minutos y descargar nueva APK
```

---

## 🐛 Si Algo Falla

### Error de permisos
```bash
git remote set-url origin https://voeseboin-sys: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@github.com/voeseboin-sys/vbn.git
git push origin main
```

### Verificar todo
```bash
./scripts/check-environment.sh
```

---

## 🔗 Enlaces Directos

| Recurso | URL |
|---------|-----|
| **Actions** | https://github.com/voeseboin-sys/vbn/actions |
| **Releases** | https://github.com/voeseboin-sys/vbn/releases |
| **Repo** | https://github.com/voeseboin-sys/vbn |

---

**¡Tu APK se compilará automáticamente cada vez que hagas `git push`!** 🎉
