# **6 Como escribir buenos commits**

Los commits del proyecto son claves ya que nos describen que cambios se han hecho a grandez razgos, es por ello que es útil conocer ciertas técnicas que permiten escribir buenos commits que sean significativos.

## Usar verbos imperativos

Los verbos imperativos describen muy bien una acción de manera concreta. Ejemplos son:
* Add
* Fix
* Resolve
* Change
* Remove

## No usar signos de puntuación de manera excesiva

Colocar puntos finales, suspensivos, punto y coma, o paréntesis son signos omitibles que no afectan al entenimiento del commit.

## Usar 50 caracteres como máximo

Utilizar más de 50 caracteres para el título de un commit es innesesario. Si se han cambiado múltiples partes del programa es más recomendable realizar un commit para cada funcionalidad en vez de un solo commit describiendo todas las funcionalidades agregadas.

## Utilizar una estructura predefinida

Es recomendable utilizar una estructura: `<tipo-de-commit>[scope]: <descripcion>`

Con prefijos como estos:
* **feat:** Una nueva característica para el usuario.
* **fix:** Arregla un bug que afecta al usuario.
* **perf:** Cambios que mejoran el rendimiento del sitio.
* **build:** Cambios en el sistema de build, tareas de despliegue o instalación.
* **ci:** Cambios en la integración continua.
* **docs:** Cambios en la documentación.
* **refactor:** Refactorización del código como cambios de nombre de variables o funciones.
* **style:** Cambios de formato, tabulaciones, espacios o puntos y coma, etc; no afectan al usuario.
* **test:** Añade tests o refactoriza uno existente.

