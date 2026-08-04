# 🔄 Guía de Sincronización con GitHub - Editor Carnicería

## ¿Qué es?

El Editor Carnicería ahora permite sincronizar los cambios de productos **directamente en GitHub**, en el archivo `carniceria-productos.json`. Los cambios se guardan automáticamente en el repositorio, permitiendo:

- ✅ Persistencia permanente de datos
- - ✅ Historial de cambios (commits)
  - - ✅ Control de versiones
    - - ✅ Acceso desde cualquier dispositivo
     
      - ---

      ## 🚀 Cómo Usar

      ### Paso 1: Obtener tu Token de GitHub

      1. Ve a https://github.com/settings/tokens
      2. 2. Haz clic en **"Generate new token"** → **"Generate new token (classic)"**
         3. 3. Dale un nombre descriptivo, ej: "carniceria-sync"
            4. 4. Selecciona los permisos:
               5.    - ✅ `repo` (acceso completo a repositorios)
                     -    - ✅ `workflow` (si lo necesitas)
                          - 5. Haz clic en **"Generate token"**
                            6. 6. **IMPORTANTE:** Copia el token inmediatamente (no podrás verlo después)
                              
                               7. ### Paso 2: Configurar el Token en el Editor
                              
                               8. 1. Abre el Editor Carnicería (`editor-carniceria.html`)
                                  2. 2. Abre la **Consola del Navegador** (F12 o Ctrl+Shift+I)
                                     3. 3. En la pestaña "Console", escribe:
                                       
                                        4. ```javascript
                                           setGitHubToken("tu_token_aqui")
                                           ```

                                           Ejemplo:
                                           ```javascript
                                           setGitHubToken("ghp_a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6")
                                           ```

                                           4. Presiona Enter
                                           5. 5. Deberías ver un mensaje: **"Token de GitHub guardado. Ya puedes sincronizar cambios."**
                                             
                                              6. ### Paso 3: Sincronizar Cambios
                                             
                                              7. #### Opción A: Automático (Recomendado)
                                              8. - Edita los productos como normalmente
                                                 - - Se guardan en **LocalStorage** automáticamente
                                                   - - Haz clic en el botón **☁ Sincronizar con GitHub**
                                                     - - Los cambios se envían al repositorio
                                                      
                                                       - #### Opción B: Manual
                                                       - 1. Descarga el JSON con el botón **"Descargar JSON"**
                                                         2. 2. Edita el archivo localmente
                                                            3. 3. Usa **"Importar JSON"** para cargar los cambios
                                                               4. 4. Haz clic en **☁ Sincronizar con GitHub**
                                                                 
                                                                  5. ---
                                                                 
                                                                  6. ## 📋 Flujo de Datos
                                                                 
                                                                  7. ```
                                                                     ┌─────────────┐
                                                                     │  Editor UI  │
                                                                     └──────┬──────┘
                                                                            │ Editar/Agregar/Eliminar productos
                                                                            ▼
                                                                     ┌─────────────────────┐
                                                                     │   LocalStorage      │  ← Cambios guardados automáticamente
                                                                     └──────┬──────────────┘
                                                                            │ Clic: "Sincronizar con GitHub"
                                                                            ▼
                                                                     ┌─────────────────────┐
                                                                     │  GitHub API         │  ← Envía cambios al repositorio
                                                                     └──────┬──────────────┘
                                                                            │
                                                                            ▼
                                                                     ┌─────────────────────┐
                                                                     │ carniceria-         │  ← Archivo actualizado en GitHub
                                                                     │ productos.json      │
                                                                     └─────────────────────┘
                                                                     ```

                                                                     ---

                                                                     ## 🔐 Seguridad

                                                                     - El token se guarda **localmente en tu navegador** (localStorage)
                                                                     - - **NO se envía a servidores externos**
                                                                       - - El token es **personal y secreto** - nunca lo compartas
                                                                         - - Si lo comprometes, ve a GitHub y regenera un nuevo token
                                                                          
                                                                           - ### Buenas Prácticas
                                                                          
                                                                           - 1. Usa un token con permisos **limitados** (solo `repo`)
                                                                             2. 2. Regenera el token periódicamente
                                                                                3. 3. Usa diferentes tokens para diferentes aplicaciones
                                                                                   4. 4. No guardes tokens en código fuente
                                                                                     
                                                                                      5. ---
                                                                                     
                                                                                      6. ## 🐛 Solución de Problemas
                                                                                     
                                                                                      7. ### "Error: Necesitas configurar un token"
                                                                                      8. - Abre la consola del navegador
                                                                                         - - Ejecuta: `setGitHubToken("tu_token")`
                                                                                           - - Verifica que el token sea válido
                                                                                            
                                                                                             - ### "Error al guardar en GitHub: 401 Unauthorized"
                                                                                             - - Tu token ha expirado o es inválido
                                                                                               - - Genera un nuevo token en GitHub
                                                                                                 - - Actualiza el token en la consola
                                                                                                  
                                                                                                   - ### "Error: 404 Not Found"
                                                                                                   - - El archivo `carniceria-productos.json` no existe
                                                                                                     - - Crea el archivo primero en el repositorio
                                                                                                       - - O usa "Descargar JSON" y luego "Importar JSON"
                                                                                                        
                                                                                                         - ### Los cambios no aparecen en GitHub
                                                                                                         - - Verifica que hayas hecho clic en "☁ Sincronizar con GitHub"
                                                                                                           - - Recarga la página de GitHub para ver los cambios más recientes
                                                                                                             - - Revisa la pestaña "Commits" para confirmar
                                                                                                              
                                                                                                               - ---
                                                                                                               
                                                                                                               ## 📝 Información Técnica
                                                                                                               
                                                                                                               ### Variables Configurables
                                                                                                               
                                                                                                               ```javascript
                                                                                                               const GITHUB_TOKEN_KEY = 'github_token_carniceria';
                                                                                                               const GITHUB_REPO = 'josemarcosservia-cmyk/Cash-Record-Virtual';
                                                                                                               const GITHUB_FILE = 'carniceria-productos.json';
                                                                                                               ```
                                                                                                               
                                                                                                               ### Funciones Disponibles
                                                                                                               
                                                                                                               ```javascript
                                                                                                               // Guardar el token
                                                                                                               setGitHubToken(token)

                                                                                                               // Obtener el token
                                                                                                               getGitHubToken()

                                                                                                               // Sincronizar cambios con GitHub
                                                                                                               guardarEnGitHub()
                                                                                                               ```
                                                                                                               
                                                                                                               ### API Utilizada
                                                                                                               
                                                                                                               - **Endpoint:** `https://api.github.com/repos/[owner]/[repo]/contents/[file]`
                                                                                                               - - **Método:** PUT (crear/actualizar)
                                                                                                                 - - **Autenticación:** Token Bearer
                                                                                                                   - - **Formato:** Base64 encoding del contenido JSON
                                                                                                                    
                                                                                                                     - ---
                                                                                                                     
                                                                                                                     ## ✅ Ejemplo de Uso Completo
                                                                                                                     
                                                                                                                     1. Abre `editor-carniceria.html`
                                                                                                                     2. 2. Configura el token:
                                                                                                                        3.    ```javascript
                                                                                                                                 setGitHubToken("ghp_xxxxxxxxxxxxxxxxxxxx")
                                                                                                                                 ```
                                                                                                                              3. Agregar un nuevo producto:
                                                                                                                              4.    - Rellena el formulario
                                                                                                                                    -    - Haz clic en "Guardar producto"
                                                                                                                                         -    - Los datos se guardan en LocalStorage
                                                                                                                                          
                                                                                                                                              - 4. Sincronizar con GitHub:
                                                                                                                                                5.    - Haz clic en "☁ Sincronizar con GitHub"
                                                                                                                                                      -    - Espera a que se complete
                                                                                                                                                           -    - Verifica en GitHub que el archivo se actualizó
                                                                                                                                                            
                                                                                                                                                                - 5. Ver cambios en GitHub:
                                                                                                                                                                  6.    - Ve a https://github.com/josemarcosservia-cmyk/Cash-Record-Virtual
                                                                                                                                                                        -    - Abre `carniceria-productos.json`
                                                                                                                                                                             -    - Verás el timestamp de actualización
                                                                                                                                                                              
                                                                                                                                                                                  - ---
                                                                                                                                                                                  
                                                                                                                                                                                  ## 🔗 Enlaces Útiles
                                                                                                                                                                                  
                                                                                                                                                                                  - [Crear Personal Access Token](https://github.com/settings/tokens)
                                                                                                                                                                                  - - [Documentación GitHub API](https://docs.github.com/es/rest)
                                                                                                                                                                                    - - [REST API Contents](https://docs.github.com/en/rest/repos/contents?apiVersion=2022-11-28)
                                                                                                                                                                                     
                                                                                                                                                                                      - ---
                                                                                                                                                                                      
                                                                                                                                                                                      ## 📞 Soporte
                                                                                                                                                                                      
                                                                                                                                                                                      Si encuentras problemas:
                                                                                                                                                                                      
                                                                                                                                                                                      1. Revisa la Consola del Navegador (F12)
                                                                                                                                                                                      2. 2. Verifica que el token sea válido
                                                                                                                                                                                         3. 3. Asegúrate que tienes permisos en el repositorio
                                                                                                                                                                                            4. 4. Intenta regenerar el token en GitHub
                                                                                                                                                                                              
                                                                                                                                                                                               5. ---
                                                                                                                                                                                              
                                                                                                                                                                                               6. **Última actualización:** 4 de Agosto de 2026
                                                                                                                                                                                               7. **Versión:** 1.0
