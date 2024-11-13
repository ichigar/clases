## Escenario: Dos usuarios colaboran en un repositorio GitHub
- **Repositorio GitHub compartido:** `https://github.com/usuario/proyecto-compartido`
- **Usuarios:** Usuario1 (crea el repositorio) y Usuario2 (Usuario1 lo añade como colaborador)

---

### Paso 1: Clonar el repositorio

**Usuario1** y **Usuario2** clonan el repositorio desde GitHub usando VS Code y lo abren:

### Paso 2: Crear una nueva rama para hacer cambios

* **Usuario1** crea una nueva rama llamada `feature/usuario1` para trabajar en una nueva funcionalidad:

   ```bash
   git checkout -b feature/usuario1
   ```

**Nota:** una **rama** es una versión independiente del proyecto donde los desarrolladores pueden trabajar en nuevas funcionalidades sin afectar el código principal.

* **Usuario2** también crea una nueva rama llamada `feature/usuario2` para sus propios cambios:

   ```bash
   git checkout -b feature/usuario2
   ```

### Paso 3: Hacer cambios en el código

* **Usuario1** Crea el fichero `archivo1.html` le añade contenido y luego guarda los cambios.
* Añade y confirma sus cambios:

   ```bash
   git add archivo1.html
   git commit -m "Añadir nueva funcionalidad por Usuario1"
   ```

**Nota:** El comando **git add** añade los cambios al área de preparación, y **git commit** guarda esos cambios con un mensaje descriptivo.

* Envía la rama al repositorio remoto:
  
  ```bash
  git push origin feature/usuario1
  ```
**Nota:** **Push** envía los cambios locales al repositorio en GitHub para que otros puedan verlos y trabajar con ellos.

* **Usuario2** Crea `archivo1.html` le añade contenido y guarda los cambios.
* Añade y confirma sus cambios:
  ```bash
  git add archivo1.html
  git commit -m "Actualizar archivo2 por Usuario2"
  ```
* Envía la rama al repositorio remoto:
  ```bash
  git push origin feature-usuario2
   ```

### Paso 4: Pull Requests en GitHub

* Desde la web del repositorio **Usuario1** abre un **Pull Request (PR)** para fusionar los cambios de `feature/usuario1` a `main`:
   - Va al repositorio en GitHub y selecciona la rama `feature/usuario1`.
   - Abre un Pull Request con el título: "Añadir nueva funcionalidad por Usuario1".
   - Hace merge de la rama con main.
   - En la web nos aparece la opción de eliminar la rama. Cómo no la necesitamos más la podemos eliminar.

**Nota:** Un **Pull Request** es una solicitud para que otros revisen los cambios hechos en una rama antes de fusionarlos con la rama principal (`main`).

* **Usuario2** hace lo mismo con su rama `feature/usuario2`:
   - Abre otro Pull Request con el título: "Actualizar archivo1 por Usuario2".

### Paso 5: Revisar y resolver conflictos

* **Usuario1** fusiona su Pull Request después de que **Usuario2** lo revisa y aprueba. Los cambios de `feature-usuario1` ahora están en `main`.

**Nota**: **Fusionar** significa combinar los cambios de una rama con otra.

* **Usuario2** intenta fusionar su Pull Request, pero se encuentra con un **conflicto** porque el archivo `archivo1.html` también fue actualizado por **Usuario1**.

**Nota**: Un **conflicto** ocurre cuando dos ramas tienen cambios contradictorios en las mismas líneas de un archivo.

* **Usuario2** sincroniza su rama con la rama `main` que ya tiene los cambios de **Usuario1**:
     ```bash
     git checkout main
     git pull origin main
     git checkout feature/usuario2
     git merge main
     ```
**Nota:** **Pull** trae los cambios más recientes del repositorio remoto a la rama local para mantenerla actualizada. Y **git merge main** intenta combinar los cambios de la rama main en la rama actual.

* VSCode muestra los **conflictos** en `archivo1.html`. **Usuario2** los resuelve editando el archivo.
* Después de resolver los conflictos, confirma los cambios:
  
  ```bash
  git add archivo1.html
  git commit -m "Resolver conflictos entre feature-usuario2 y main"
  ```
* Envía la rama actualizada:
  ```bash
  git push origin feature-usuario2
  ```

### Paso 6: Fusionar la rama de Usuario2

* Desde la web del repositorio en GitHub **Usuario2** fusiona el Pull Request una vez que todos los conflictos se resuelven y el equipo lo aprueba. Ahora los cambios de ambas ramas están en `main`.
* En la web nos aparece la opción de eliminar la rama. Cómo no la necesitamos más la podemos eliminar.

### Paso 7: Actualizar las copias locales

* **Usuario1** y **Usuario2** actualizan sus copias locales para reflejar los cambios más recientes:
  ```bash
  git checkout main
  git pull origin main
  ```
Esto asegura que ambos usuarios tengan la versión más actualizada del proyecto después de las fusiones.

### Paso 8: Eliminar ramas locales

Cómo los usuarios no necesitan las ramas las pueden eliminar ejecutando.

* Usuario1:
```bash
git branch -d feature/usuario1
```
* Usuario2:
```bash
git branch -d feature/usuario2
```
### **Resumen**
- **Usuario1** y **Usuario2** clonaron el repositorio y crearon ramas separadas para trabajar en sus respectivas funcionalidades.
- Ambos usuarios abrieron Pull Requests para fusionar sus cambios en `main`.
- **Usuario2** resolvió conflictos antes de poder fusionar su rama.
- Finalmente, ambos usuarios actualizaron sus copias locales para tener los últimos cambios.

Esta simulación muestra un flujo básico de trabajo colaborativo en GitHub utilizando VS Code, permitiendo a los usuarios trabajar de forma organizada y evitar sobrescribir el trabajo del otro.

## Anexo. Nombres de ramas en grupos de trabajo



| **Tipo de Rama**             | **Convención de Nombres**           | **Descripción**                                                                                                                                                     | **Ejemplos**                    |
|-----------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|
| **Rama Principal**          | `main` o `master`                   | Rama principal y estable del proyecto; generalmente contiene código listo para producción.                                                                         | `main`, `master`                |
| **Rama de Desarrollo**      | `develop`                           | Rama para la integración de nuevas características antes de fusionarlas en `main`.                                                                                 | `develop`                       |
| **Rama de Características** | `feature/nombre-de-la-caracteristica` | Utilizada para desarrollar nuevas funcionalidades.                                                                                                                 | `feature/login-page`, `feature/user-profile` |
| **Rama de Corrección**      | `bugfix/nombre-del-bug`             | Usada para corregir errores menores o problemas específicos.                                                                                                        | `bugfix/fix-login-bug`, `bugfix/ui-alignment` |
| **Rama de Soporte**         | `hotfix/nombre-del-hotfix`          | Para aplicar correcciones urgentes y críticas en `main` o `master`.                                                                                                 | `hotfix/security-patch`, `hotfix/critical-bug` |
| **Rama de Pruebas**         | `release/nombre-de-la-version`      | Preparación de nuevas versiones; pruebas finales antes de fusionar en `main`.                                                                                       | `release/v1.0.0`, `release/2.1.5` |
| **Rama Experimental**       | `experiment/nombre-del-experimento` | Para pruebas rápidas o ideas no listas para producción.                                                                                                            | `experiment/new-idea`, `experiment/test-feature` |
| **Rama de Documentación**   | `docs/nombre-del-documento`         | Para actualizaciones o mejoras en la documentación del proyecto.                                                                                                   | `docs/api-update`, `docs/readme-enhancement` |




