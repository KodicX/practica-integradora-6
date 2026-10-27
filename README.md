# Reto Final Integrador: El Muro del Congreso Proxy

El sitio del congreso sale a produccion en 35 minutos y las 3 ramas de desarrollo tienen problemas graves.

## Instrucciones de Arranque para el Equipo (3 personas)
1. **Un representante del equipo** hace **Fork** de este repositorio en GitHub.
   - **MUY IMPORTANTE:** Al hacer el Fork, **DESMARCA** la casilla *"Copy the main branch only"* para que se copien las 3 ramas del reto.
2. El representante va a **Settings -> Collaborators** en su Fork y agrega a sus 2 companeros.
3. Los 3 clonan el Fork del representante por SSH y ejecutan `git fetch --all`.

---

## Misiones Individuales (Cada integrante toma una rama)

### Integrante A -> Rama `feature/ponentes` (Limpieza con Rebase)
1. Cambiate a `feature/ponentes` y revisa el historial (`git log --oneline`).
2. Hay commits basura ("wip", "asdf", "ya quedo") y alguien subio `claves_servidor.txt` con contrasenas.
3. Elimina `claves_servidor.txt` y usa `git rebase -i main` para compactar todo en UN SOLO commit limpio con buen mensaje.
4. En `index.html`, cambia la linea 2 a `<p>Estado del sitio: PONENCIAS CONFIRMADAS</p>`.
5. Sube tu rama (`git push --force-with-lease`) y abre un Pull Request hacia la rama `main` de tu equipo.

### Integrante B -> Rama `feature/agenda` (Revertir error sin borrar historia)
1. Cambiate a `feature/agenda` y revisa el historial (`git log --oneline`) y el archivo `agenda.html`.
2. Alguien hizo un commit llamado `"Borra horarios matutinos por error"` que vacio la agenda, pero encima ya hay otro commit bueno (`"Agrega sede del evento"`).
3. Usa `git revert <hash>` para deshacer UNICAMENTE el commit que borro los horarios, conservando la sede.
4. En `index.html`, cambia la linea 2 a `<p>Estado del sitio: AGENDA PUBLICADA</p>` y cambia `Agenda: Pendiente` por `Agenda: Lista`.
5. Sube tu rama y abre un Pull Request hacia la rama `main` de tu equipo.

### Integrante C -> Rama `feature/registro` (.gitignore y Amend)
1. Cambiate a `feature/registro` y revisa los archivos (`ls` y `git log -1`).
2. Subieron archivos basura (`debug.log` y `temp.cache`) y el ultimo commit tiene una falta de ortografia: `"Agrega rejistro"`.
3. Crea un archivo `.gitignore` para ignorar `*.log` y `*.cache`, sacalos del repositorio con `git rm --cached debug.log temp.cache`.
4. En `index.html`, cambia la linea 2 a `<p>Estado del sitio: REGISTRO ABIERTO</p>` y cambia `Registro: Pendiente` por `Registro: Activo`.
5. Corrige el ultimo commit usando `git commit --amend` con un mensaje limpio, sube con `git push --force-with-lease` y abre tu Pull Request hacia `main` de tu equipo.

---

## Fase Final en Equipo: Revision, Conflictos y Entrega
1. Revisen los 3 Pull Requests en el Fork de su equipo (dejen al menos 1 comentario y den Approve).
2. Al hacer Merge del primer PR, los otros dos tendran **Conflicto en `index.html`**.
3. Resuelvan los conflictos en local (`git pull origin main`, `git merge main`, editar en VS Code, commit y push) hasta que los 3 PRs esten fusionados en la rama `main` de su equipo.
4. **Entrega final:** Desde su Fork, abran un **Pull Request final hacia el repositorio original de los instructores** con el nombre de su equipo.
