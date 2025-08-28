# Git - Quick Reference Manual

## Setup Initial (una sola vez)
```bash
# Configurar identidad
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@gmail.com"
```

## Crear Proyecto Nuevo
```bash
mkdir mi-proyecto
cd mi-proyecto
# ... crear archivos ...

git init
git add .
git commit -m "initial commit"
# Crear repo en GitHub.com manualmente, luego:
git remote add origin https://github.com/usuario/mi-proyecto.git
git push -u origin main
```

## Subir Proyecto Existente
```bash
cd mi-proyecto-existente
git init
git add .
git commit -m "initial commit"
# Crear repo en GitHub.com manualmente, luego:
git remote add origin https://github.com/usuario/mi-proyecto.git  
git push -u origin main
```

## Clonar Proyecto Existente
```bash
git clone https://github.com/usuario/proyecto.git
cd proyecto
```

## Workflow Diario

### Ver estado actual
```bash
git status              # Ver cambios pendientes
git branch             # Ver branch actual  
git log --oneline      # Ver historial de commits
git remote -v          # Ver repos remotos configurados
```

### Subir cambios (local → GitHub)
```bash
git add .                    # Agregar todos los cambios
git commit -m "descripcion"  # Crear commit
git push                     # Subir a GitHub
```

### Bajar cambios (GitHub → local)
```bash
git pull    # Bajar y aplicar cambios
git fetch   # Solo bajar, no aplicar
```

### Borrar archivos
```bash
# Si borraste archivos localmente:
git add -A              # Incluye archivos borrados
git commit -m "cleanup: removed old files"
git push
```

## Comandos Útiles

### Ver diferencias
```bash
git diff                # Cambios no commitados
git diff HEAD~1         # Comparar con commit anterior
git diff origin/main    # Comparar con repo remoto
```

### Deshacer cambios
```bash
git checkout -- archivo.txt    # Deshacer cambios en archivo
git reset HEAD archivo.txt     # Quitar archivo del staging
git reset --hard HEAD~1        # Deshacer último commit (PELIGROSO)
```

### Branches (ramas)
```bash
git branch                     # Ver branches locales
git branch nueva-feature       # Crear branch
git checkout nueva-feature     # Cambiar branch
git checkout -b nueva-feature  # Crear y cambiar branch
git checkout main             # Volver a main
git merge nueva-feature       # Mergear branch a main
git branch -d nueva-feature   # Borrar branch local
```

### Historial
```bash
git log                # Historial completo
git log --oneline      # Historial resumido
git show               # Ver último commit
git show HEAD~2        # Ver commit hace 2 versiones
```

## Flujo Típico
1. `git status` - Ver qué cambió
2. `git add .` - Agregar cambios  
3. `git commit -m "mensaje"` - Crear commit
4. `git push` - Subir a GitHub

## Flujo con Branches (trabajo en equipo)
1. `git checkout -b feature-login` - Crear nueva rama
2. Hacer cambios...
3. `git add .` y `git commit -m "add login feature"`
4. `git push -u origin feature-login`
5. Crear Pull Request en GitHub.com
6. `git checkout main` - Volver a main
7. `git pull` - Actualizar main

## Comandos de Emergencia
```bash
# Si algo salió mal:
git status              # Ver qué pasa
git stash              # Guardar cambios temporalmente  
git stash pop          # Recuperar cambios guardados
git checkout .         # Descartar TODOS los cambios
```

## Tips
- **git status:** Úsalo todo el tiempo para saber dónde estás
- **Commits frecuentes:** Mejor muchos commits pequeños que uno grande
- **Mensajes claros:** "fix: login validation bug" vs "cambios"
- **Pull antes de push:** Siempre `git pull` antes de `git push`
- **Branches para features:** Nunca trabajes directo en main en proyectos compartidos