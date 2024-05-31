# AVAXGods - Solidity Card Game on Avalanche (AVAX)

Welcome to AVAXGods, a decentralized card game built on the Avalanche (AVAX) blockchain using Solidity and Hardhat. This repository contains the smart contracts and front-end code necessary to run the game.

`AVAXGods` es un contrato inteligente basado en Solidity para un juego de batalla en la blockchain. Utiliza el estándar ERC-1155 para tokens no fungibles (NFTs) y permite a los jugadores registrar, crear tokens de batalla y participar en batallas.

## Características

- **ERC-1155 Tokens**: Utiliza el estándar ERC-1155 para manejar tokens de batalla.
- **Registro de Jugadores**: Los jugadores pueden registrarse proporcionando un nombre y un nombre para su token de batalla.
- **Creación de Tokens**: Los jugadores pueden crear tokens de batalla con atributos aleatorios de ataque y defensa.
- **Batallas**: Los jugadores pueden crear y unirse a batallas. Las batallas consisten en elegir entre atacar o defender, y los resultados se resuelven de acuerdo a los atributos de los tokens.

## Descripción del Contrato

### Variables Públicas

- `baseURI`: La URI base donde se almacena la metadata de los tokens.
- `totalSupply`: El número total de tokens minteados.
- `MAX_ATTACK_DEFEND_STRENGTH`: La fuerza máxima de ataque y defensa para los tokens de batalla.

### Enums

- `BattleStatus`: Representa el estado de una batalla (`PENDING`, `STARTED`, `ENDED`).

### Estructuras

- `GameToken`: Representa un token de batalla con atributos como nombre, ID, fuerza de ataque y fuerza de defensa.
- `Player`: Representa un jugador con atributos como dirección, nombre, mana, salud y estado de batalla.
- `Battle`: Representa una batalla con atributos como estado, hash, nombre, jugadores, movimientos y ganador.

### Funciones Públicas

- `isPlayer(address addr)`: Verifica si una dirección es un jugador registrado.
- `getPlayer(address addr)`: Obtiene la información de un jugador.
- `getAllPlayers()`: Obtiene todos los jugadores registrados.
- `isPlayerToken(address addr)`: Verifica si una dirección tiene un token de jugador registrado.
- `getPlayerToken(address addr)`: Obtiene la información de un token de jugador.
- `getAllPlayerTokens()`: Obtiene todos los tokens de jugadores registrados.
- `isBattle(string memory _name)`: Verifica si una batalla con un nombre dado existe.
- `getBattle(string memory _name)`: Obtiene la información de una batalla.
- `getAllBattles()`: Obtiene todas las batallas registradas.
- `registerPlayer(string memory _name, string memory _gameTokenName)`: Registra un nuevo jugador.
- `createRandomGameToken(string memory _name)`: Crea un token de batalla aleatorio para un jugador registrado.
- `getTotalSupply()`: Obtiene el suministro total de tokens.
- `createBattle(string memory _name)`: Crea una nueva batalla.
- `joinBattle(string memory _name)`: Permite a un jugador unirse a una batalla existente.
- `attackOrDefendChoice(uint8 _choice, string memory _battleName)`: Permite a un jugador elegir atacar o defender en una batalla.
- `quitBattle(string memory _battleName)`: Permite a un jugador abandonar una batalla.
- `tokenURI(uint256 tokenId)`: Obtiene la URI del token.

### Eventos

- `NewPlayer(address indexed owner, string name)`: Emitido cuando un nuevo jugador se registra.
- `NewBattle(string battleName, address indexed player1, address indexed player2)`: Emitido cuando se crea una nueva batalla.
- `BattleEnded(string battleName, address indexed winner, address indexed loser)`: Emitido cuando una batalla termina.
- `BattleMove(string indexed battleName, bool indexed isFirstMove)`: Emitido cuando un jugador realiza un movimiento en una batalla.
- `NewGameToken(address indexed owner, uint256 id, uint256 attackStrength, uint256 defenseStrength)`: Emitido cuando se crea un nuevo token de batalla.
- `RoundEnded(address[2] damagedPlayers)`: Emitido cuando termina una ronda en una batalla.

## Instalación

Para desplegar e interactuar con este contrato, sigue los siguientes pasos:

1. Clona el repositorio:
   ```sh
   git clone https://github.com/tu_usuario/avaxgods.git
   cd avaxgods
   ```

2. Instala las dependencias:
   ```sh
   npm install
   ```

3. Compila el contrato:
   ```sh
   npx hardhat compile
   ```

4. Despliega el contrato:
   ```sh
   npx hardhat run scripts/deploy.js --network <tu_red>
   ```
