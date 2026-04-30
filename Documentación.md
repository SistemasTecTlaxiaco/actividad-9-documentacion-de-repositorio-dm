# DOCUMENTACIÓN DEL PROYECTO COFFEE TEC

## Introducción
**CoffeeTec** es una aplicación descentralizada (DApp) diseñada para la gestión de activos y dinero digital dentro de un entorno basado en tecnología blockchain. La plataforma está construida sobre la red **Stellar**, la cual permite realizar transacciones rápidas y de bajo costo, así como la creación y transferencia de activos digitales en una red global descentralizada.

A través de la integración de contratos inteligentes con **Soroban**, CoffeeTec incorpora capacidades avanzadas de programación que permiten automatizar procesos financieros y ejecutar operaciones de manera segura sin la necesidad de intermediarios.
##repositorio: https://github.com/SistemasTecTlaxiaco/coffetec

## Objetivo del Proyecto
Desarrollar una plataforma descentralizada que permita:
*   Realizar transacciones de activos sin intermediarios.
*   Garantizar seguridad mediante la infraestructura de **Stellar**.
*   Proveer transparencia total en cada operación mediante Smart Contracts.
*   Simular un ecosistema financiero digital moderno y eficiente.

## Tecnologías Utilizadas
El stack tecnológico de **CoffeeTec** ha sido seleccionado para garantizar un desarrollo robusto, escalable y alineado con los estándares de la Web 3.0:

### 1. Blockchain y Contratos Inteligentes
*   **Stellar Network:** Red descentralizada utilizada para el intercambio de valor y activos.
*   **Soroban (Rust):** Plataforma de contratos inteligentes de Stellar. Se utiliza Rust por su seguridad de memoria y alto rendimiento para la lógica de los contratos (`contador` y `token`).
*   **Soroban SDK:** Kit de desarrollo para interactuar con el entorno de ejecución de Smart Contracts.


## Funcionalidades del Sistema
*   **Gestión de Tokens:** Funciones de emisión (`mint`), transferencia (`transfer`) y quema de activos (`burn`).
*   **Contador de Operaciones:** Registro persistente de la actividad del contrato para auditoría.
*   **Consulta de Saldo:** Panel de control para visualizar balances en tiempo real.
*   **Historial de Transacciones:** Registro inmutable respaldado por la blockchain.

## Integración con Blockchain

### Lectura de datos
*   `balance(account: Address)`: Consulta el saldo de una cuenta específica.
*   `total_supply()`: Recupera el suministro total de activos emitidos.

### Escritura de datos (Transacciones)
*   `mint(to, amount)`: Crea nuevos activos en la red.
*   `transfer(from, to, amount)`: Mueve activos tras validar la solvencia del emisor.
*   `increment()`: Registra una nueva acción en el contador global.

## Puntos finales de la API (Endpoints)

El backend de CoffeeTec expone los siguientes endpoints para interactuar con la lógica del contrato y los datos de usuario:

### Consultas (GET)
*   `GET /usuario/:id`: Obtiene el perfil y datos básicos del usuario registrado.
*   `GET /saldo/:id`: Consulta el balance de tokens actual directamente desde la blockchain.
*   `GET /transacciones/:id`: Recupera el historial de operaciones vinculadas a una dirección específica.
*   `GET /contador/valor`: Obtiene el estado actual del contador persistente del contrato.

### Operaciones de Escritura (POST)
*   `POST /usuario/crear`: Registra una nueva identidad en el sistema vinculado a una Address.
*   `POST /transferencia/enviar`: Ejecuta el envío de tokens entre cuentas (Llama a la función `transfer`).
*   `POST /token/mint`: Función administrativa para emitir nuevos activos (Llama a la función `mint`).
*   `POST /contador/incrementar`: Registra una nueva acción incrementando el contador en el contrato.

### Actualizaciones (PUT)
*   `PUT /usuario/actualizar`: Permite modificar la información del perfil del usuario.
*   `PUT /transaccion/confirmar`: Valida y actualiza el estado de una operación pendiente.

## Integración con Blockchain
El sistema implementa dos funciones internas principales en el backend para gestionar la comunicación:

1.  **`leerDatos(metodo, args)`**: Consulta información sin modificar el estado de la blockchain (no consume gas). Ejemplo: Consultar el saldo.
2.  **`ejecutarAccion(metodo, args)`**: Ejecuta transacciones que modifican el estado, requiere firma y genera un **Hash de Transacción** único.

## Flujo de funcionamiento y Diagrama de Arquitectura
<img width="1408" height="768" alt="Gemini_Generated_Image_kbbwf1kbbwf1kbbw" src="https://github.com/user-attachments/assets/8306c626-9b02-4a12-b30b-62e142b87d95" />


## Conclusión
**CoffeeTec** representa una implementación práctica de los principios de la **Web 3.0**, demostrando cómo las tecnologías descentralizadas pueden transformar la gestión de activos hacia un modelo más seguro, transparente y sin intermediarios, integrando exitosamente contratos inteligentes con una interfaz funcional.
