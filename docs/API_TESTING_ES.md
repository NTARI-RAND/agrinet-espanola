# Guía de Pruebas de API de Agrinet

Esta guía lo ayudará a probar la API de backend para los componentes de Chat-UI utilizando comandos curl. Explica resultados esperados, errores comunes y consejos de solución de problemas.

## 1. Puertos de Servicio y Puntos Finales

| Servicio | Puerto | Uso |
|----------|--------|-----|
| Backend | 5000 | Solicitudes de API |
| Frontend | 3000 | Interfaz de usuario Next.js |

Use el puerto 5000 para pruebas de API a menos que se configure de otra manera.

## 2. Autenticación

La mayoría de los puntos finales de la API requieren una clave de API válida:

Pasar con encabezado: `x-api-key: <your-key>`

Ejemplo:
```bash
curl -X POST http://localhost:5000/conversations \
  -H "Content-Type: application/json" \
  -H "x-api-key: da2-5z3fzvunwvhwtbyudvutf6x6by" \
  -d '{"title": "Chat QA Demo"}'
```

Si ve: `{"error":"Unauthorized: Invalid API Key"}`
→ Su clave de API es inválida, falta o no es reconocida por el backend.

## 3. Vocabulario Principal

- **Backend** - Servidor: API del lado del servidor
- - **Frontend** - Interfaz de usuario
  - - **Clave** - Key: token de autenticación
    - - **Error** - Error: problema en la solicitud
      - - **Punto Final** - Endpoint: dirección URL de la API
       
        - ## 4. Comandos Importantes
       
        - ```bash
          # Verificar salud
          curl -X GET http://localhost:5000/health

          # Crear conversación
          curl -X POST http://localhost:5000/conversations

          # Enviar mensaje
          curl -X POST http://localhost:5000/messages/<id>
          ```

          ## 5. Errores Comunes

          | Error | Significado |
          |-------|------------|
          | Cannot GET | Puerto incorrecto o punto final no implementado |
          | Unauthorized | Clave de API inválida |
          | 404 Error | Página no encontrada |

          ## 6. Solución de Problemas

          - Verifique el backend en el puerto 5000
          - - Valide la clave de API
            - - Revise los registros del backend
             
              - ## 7. Verificación de Frontend vs Backend
             
              - - **Frontend (localhost:3000)**: Para acceso del navegador; siempre devuelve HTML
                - - **Backend (localhost:5000)**: Para API; devuelve JSON (si funciona)
                 
                  - Para más información, consulte el documento original: https://github.com/NTARI-RAND/Agrinet/blob/main/docs/API_TESTING.md
