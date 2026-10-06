#  2D Evolutionary Ecosystem

A 2D ecosystem simulation that runs entirely in the browser, with no dependencies and no install. Plants, herbivores and carnivores make decisions from their perception, energy and genes, so chases, famines and local extinctions **emerge from the rules** instead of following a script. You play as a "God" who can intervene in the world.

*Also available in Spanish: [README.es.md](README.es.md).*

## Running it

1. Download or clone the repository.
2. Open `ecosistema.html` in any modern browser. The simulation starts on its own.

To publish with **GitHub Pages**, rename the file to `index.html` and enable Pages under *Settings → Pages*.

## What it simulates

**Biomes.** Five biomes, generated with smooth noise on every new world. They genuinely affect the simulation:

| Biome | Plants | Movement | Visibility | Climate |
|---|---|---|---|---|
| Prairie | abundant | normal | normal | mild |
| Forest | very abundant | slightly slower | reduced | mild |
| Desert | scarce | normal | wide | hot, higher energy cost |
| Swamp | very abundant | slow | medium | humid |
| Tundra | scarce | slow | normal | cold, higher energy cost |

**Plants.** They grow gradually, spread by nearby seeds, can be partially eaten, and die of old age. A small share are **hallucinogenic** (purple and glowing).

**Animals.** Herbivores and carnivores share the same logic and differ only by their traits. Each has an age, growth, health, energy and a state (wander, search, eat, flee, chase, attack, seek mate, rest). Priorities: danger, prey, mate, food, exploration.

- **Carnivores:** perceive through a working **45° cone**. They chase, intercept, stop, attack with a wind-up and lunge animation, and feed on the corpse. They tire if a chase lasts too long.
- **Herbivores:** detect predators, flee in zigzags and eat plants. A rare mutation, `defPred`, lets them defend themselves and eat carnivores.
- **Life cycle:** birth, growth, maturity, reproduction, aging and death (from age, hunger, predation or environment).

**Genetics.** Offspring mix both parents' genes and may mutate slightly: speed, size, perception, lifespan, feeding efficiency, aggression, heat resistance, cold resistance and `defPred`. Natural selection does the rest: over time, desert or tundra populations adapt to their biome.

**Hallucinogenic plants.** A herbivore that eats one trips for 25 s: it changes color, moves at double speed and attacks any nearby animal.

## God powers

| Power | Effect |
|---|---|
| Pacify (`P`) | Carnivores stop hunting for 15 s (30 s cooldown). |
| Follow me (`G`) | For 25 s every animal heads toward God. |
| Fury (`T`) | For 30 s every animal attacks the nearest animal, faster and with more damage. |

The consequences (more herbivores, fewer plants, later imbalances) play out on their own.

## Controls

| Key / action | Function |
|---|---|
| `W` `A` `S` `D` | Move God |
| `P` / `G` / `T` | Pacify / Follow me / Fury |
| `Space` | Pause and resume |
| `+` / `-` | Simulation speed (0.5x to 8x) |
| `Q` / `E` or wheel | Zoom |
| `V` | Show perception cones |
| `B` | Debug mode (state, heading, target) |
| `F` | Follow the selected organism |
| `C` | Center the camera on God |
| `R` | Restart with a new world |
| Click | Inspect an organism (age, health, energy, genes, offspring) |

Every control also has an on-screen button, so it works on mobile.

## Configuration

The main parameters live in the `C` object at the top of the script: map size, initial and maximum populations, mutation rate and magnitude, `defPred` probability, reproduction costs and cooldowns, power durations and available speeds. Base traits for each species are in `BASE`, and biomes are in `BI`.

## Population balance

Populations fluctuate naturally. To keep the ecosystem from emptying out, if carnivores fall below a minimum (`minCarn`) new ones appear next to prey, and if herbivores drop below 20 new ones enter from the map edge.

## Known limitations

- All the code is in a single HTML file. It works, but it is not split into modules.
- There are no physical obstacles: trees are decoration, and forest only reduces visibility and speed.
- Games cannot be saved or loaded.
- The balance between species may need tuning in `C` and `BASE` depending on how long it runs.
- With the large map at 8x it may be slow on modest hardware.

## License

Add the license of your choice here (for example MIT).


# Ecosistema evolutivo 2D

Simulación de ecosistema 2D que corre íntegramente en el navegador, sin dependencias ni instalación. Plantas, herbívoros y carnívoros toman decisiones a partir de su percepción, su energía y sus genes, de modo que las persecuciones, las hambrunas o las extinciones locales **surgen de las reglas** y no de un guion. Tú juegas como un "Dios" que puede intervenir en el mundo.

## Cómo ejecutarlo

1. Descarga o clona el repositorio.
2. Abre `ecosistema.html` en cualquier navegador moderno. La simulación empieza sola.

Para publicarlo con **GitHub Pages**, renombra el archivo a `index.html` y activa Pages en *Settings → Pages*.

## Qué simula

**Biomas.** Cinco biomas generados con ruido suave en cada partida. Afectan de verdad a la simulación:

| Bioma | Plantas | Movimiento | Visibilidad | Clima |
|---|---|---|---|---|
| Pradera | abundantes | normal | normal | templado |
| Bosque | muy abundantes | algo más lento | reducida | templado |
| Desierto | escasas | normal | amplia | calor, más gasto de energía |
| Pantano | muy abundantes | lento | media | húmedo |
| Tundra | escasas | lento | normal | frío, más gasto de energía |

**Plantas.** Crecen poco a poco, se reproducen por semillas cercanas, se pueden comer parcialmente y mueren de vejez. Un pequeño porcentaje son **alucinógenas** (moradas y brillantes).

**Animales.** Herbívoros y carnívoros comparten la misma lógica y se diferencian por sus rasgos. Cada uno tiene edad, crecimiento, vida, energía y un estado (deambular, buscar, comer, huir, perseguir, atacar, buscar pareja, descansar). Prioridades: peligro, presa, pareja, comida, exploración.

- **Carnívoros:** perciben con un **cono de 45°** que funciona de verdad. Persiguen, interceptan, se paran, atacan con una animación de preparación y embestida, y se alimentan del cadáver. Se cansan si la persecución dura demasiado.
- **Herbívoros:** detectan depredadores, huyen en zigzag y comen plantas. Pueden desarrollar por mutación rara `defPred`, que les permite defenderse y comer carnívoros.
- **Ciclo de vida:** nacimiento, crecimiento, madurez, reproducción, envejecimiento y muerte (por edad, hambre, depredación o ambiente).

**Genética.** Los hijos mezclan los genes de ambos padres y pueden mutar ligeramente: velocidad, tamaño, percepción, esperanza de vida, eficiencia alimenticia, agresividad, resistencia al calor, resistencia al frío y `defPred`. La selección natural hace el resto: con el tiempo las poblaciones del desierto o la tundra se adaptan a su bioma.

**Plantas alucinógenas.** El herbívoro que se come una pasa 25 s alucinando: cambia de color, va al doble de velocidad y ataca a cualquier animal cercano.

## Poderes de Dios

| Poder | Efecto |
|---|---|
| Pacificar (`P`) | Los carnívoros dejan de cazar durante 15 s (recarga de 30 s). |
| Seguidme (`G`) | Durante 25 s todos los animales van hacia Dios. |
| Furia (`T`) | Durante 30 s todos atacan al animal más cercano, más rápido y con más daño. |

Las consecuencias (más herbívoros, menos plantas, desequilibrios posteriores) se producen solas.

## Controles

| Tecla / acción | Función |
|---|---|
| `W` `A` `S` `D` | Mover a Dios |
| `P` / `G` / `T` | Pacificar / Seguidme / Furia |
| `Espacio` | Pausar y reanudar |
| `+` / `-` | Velocidad de simulación (0.5x a 8x) |
| `Q` / `E` o rueda | Zoom |
| `V` | Mostrar conos de percepción |
| `B` | Modo debug (estado, dirección, objetivo) |
| `F` | Seguir al organismo seleccionado |
| `C` | Centrar la cámara en Dios |
| `R` | Reiniciar con un mundo nuevo |
| Clic | Inspeccionar un organismo (edad, vida, energía, genes, descendientes) |

Todos los controles tienen también botón en pantalla, así que funciona en móvil.

## Configuración

Los parámetros principales están en el objeto `C` al principio del script: tamaño del mapa, poblaciones iniciales y máximas, tasa y magnitud de mutación, probabilidad de `defPred`, costes y esperas de reproducción, duración de los poderes y velocidades disponibles. Los rasgos base de cada especie están en `BASE` y los biomas en `BI`.

## Equilibrio de poblaciones

Las poblaciones fluctúan de forma natural. Para evitar que el ecosistema se vacíe, si los carnívoros bajan de un mínimo (`minCarn`) aparecen otros junto a las presas, y si los herbívoros bajan de 20 entran nuevos por el borde del mapa.

## Limitaciones conocidas

- Todo el código está en un único archivo HTML. Funciona, pero no está dividido en módulos.
- No hay obstáculos físicos: los árboles son decoración y el bosque solo reduce visibilidad y velocidad.
- No se puede guardar ni cargar una partida.
- El equilibrio entre especies puede necesitar ajustes en `C` y `BASE` según cuánto tiempo se deje correr.
- Con el mapa grande y 8x puede ir lento en equipos modestos.

## Licencia

Añade aquí la licencia que prefieras (por ejemplo MIT).
