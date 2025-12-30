# Guía de Configuración del Nodo de Federación

¡Bienvenido a la Federación de Agrinet! Esta guía lo guiará a través de la configuración de su nodo, sincronización con Mycelium, generación de claves McEliece y ejemplo de contrato de interfaz de usuario.

## Requisitos Previos

- Node.js (v14+ recomendado)
- - Git
  - - Yarn o npm
    - - Acceso al repositorio de Agrinet
     
      - ## Clonar el Repositorio
     
      - ```bash
        git clone https://github.com/NTARI-RAND/Agrinet.git
        cd Agrinet
        ```

        ## Instalar Dependencias

        ```bash
        # Usando yarn
        yarn install

        # O usando npm
        npm install
        ```

        ## Sincronización Mycelium

        Mycelium es el protocolo utilizado para sincronizar nodos de federación.

        ### Configuración

        Localice o cree su archivo .env en la raíz del proyecto y agregue:

        ```
        MYCELIUM_NODE_NAME=your-node-name
        MYCELIUM_PEER_URLS=https://peer1.example.com,https://peer2.example.com
        MYCELIUM_PORT=7000
        ```

        ### Iniciar Nodo Mycelium

        ```bash
        yarn mycelium:start
        # o
        npm run mycelium:start
        ```

        ## Generación de Clave (McEliece)

        McEliece es un criptosistema utilizado para comunicación segura entre nodos de federación.

        ### Generar Claves McEliece

        ```bash
        node scripts/gen-mceliece.js
        ```

        ## Ejemplo de Contrato de Interfaz de Usuario

        Un contrato de interfaz de usuario define la interacción entre la interfaz de usuario y la API del nodo de federación.

        ```javascript
        module.exports = {
          authenticateUser: async (publicKey) => {
            // implementación
          },
          requestSync: async () => {
            // implementación
          },
          submitTransaction: async (transaction, signature) => {
            // implementación
          }
        };
        ```

        ## Pasos Finales

        ✅ Pruebe su nodo de federación ejecutando el stack completo
        🔐 Asegúrese de que las claves se generen correctamente
        🔗 Utilice los métodos de contrato de interfaz de usuario en su integración de frontend

        Para más información, consulte: https://github.com/NTARI-RAND/Agrinet/blob/main/docs/ONBOARDING.md
