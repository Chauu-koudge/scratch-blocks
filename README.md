# Venago Blocks

The block library of the Venago block-coding editor (a fork of OpenBlock Blocks / Scratch
Blocks, package name `openblock-blocks`): the Blockly-based block rendering plus the
Arduino and MicroPython code generators.

## What is new in this version

- Updates to the Arduino generators (`generators/arduino/arduino.js`).
- Build and test page updates (`webpack.config.js`, `tests/custom_procedure_playground.html`).

The precompiled bundles used by the editor (`*_compressed.js`) are included. Rebuilding them
needs Python 2 (Closure Compiler), so newer generators are added at runtime by the editor
(see scratch-gui `src/lib/*-generators.js`).

## Run the whole Venago editor locally

Venago is made of four projects that sit next to each other in one folder:

| Folder | Repository | What it is |
|---|---|---|
| `venago-gui` | [scratch-gui](https://github.com/Chauu-koudge/scratch-gui) | The editor (React / Scratch GUI) |
| `venago-vm` | [scratch-vm](https://github.com/Chauu-koudge/-scratch-vm) | Blocks, boards, sensors, runtime |
| `venago-blocks` | [scratch-blocks](https://github.com/Chauu-koudge/scratch-blocks) | Blockly blocks and code generators |
| `venago-link` | [scratch-link](https://github.com/Chauu-koudge/scratch-link) | Serial / Bluetooth connection and upload service |

```
git clone https://github.com/Chauu-koudge/scratch-gui.git venago-gui
git clone https://github.com/Chauu-koudge/-scratch-vm.git venago-vm
git clone https://github.com/Chauu-koudge/scratch-blocks.git venago-blocks
git clone https://github.com/Chauu-koudge/scratch-link.git venago-link
```

Install dependencies in each folder (`npm install`), then in two terminals:

```
cd venago-link && npm start
cd venago-gui && set NODE_OPTIONS=--openssl-legacy-provider && npx webpack-dev-server --host 127.0.0.1 --port 8601
```

Open http://127.0.0.1:8601
