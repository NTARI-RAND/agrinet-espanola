# Lanzamiento, Versionado y Automatización de Etiquetado

Este repositorio automatiza el etiquetado de versiones y lanzamientos de GitHub con dos flujos de trabajo ubicados en `.github/workflows`.

## Flujo de Trabajo de Versión y Etiqueta

**Archivo:** `.github/workflows/version-and-tag.yml`

**Desencadenador:** Empuja al principal que cambia cualquier package.json en:
- `frontend/`
- - `frontend/chat-ui/`
  - - `backend/`
   
    - **Comportamiento:**
    - - Lee la versión canónica de `frontend/package.json`
      - - Valida que siga versionado semántico (x.y.z)
        - - Asegura que las versiones en otros package.json coincidan
          - - Crea una etiqueta anotada si v<version> no existe
            - - Usa la identidad del bot de GitHub Actions
             
              - ## Flujo de Trabajo de Lanzamiento
             
              - **Archivo:** `.github/workflows/create-release.yml`
             
              - **Desencadenador:** Empuje de etiquetas que coincidan con el patrón v*.*.* (ejemplo: v1.2.3)
             
              - **Comportamiento:**
              - - Revisa el repositorio en el commit etiquetado
                - - Publica un lanzamiento de GitHub con `softprops/action-gh-release`
                  - - Nombra el lanzamiento después de la etiqueta
                    - - Genera notas de lanzamiento automáticamente
                     
                      - ## Conjuntos de Reglas de Etiqueta GitHub
                     
                      - Si el repositorio usa conjuntos de reglas de etiqueta para controlar quién puede crear o actualizar etiquetas de lanzamiento, asegúrese de que el conjunto de reglas permita al bot `github-actions` crear etiquetas que comiencen con v.
                     
                      - Los administradores del repositorio pueden administrar estos ajustes en **Settings → Rules → Tag rules**.
                     
                      - ## Mejores Prácticas
                     
                      - ✅ Mantenga las versiones sincronizadas en los tres package.json
                     
                      - ✅ Actualice la versión antes de fusionar a main
                     
                      - ✅ Siga el versionado semántico (MAYOR.MENOR.PARCHE)
                     
                      - Para más información, consulte: https://github.com/NTARI-RAND/Agrinet/blob/main/docs/release-process.md
