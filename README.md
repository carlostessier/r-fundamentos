# Curso de R — Fundamentos para Análisis de Datos e IA

Este repositorio contiene los **materiales y actividades prácticas** del curso de **R**, orientado a sentar las bases necesarias para trabajar en:

- Análisis Exploratorio de Datos (EDA)
- Estadística aplicada
- Machine Learning clásico
- Flujos de trabajo reales en ciencia de datos

El objetivo principal **no es memorizar sintaxis**, sino **aprender a pensar con datos usando R**.

---

## 🎯 Objetivo del repositorio

Este repositorio tiene dos finalidades claras:

1. **Aprender R desde cero**, entendiendo:
   - variables y tipos de datos
   - operaciones básicas
   - lógica y control de flujo
   - funciones fundamentales
2. **Familiarizarse con un flujo de trabajo profesional**, usando:
   - Jupyter Notebooks
   - Git
   - Pull Requests (PRs)

Las actividades se evaluarán como **Apto / No Apto**.

---

## 📁 Estructura del repositorio

```

.
├─ actividades/        # Notebooks y enunciados oficiales (solo el profesor)
│  └─ Notebook_01.ipynb
│  └─ Notebook_02.ipynb
   └─ ...
│     
│
├─ entregas/           # Entregas de los alumnos (una carpeta por alumno)
│  └─ <apellidos_nombre>/
│     └─ Notebook_01.ipynb
│
└─ README.md

```

⚠️ **Importante**  
- La carpeta `actividades/` **no debe modificarse**
- Cada alumno trabaja **únicamente dentro de su carpeta** en `entregas/`

---

## 🧑‍💻 Cómo trabajar los notebooks

Para cada actividad:

1. Abre el notebook correspondiente en `actividades/`
2. **Copia** el notebook a tu carpeta personal:
```

entregas/<apellidos_nombre>/Notebook_0X.ipynb

```
3. Resuelve los ejercicios directamente en tu copia
4. Ejecuta todas las celdas para comprobar que funciona
5. Antes de entregar:
- Reinicia el kernel
- Limpia los outputs (`Restart & Clear Outputs`)

---

## 🆘 Solución de Problemas: VS Code se queda cargando

Si al intentar abrir el proyecto en un **Dev Container**, Visual Studio Code se queda "atascado" en la pantalla de *Starting Dev Container...* o *Building image...* durante mucho tiempo, sigue estos pasos para construir la imagen manualmente desde la terminal:

1. Abre una terminal (PowerShell, CMD o Bash) en la **carpeta raíz** del proyecto.
2. Ejecuta el siguiente comando para construir la imagen usando el Dockerfile de la carpeta `.devcontainer`:

```bash
docker build -t r-curso -f .devcontainer/Dockerfile .

```

> **Nota:** Asegúrate de incluir el punto `.` al final del comando.

3. Una vez que el proceso termine con éxito (`SUCCESS`), vuelve a Visual Studio Code.
4. Presiona `F1` (o `Ctrl` + `Shift` + `P`) y selecciona:
**Dev Containers: Rebuild and Reopen in Container**.

Al haber construido la imagen manualmente, VS Code la detectará inmediatamente y arrancará sin esperas.

---

## ⚙️ Configuración Inicial (Solo la primera vez)

Antes de empezar el curso, debes preparar tu entorno en GitHub y en tu ordenador.

### 1. Hacer un Fork del repositorio

Ve a la esquina superior derecha de esta página y haz clic en el botón **Fork**.

* Esto creará una **copia exacta** de este repositorio en **tu cuenta de GitHub**.

### 2. Clonar TU repositorio (el Fork)

En tu ordenador, clona la copia que acabas de crear (no la del profesor):

```bash
# ⚠️ Sustituye <TU_USUARIO> por tu nombre de usuario de GitHub
git clone https://github.com/<TU_USUARIO>/r-fundamentos.git

cd r-fundamentos

```

### 3. Crear tu carpeta de entregas

Crea una carpeta con tus apellidos y nombre dentro de `entregas/`:

```bash
# Ejemplo: mkdir entregas/perez_juan
mkdir entregas/<apellidos_nombre>

```

---

## 🔄 Flujo de trabajo para cada Actividad

Cada vez que tengas que realizar una nueva práctica (ej. Notebook 02, 03...), sigue estos pasos ordenados:

### Paso 1: Sincronizar tu Fork (Obtener nuevos enunciados)

El profesor subirá nuevos notebooks a la carpeta `actividades/`. Para tenerlos en tu repositorio:

1. Ve a la página de **tu repositorio (Fork)** en GitHub.
2. Haz clic en el botón **Sync Fork** (debajo del botón verde de "Code").
3. Dale a **Update branch**.
4. En tu terminal local, descarga esos cambios:
```bash
git pull origin main

```



### Paso 2: Trabajar en la actividad

1. Copia el fichero de `actividades/Notebook_XX.ipynb` a tu carpeta `entregas/<apellidos_nombre>/`.
2. Resuelve los ejercicios en tu copia.
3. **Comprobación:** Antes de guardar, reinicia el kernel y limpia las salidas (*Restart & Clear Outputs*).

### Paso 3: Subir los cambios a tu nube (Push)

```bash
# 1. Añade los cambios
git add entregas/<apellidos_nombre>/

# 2. Guarda el cambio con un mensaje claro
git commit -m "Entrega Notebook XX - Apellidos Nombre"

# 3. Sube los cambios a TU repositorio en GitHub
git push origin main

```

### Paso 4: Entregar al profesor (Pull Request)

Una vez tus cambios están en tu GitHub:

1. Ve a la pestaña **Pull Requests** en tu repositorio.
2. Haz clic en **New Pull Request**.
3. Verás una comparación. Asegúrate de que la flecha apunta así:
* `base repository: carlostessier/r-fundamentos` ⬅️ `head repository: <tu_usuario>/r-fundamentos`


4. Haz clic en **Create Pull Request**.
5. En el título pon: `Entrega Notebook XX - <Tus Apellidos Nombre>`.

---


# 🎯 Buenas prácticas

* No subir datasets muy pesados si no es necesario.
* Comprobar que el notebook ejecuta sin errores antes del commit.
* No modificar archivos de otros compañeros.
* No trabajar nunca directamente sobre `main`.

---

Si quieres, puedo prepararte una versión lista para copiar y pegar en el README del repositorio para los alumnos.


### Reglas de entrega

- ✅ Una carpeta por alumno: `entregas/<usuario_github>/`
- ✅ Un notebook por actividad
- ❌ No modificar archivos fuera de tu carpeta
- ❌ No borrar ni modificar entregas de otros compañeros

Si un Pull Request modifica archivos fuera de tu carpeta, **no se considerará válido**.

---

## ✅ Evaluación

Cada actividad se calificará como:

- **Apto**: la actividad está completa y correctamente resuelta
- **No Apto**: faltan partes, hay errores importantes o no se siguen las normas

---

## 💡 Recomendaciones finales

- Lee los mensajes de error: R explica bastante bien qué falla
- No tengas miedo a equivocarte: cometer errores es parte del aprendizaje
- Prioriza **entender lo que haces**, no solo que “funcione”

---

Si tienes dudas técnicas (Git, Jupyter, R), consúltalas **antes de entregar**.
```

---
