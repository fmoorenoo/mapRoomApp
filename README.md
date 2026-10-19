<div align="center">

# Map Room App

### Explorador de puntos de interés con mapas interactivos y favoritos locales

**Proyecto Android · Mapas · Persistencia con Room**

![Kotlin](https://img.shields.io/badge/Kotlin-1A1B26?style=for-the-badge&logo=kotlin&logoColor=E46B79)
![Jetpack Compose](https://img.shields.io/badge/Jetpack_Compose-1A1B26?style=for-the-badge&logo=jetpackcompose&logoColor=E46B79)
![Room](https://img.shields.io/badge/Room-1A1B26?style=for-the-badge&logo=android&logoColor=E46B79)
![osmdroid](https://img.shields.io/badge/osmdroid-1A1B26?style=for-the-badge&logo=openstreetmap&logoColor=E46B79)

[![Estado](https://img.shields.io/badge/ESTADO-Proyecto_académico-712B39?style=flat-square)](#estado-del-proyecto)
[![Plataforma](https://img.shields.io/badge/PLATAFORMA-Android-22252C?style=flat-square)](#tecnologías)
[![Código](https://img.shields.io/badge/REPOSITORIO-Código_fuente-22252C?style=flat-square)](https://github.com/fmoorenoo/mapRoomApp)

</div>

---

## Sobre el proyecto

**Map Room App** es una aplicación Android que representa **puntos de interés geográficos** en un mapa interactivo. Cada marcador dispone de coordenadas, nombre, categoría y descripción, y puede añadirse a una lista de favoritos.

El proyecto combina **Kotlin y Jetpack Compose** para la interfaz, bibliotecas de mapas basadas en **osmdroid** y **Room** para la persistencia local. Un **ViewModel** conecta los datos de la base de datos con la representación cartográfica.

## Funcionalidades

- **Mapa interactivo:** visualización y exploración de ubicaciones mediante controles de zoom y gestos.
- **Marcadores categorizados:** iconos distintos para monumentos, restauración, centros educativos, comercios, centros sanitarios y ocio.
- **Información contextual:** selección de marcadores para mostrar su título, tipo y detalles.
- **Favoritos:** marcar y desmarcar lugares guardados en la base de datos local.
- **Gestión de estado:** consulta de marcadores, categorías y favoritos mediante `StateFlow` y `ViewModel`.
- **Datos persistentes:** entidades relacionadas de Room para marcadores, tipos y favoritos.

> Las funcionalidades se han contrastado con el código fuente. No se ha ejecutado una prueba integral en un dispositivo durante esta revisión.

## Tecnologías

| Área | Tecnologías |
| --- | --- |
| **Lenguaje** | Kotlin |
| **Plataforma** | Android (minSdk 35 · targetSdk 35) |
| **Interfaz** | Jetpack Compose · Material 3 |
| **Mapas** | osmdroid · osmdroid/Compose |
| **Persistencia** | Room · SQLite · DAOs |
| **Arquitectura y estado** | Android ViewModel · Kotlin StateFlow |
| **Procesamiento de anotaciones** | KSP |
| **Asincronía** | Kotlin Coroutines |
| **Compilación** | Gradle Kotlin DSL |

## Arquitectura

```text
mapRoomApp/
├── app/src/main/
│   ├── java/org/iesharia/maproomapp/
│   │   ├── MainActivity.kt        # Punto de entrada Android
│   │   ├── model/
│   │   │   ├── MapDatabase.kt     # Base de datos Room
│   │   │   ├── dao/               # Acceso a marcadores, tipos y favoritos
│   │   │   └── entities/          # Modelos persistentes
│   │   ├── view/
│   │   │   └── MainApp.kt         # Mapa interactivo y marcadores
│   │   └── viewmodel/
│   │       └── MapViewModel.kt    # Estado y operaciones de favoritos
│   └── res/drawable/             # Iconos por categoría
├── app/build.gradle.kts
└── settings.gradle.kts
```

El **ViewModel** obtiene las ubicaciones y categorías desde los DAOs, expone sus datos mediante flujos observables y gestiona el cambio de estado de los favoritos. La interfaz Compose utiliza ese estado para representar los marcadores.

## Modelo de datos

| Entidad | Propósito |
| --- | --- |
| **Marker** | Información y coordenadas de cada punto de interés |
| **MarkerType** | Clasificación de los marcadores |
| **Favorite** | Asociación con los marcadores guardados como favoritos |

La documentación original del ejercicio planteaba una colección inicial de al menos doce marcadores distribuidos en varias categorías. Esa cifra se presenta como **requisito original**, no como cantidad de registros verificada en una ejecución.

## Diseño y capturas

El repositorio incluye recursos gráficos para los iconos de los marcadores, pero no se han localizado capturas verificadas de la aplicación ejecutándose. Este apartado podrá ampliarse con imágenes reales del mapa y del panel de detalles.

## Instalación y ejecución

1. Clona el repositorio:

   ```bash
   git clone https://github.com/fmoorenoo/mapRoomApp.git
   cd mapRoomApp
   ```

2. Abre el proyecto en **Android Studio**.
3. Configura el SDK de Android y sincroniza Gradle.
4. Ejecuta el módulo `app` en un emulador o dispositivo compatible con **API 35 o superior**.
5. Utiliza una conexión a Internet para cargar las imágenes del mapa.

No se ha verificado la compilación ni la disponibilidad del proveedor de teselas en esta revisión.

## Estado del proyecto

**Proyecto académico / demostración de mapas y persistencia local.**

Aspectos a tener en cuenta antes de reutilizar la aplicación en producción:

- **Migraciones de datos:** `MapDatabase.kt` configura `fallbackToDestructiveMigration()`, que puede provocar pérdida de datos al cambiar el esquema sin migraciones definidas.
- **Teselas cartográficas:** `MainApp.kt` define una fuente satelital mediante servidores externos de Google; su disponibilidad y condiciones de uso deben revisarse antes de distribuir la aplicación.
- **Compatibilidad:** la configuración actual exige **Android API 35** como versión mínima.
- **Centro inicial:** el mapa parte de unas coordenadas predeterminadas situadas en París; no implica geolocalización automática del usuario.

## Autor

**Fernando Montelongo Moreno** · Full Stack Developer · DAM + DAW

[![GitHub](https://img.shields.io/badge/GitHub-fmoorenoo-22252C?style=flat-square&logo=github)](https://github.com/fmoorenoo)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Perfil_profesional-712B39?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/fernando-montelongo/)

---

<div align="center">
  <sub>Map Room App · Cartografía interactiva y favoritos con Kotlin, Compose y Room</sub>
</div>
