# Guía práctica: trabajo colaborativo con GitHub y Visual Studio Code

## 1. Escenario
Tres participantes desarrollan una página web sencilla sobre el curso de Git y GitHub de INATEC. Cada integrante trabaja en una rama y envía sus cambios mediante Pull Request.

| Integrante | Responsabilidad | Rama |
|---|---|---|
| Usuario 1 | Coordinación, repositorio e integración | `main` |
| Usuario 2 | Contenido académico | `feature/contenido` |
| Usuario 3 | Diseño y estilos | `feature/diseno` |

Sustituyan los nombres de ejemplo por los nombres reales. Los tres deben realizar commits y participar en revisiones.

## 2. Preparar cada computadora
1. Instalar Git y Visual Studio Code.
2. Instalar extensiones Dart no son necesarias; para esta práctica recomendamos Live Server y GitHub Pull Requests.
3. Crear una cuenta GitHub.
4. Configurar la identidad Git:

```bash
git config --global user.name "Nombre Apellido"
git config --global user.email "correo-verificado@example.com"
git config --global init.defaultBranch main
```

Utiliza el correo asociado a GitHub o su correo privado noreply. No dejes el correo de ejemplo literalmente.

## 3. Crear repositorio remoto (Usuario 1)
1. Iniciar sesión en GitHub y seleccionar **New repository**.
2. Nombre: `proyecto-colaborativo-inatec`.
3. Descripción: `Práctica colaborativa del curso Git y GitHub - INATEC`.
4. Elegir Public o Private según indique el docente.
5. Como ya tienes archivos locales, no inicialices con README ni .gitignore.
6. Crear repositorio.
7. Ir a Settings > Collaborators / Manage access e invitar a Usuario 2 y Usuario 3. Ambos aceptan la invitación.

## 4. Primer envío del proyecto (Usuario 1)
Descomprime el ZIP y abre en VS Code la carpeta `proyecto_colaborativo_inatec`. En Terminal > New Terminal ejecuta:

```bash
git init
git add .
git commit -m "chore: crear estructura inicial del sitio INATEC"
git branch -M main
git remote add origin https://github.com/USUARIO_GITHUB/proyecto-colaborativo-inatec.git
git push -u origin main
```

Reemplaza `USUARIO_GITHUB` por el usuario real y copia la URL HTTPS desde el botón Code del repositorio.

## 5. Clonar (Usuarios 2 y 3)
Cada colaborador clona el mismo repositorio en su computadora:

```bash
git clone https://github.com/USUARIO_GITHUB/proyecto-colaborativo-inatec.git
cd proyecto-colaborativo-inatec
code .
```

Si `code .` no funciona, abre VS Code y utiliza File > Open Folder.

## 6. Flujo de trabajo de cada colaborador
Antes de iniciar una tarea:

```bash
git switch main
git pull origin main
```

Crear la rama correspondiente:

```bash
git switch -c feature/contenido
```

Usuario 2 usa `feature/contenido`; Usuario 3 usa `feature/diseno`.

Revisar los cambios:

```bash
git status
git diff
```

Guardar y publicar cambios. Ejemplo Usuario 2:

```bash
git add index.html
git commit -m "feat: ampliar contenido del curso"
git push -u origin feature/contenido
```

Ejemplo Usuario 3:

```bash
git add css/styles.css
git commit -m "style: mejorar diseño adaptable"
git push -u origin feature/diseno
```

## 7. Crear y revisar Pull Request
1. Abrir el repositorio en GitHub.
2. Seleccionar Compare & pull request.
3. Base: `main`; compare: la rama de trabajo.
4. Explicar qué se cambió, por qué y cómo se probó.
5. Solicitar revisión a otro integrante.
6. El revisor examina Files changed y deja comentarios.
7. El autor corrige en su misma rama y vuelve a ejecutar `git push`.
8. Cuando esté aprobado, integrar con Merge pull request.

No aprobar cambios sin revisarlos y probarlos.

## 8. Sincronizar después de integrar
Todos actualizan su rama principal:

```bash
git switch main
git pull origin main
```

Después de integrar una rama, puede eliminarse localmente:

```bash
git branch -d feature/contenido
git fetch --prune
```

## 9. Resolver un conflicto
Un conflicto ocurre cuando dos ramas modifican las mismas líneas y Git no puede decidir automáticamente.

```bash
git switch main
git pull origin main
git switch feature/contenido
git merge main
```

Si aparece conflicto:
1. Abrir el archivo señalado en VS Code.
2. Revisar los bloques marcados `<<<<<<<`, `=======` y `>>>>>>>`.
3. Elegir o combinar manualmente el contenido correcto.
4. Eliminar todos los marcadores y guardar.
5. Marcar resuelto y confirmar:

```bash
git add index.html
git commit -m "fix: resolver conflicto con main"
git push
```

Luego revisar el Pull Request.

## 10. Reglas del equipo
- No compartir contraseñas ni tokens.
- No trabajar directamente en `main`.
- Crear una rama por tarea.
- Hacer commits pequeños y descriptivos.
- Probar la página en navegador antes de abrir PR.
- Revisar el trabajo de otro compañero.
- Conversar antes de sobrescribir cambios.
- Sincronizar `main` antes de iniciar otra tarea.

## 11. Evidencias de aprendizaje
1. Repositorio GitHub y rama main.
2. Tres integrantes con acceso.
3. Dos ramas de características.
4. Dos Pull Requests revisados.
5. Commits de los tres participantes.
6. Página final en navegador.
7. Capturas de ramas, historial, PR y revisión.
8. Reflexión individual sobre lo aprendido.
