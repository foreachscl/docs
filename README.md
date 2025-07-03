# Lineamientos
# Ramas Git y Flujo Gitflow
## Ramas principales y su uso:

`main`:
 Rama principal, siempre estable y lista para producción. Solo se integran aquí cambios probados y aprobados.
 
`develop`:
 Rama de integración para desarrollo y QA. Aquí se juntan todas las funcionalidades y correcciones antes de pasar a producción (main).
 
`feature/`:
 Ramas para desarrollar nuevas funcionalidades. Se crean desde develop y, al estar listas y testeadas localmente, se mergean de vuelta a develop.
 
`bugfix/`:
 Ramas para corregir bugs detectados durante pruebas o QA. Parten de develop y se fusionan de vuelta a develop una vez corregidos.
 
`hotfix/`:
 Correcciones urgentes para arreglos directos a producción (main). Se crean desde main, y al finalizar se fusionan tanto en main como en develop para mantener sincronización.
 
`release/`:
 Ramas para preparar versiones estables antes de fusionar a main. Aquí se hacen ajustes finales y pruebas de QA.

## Flujo general de Gitflow:

- La rama develop se crea partiendo de main.
- Desde develop se crean ramas release para preparar nuevas versiones.
- También desde develop se crean ramas feature para funcionalidades.
- Cuando una feature está lista, se fusiona de nuevo a develop.
- Al estar lista la release, se fusiona a develop y main.
- Si se detecta un problema en main, se crea una rama hotfix desde main para corregirlo rápido.
- Finalizada la hotfix, se fusiona en ambas ramas: develop y main.
