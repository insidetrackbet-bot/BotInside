# 🏇 Inside Track - Casa de apuestas ®

## Descripción del Proyecto

Sistema completo de apuestas y casino para Discord con carreras de caballos automatizadas, peleas de boxeo profesionales y juegos de casino. Diseñado con una interfaz profesional y elegante, sistema de cuotas dinámicas, registro de peleadores y auditoría completa de transacciones.

## Estado Actual

✅ Bot completamente funcional y operativo
✅ Sistema profesional de cuotas y registro de peleadores
✅ Comisión automática del 10% en carreras
✅ Sistema de auditoría y registros de transacciones
✅ Embeds profesionales con branding "Inside Track"
✅ Sistema de economía robusto y sin exploits

## Estructura del Proyecto

```
├── bot.js              # Archivo principal del bot con todos los comandos
├── package.json        # Dependencias del proyecto (Discord.js v14)
└── replit.md          # Esta documentación
```

## Comandos Disponibles

### 📊 Comandos Administrativos

- **!balance [@usuario]** - Ver el saldo propio o de otro usuario
  - Ejemplo: `!balance` o `!balance @Juan`

- **!apuestastotal** - Ver todas las apuestas activas con detalles
  - Muestra carreras y peleas activas con montos totales apostados

- **!apostadores** - Ver el ranking de los 10 usuarios con más dinero
  - Formato de tabla profesional con posiciones

- **!dardinero @usuario <cantidad>** - Dar dinero a un usuario (solo admin)
  - Ejemplo: `!dardinero @Juan 5000`
  - Registra la transacción para auditoría

- **!quitardinero @usuario <cantidad>** - Quitar dinero a un usuario (solo admin)
  - Ejemplo: `!quitardinero @Juan 1000`
  - Registra la transacción para auditoría

- **!registros [cantidad]** - Ver auditoría de transacciones
  - Usuarios normales: Ver sus últimas 10 transacciones
  - Administradores: Ver últimas N transacciones del sistema (default 20)
  - Ejemplo: `!registros 50` (admin)

### 🎰 Juegos de Casino

#### Slots
- **!slots <cantidad>** - Jugar a las máquinas tragamonedas
  - Símbolos: 🍒 🍋 🍊 💎 7️⃣ ⭐
  - Multiplicador x3 por tres símbolos iguales
  - Multiplicador x5 por tres 💎
  - Multiplicador x10 por tres 7️⃣
  - Ejemplo: `!slots 500`

#### Ruleta
- **!ruleta <color/número> <cantidad>** - Jugar a la ruleta europea
  - Colores: rojo, negro, verde (0)
  - Números: 0-36
  - Pago x2 por color correcto
  - Pago x36 por número exacto
  - Ejemplos: `!ruleta rojo 1000` o `!ruleta 17 100`

#### Blackjack
- **!blackjack <cantidad>** - Iniciar una partida de blackjack
  - Objetivo: Llegar a 21 o lo más cerca posible sin pasarse
  - Dealer debe llegar a 17 mínimo
  - Ejemplo: `!blackjack 500`

- **!hit** - Pedir otra carta durante la partida

- **!stand** - Plantarse con las cartas actuales

### 🏇 Carreras de Caballos (Inside Track)

- **!insidetrack** - Iniciar una nueva carrera de caballos
  - Genera 4 caballos con nombres aleatorios y cuotas
  - La carrera dura exactamente 3 minutos
  - **Comisión automática del 10% sobre ganancias**
  - Multiplicador x3 si aciertas el ganador (antes de comisión)
  - Ganancia neta = (Apuesta x 3) - 10%

- **!vercaballos** - Ver los caballos participantes de la carrera actual
  - Muestra los 4 caballos numerados con sus cuotas
  - Muestra el total apostado en la carrera

- **!apostarcaballo <número> <cantidad>** - Apostar en un caballo
  - Números del 1 al 4
  - Muestra ganancia potencial después de comisión
  - Ejemplo: `!apostarcaballo 3 2000`

### 🥊 Peleas de Boxeo (Sistema Profesional)

#### Gestión de Peleadores (Solo Admin)

- **!registrarpeleador <nombre> <cuota>** - Registrar un nuevo peleador
  - El nombre puede tener espacios (usar comillas si tiene espacios)
  - La cuota debe ser >= 1.0
  - Ejemplo: `!registrarpeleador "Mike Tyson" 1.8`
  - Ejemplo: `!registrarpeleador Floyd_Mayweather 2.1`

- **!ajustarcuotapeleador <id_peleador> <nueva_cuota>** - Ajustar cuota de un peleador
  - El ID es el nombre en minúsculas con guiones bajos
  - Ejemplo: `!ajustarcuotapeleador mike_tyson 2.5`

- **!peleadores** - Ver todos los peleadores registrados
  - Muestra tabla con nombre, cuota y récord

#### Gestión de Peleas

- **!crearpelea <id_peleador1> <id_peleador2>** - Crear una pelea (solo admin)
  - Usa los IDs de peleadores registrados (no @menciones)
  - Asigna un ID único a la pelea automáticamente
  - Ejemplo: `!crearpelea mike_tyson floyd_mayweather`

- **!peleas** - Ver todas las peleas programadas activas
  - Muestra ID, participantes, cuotas y total apostado

- **!apostarpelea <ID> <1/2> <cantidad>** - Apostar en una pelea
  - ID: Número de la pelea
  - 1 = Esquina Roja (primer peleador)
  - 2 = Esquina Azul (segundo peleador)
  - Muestra ganancia potencial según cuota del peleador
  - Ejemplo: `!apostarpelea 5234 1 1500`

- **!finalizarpelea <ID> <id_ganador>** - Finalizar pelea y declarar ganador (solo admin)
  - Usa el ID del peleador ganador (no número de esquina)
  - Paga según la cuota del ganador
  - Actualiza récords automáticamente
  - Ejemplo: `!finalizarpelea 5234 mike_tyson`

### ℹ️ Ayuda

- **!ayuda** - Muestra la lista completa de comandos disponibles

## Características Técnicas

### Sistema de Economía
- Balance inicial: 1000 monedas por usuario
- Almacenamiento en memoria (Map)
- Previene balances negativos
- Formato con separadores de miles para mejor legibilidad
- Sistema de escrow en blackjack (descuenta apuesta al inicio)
- Validación robusta de balances en todas las transacciones

### Sistema de Auditoría
- Todas las transacciones se registran automáticamente
- Tipo de transacción: crédito, débito, inicial
- Descripción detallada de cada movimiento
- Timestamp de cada transacción
- Los usuarios pueden ver sus últimas 10 transacciones
- Los administradores pueden ver el historial completo del sistema

### Carreras Automatizadas con Comisión
- Duración fija de 3 minutos (180000ms)
- 4 caballos con nombres aleatorios y cuotas cada carrera
- Pool de nombres: Thunder, Lightning, Storm, Blaze, Shadow, Spirit, Phoenix, Rocket, Flash, Comet, Tornado, Bullet, Mustang, Hurricane, Champion
- **Comisión automática del 10% sobre ganancias brutas**
- Ganancia neta = (Apuesta x 3 x 0.9)
- Sistema de apuestas con multiplicador x3 base
- Muestra comisión total recaudada al finalizar

### Sistema Profesional de Boxeo
- **Registro de peleadores con nombres personalizados**
- Sistema de cuotas dinámicas ajustables
- Récord automático de victorias y derrotas
- Identificadores únicos para cada peleador
- Pagos según cuota del ganador
- No requiere @menciones, solo nombres/IDs

### Embeds Profesionales
- **Branding unificado: "Inside Track - Casa de apuestas ®"**
- Colores corporativos profesionales:
  - Azul oscuro (#1E3A8A) para información general
  - Verde (#059669) para ganancias y éxito
  - Rojo (#DC2626) para pérdidas y peleas
  - Dorado (#D97706) para carreras
  - Morado (#7C3AED) para rankings
- Footers específicos por sección:
  - "Inside Track Financial" para balances
  - "Inside Track Carreras" para caballos
  - "Apuestas Boxing Los Santos" para peleas
  - "Casino [Juego]" para juegos de casino
- Timestamps en todos los mensajes
- Íconos y emojis apropiados por contexto
- Formato consistente y elegante

### Permisos y Seguridad
- Comandos administrativos restringidos a usuarios con permiso "Administrator"
- Validación de montos y balances en todas las apuestas
- Prevención de apuestas negativas o inválidas
- Verificación de existencia de peleadores y peleas
- Sistema de escrow que previene fraudes económicos
- No se pueden duplicar peleadores
- IDs únicos automáticos para peleas

## Variables de Entorno

- **DISCORD_TOKEN** - Token del bot de Discord (configurado en Secrets)

## Tecnologías Utilizadas

- **Node.js** v20+
- **Discord.js** v14.14.1 (última versión estable)
- **JavaScript** ES6+

## Flujo de Trabajo

### Carreras de Caballos
1. Admin/Usuario inicia carrera con `!insidetrack`
2. Sistema genera 4 caballos con cuotas aleatorias
3. Usuarios apuestan durante 3 minutos con `!apostarcaballo`
4. El dinero se descuenta inmediatamente al apostar
5. Al finalizar, se determina el ganador aleatorio
6. Se calcula comisión del 10% sobre ganancias brutas
7. Se paga a los ganadores (apuesta x 3 - 10% comisión)
8. Se anuncia el ganador y la comisión total recaudada

### Peleas de Boxeo
1. Admin registra peleadores con `!registrarpeleador`
2. Admin ajusta cuotas según necesidad con `!ajustarcuotapeleador`
3. Admin crea pelea con `!crearpelea id_p1 id_p2`
4. Usuarios consultan peleas activas con `!peleas`
5. Usuarios apuestan con `!apostarpelea ID esquina cantidad`
6. El dinero se descuenta inmediatamente
7. Admin finaliza pelea con `!finalizarpelea ID id_ganador`
8. Sistema paga según cuota del ganador
9. Actualiza récords de ambos peleadores automáticamente

### Juegos de Casino
1. Usuario inicia juego (slots, ruleta, blackjack)
2. El dinero se descuenta al inicio
3. Se ejecuta el juego
4. Se determina resultado
5. Se acredita ganancia si aplica
6. Todo se registra en auditoría automáticamente

## Mejoras Implementadas

### Profesionalismo
- Branding consistente "Inside Track - Casa de apuestas ®"
- Diseño elegante con colores corporativos
- Formato de tablas profesionales para rankings y peleadores
- Mensajes claros y descriptivos
- Separadores de miles en todas las cantidades

### Sistema de Cuotas
- Cuotas dinámicas ajustables por administradores
- Cuotas visibles en todas las consultas
- Cálculo automático de ganancias potenciales
- Sistema de multiplicadores realista

### Comisión de la Casa
- 10% automático en carreras de caballos
- Se muestra en la descripción de la carrera
- Se calcula en la ganancia potencial mostrada al apostar
- Se anuncia la comisión total al finalizar la carrera

### Auditoría Completa
- Registro de todas las transacciones
- Consulta personal para usuarios
- Consulta completa para administradores
- Trazabilidad total del dinero

## Próximas Mejoras Sugeridas

- Persistencia de datos con base de datos PostgreSQL
- Sistema de niveles VIP para apostadores frecuentes
- Torneos programados de blackjack
- Estadísticas detalladas por usuario y peleador
- Cooldowns opcionales en comandos de juego
- Sistema de jackpot progresivo en slots
- Notificaciones automáticas de carreras próximas
- API REST para integración externa
- Panel web de administración

## Notas de Desarrollo

- El bot usa Discord.js v14 con intents de mensajes y miembros
- El deprecation warning de clientReady es normal y no afecta funcionalidad
- La estructura modular permite fácil adición de nuevos juegos
- Todos los juegos tienen validaciones robustas contra exploits
- Los embeds siguen un patrón consistente con el branding
- El sistema de cuotas es flexible y extensible
- La comisión del 10% es configurable en la constante HOUSE_COMMISSION

## Soporte y Uso

Para dudas o sugerencias sobre Inside Track, usa el comando `!ayuda` en Discord.

**Administradores:** Recuerden registrar peleadores antes de crear peleas, y usar los IDs correctos (minúsculas con guiones bajos) al finalizar peleas.

---

**Fecha de creación:** Noviembre 2025
**Versión:** 2.0.0 Professional
**Estado:** Producción
**Marca:** Inside Track - Casa de apuestas ®
