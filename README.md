# purescript-hylograph-simulation-halogen

Halogen integration for Hylograph force simulations.

## Overview

Provides utilities for integrating Hylograph force simulations with Halogen applications, including event emitters that work with Halogen's subscription system.

## Installation

```bash
spago install hylograph-simulation-halogen
```

## Usage

```purescript
import Hylograph.ForceEngine.Halogen (toHalogenEmitter)

handleAction Initialize = do
  { handle, events } <- liftEffect $ runSimulation config
  halogenEmitter <- liftEffect $ toHalogenEmitter events
  void $ H.subscribe $ halogenEmitter <#> SimEvent

handleAction (SimEvent (Tick { alpha })) =
  H.modify_ _ { alpha = alpha }
```

## Modules

- `Hylograph.ForceEngine.Halogen` - Halogen emitter adapter

## Part of Hylograph

- **hylograph-simulation-halogen** - Halogen integration (this package)
- **hylograph-simulation** - Core simulation API
- **hylograph-d3-kernel** - D3 physics engine

## License

MIT
