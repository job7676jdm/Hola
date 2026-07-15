### Conceptos básicos que estoy aprendiendo

- Layer 2 vs Layer 1
- Chain ID de Base (8453)
- Diferencia entre mainnet y testnet
- Importancia de los fees bajos para experimentar


### Objetivos iniciales

- Entender bien cómo funciona Base como L2
- Aprender Solidity básico
- Probar herramientas de desarrollo
- Documentar todo el proceso en este repo

### Por qué estoy documentando todo aquí

- Me ayuda a consolidar lo aprendido
- Crea un historial visible de progreso
- Puede servir de referencia en el futuro
- Es buena práctica para cualquier builder

### Primer paso recomendado para nuevos builders

1. Configurar wallet + red Base
2. Probar enviar una transacción pequeña
3. Explorar un DEX (como Aerodrome)
4. Empezar a leer documentación oficial

Este es el camino que estoy siguiendo.

### Importancia de los eventos en contratos

Los eventos permiten que el frontend sepa cuándo pasa algo en el contrato (ej: un mint, un swap, un cambio de estado).

### Primera aproximación a Solidity

Solidity es el lenguaje principal para escribir contratos inteligentes en Base.

Características básicas:
- Similar a JavaScript en sintaxis
- Es fuertemente tipado
- Se compila a bytecode para la EVM

- ### Primer proyecto recomendado para practicar

Un contador on-chain simple:
- Contrato que permite incrementar un número
- Frontend que muestra el valor y botón para modificar
- Desplegarlo en Base

Es un clásico para empezar.

### Conceptos básicos de DeFi en Base

- DEX (Decentralized Exchange): Para hacer swaps
- Lending: Prestar y pedir prestado
- Yield Farming: Ganar rendimiento con liquidez
- Liquidity Pools: Proporcionar liquidez a cambio de fees

Base es un buen lugar para empezar en DeFi por sus bajos fees.

### Por qué Base es ideal para principiantes

- Fees muy bajos → Puedes cometer errores sin perder mucho
- Buena documentación
- Comunidad activa
- Integración con Coinbase Wallet

Es una excelente red para aprender y construir.

### Consejos importantes para no perder fondos

- Nunca des tu seed phrase
- Verificar direcciones antes de enviar
- Usar cantidades pequeñas al principio
- Revisar contratos antes de interactuar

- ### Composability en DeFi

Es la capacidad de que los protocolos se combinen entre sí como "bloques de Lego".

Ejemplo: Usar un préstamo para hacer yield farming en otro protocolo.

### Importancia del código abierto en web3

Publicar los contratos y el código del frontend permite:
- Transparencia
- Auditorías por la comunidad
- Que otros puedan aprender y mejorar

### Contrato Counter simple (primer experimento)

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Counter {
    uint256 public count = 0;

    function increment() public {
        count += 1;
    }

    function decrement() public {
        count -= 1;
    }

    function reset() public {
        count = 0;
    }
}
**Mensaje:** `docs: script de despliegue básico con Hardhat`

**Texto para añadir:**

```markdown
### Script de despliegue básico (Hardhat)

```javascript
// deploy.js
const hre = require("hardhat");

async function main() {
  const Counter = await hre.ethers.getContractFactory("Counter");
  const counter = await Counter.deploy();

  await counter.deployed();
  console.log("Counter desplegado en:", counter.address);
}

main().catch((error) => {
  console.error(error);
  process.exit(1);
});

**Mensaje:** `docs: frontend básico para interactuar con Counter`

**Texto para añadir:**

```markdown
### Frontend básico para interactuar con el Counter

```html
<button onclick="increment()">Incrementar</button>
<p>Contador: <span id="value">0</span></p>

<script>
  // Código con ethers.js para llamar al contrato en Base
</script>

```markdown
### Idea de mejora al Counter

Añadir:
- Eventos cuando se modifica el contador
- Ownership (solo owner puede resetear)
- Contador por usuario

Esto lo haría más útil como proyecto de práctica.
