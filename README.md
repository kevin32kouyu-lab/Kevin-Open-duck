# Kevin Open Duck

This repository contains my ROSE5720 MiniDuck / Open Duck project materials. It is organized as a clean public version of the local working folder, without the raw Raspberry Pi home backup, conda environment, caches, compressed archives, or personal system files.

## Repository Layout

```text
.
├── runtime/                 # Open Duck Mini runtime code used on the robot
├── configs/                 # Final tuned robot configuration and IMU offsets
├── models/                  # ONNX walking policies used during tests
└── requirements/            # Conda explicit environment record from the Raspberry Pi setup
```

## Project Summary

The project goal was to assemble and bring up a MiniDuck biped robot, then improve walking stability for the sprint-style course task. The main work included:

- Raspberry Pi environment setup
- I2C and IMU verification
- foot contact switch testing
- servo configuration and motor checks
- soft offset tuning through `duck_config.json`
- walking tests with ONNX policies

The final tuned configuration is stored in `configs/duck_config_tuned.json`.

## Quick Start on Raspberry Pi

The runtime code is under `runtime/`. The original runtime README is kept at `runtime/README.md`.

Typical setup and test commands used during the project were:

```bash
conda activate duck313
cd ~/Open_Duck_Mini_Runtime-2
python scripts/check_motors.py
cd scripts
python find_soft_offsets.py
python v2_rl_walk_mujoco.py --duck_config_path ~/duck_config.json --onnx_model_path ~/kevin.onnx
```

Before walking tests, copy the tuned configuration to the Raspberry Pi home folder if appropriate for the same robot:

```bash
cp configs/duck_config_tuned.json ~/duck_config.json
```

## Models

The `models/` folder contains:

- `demo.onnx` - baseline model used during early integration
- `kevin.onnx` - model used repeatedly during later walking tests

## Notes on Excluded Files

The local folder also contains raw backups and offline installation material. These are intentionally excluded from GitHub because they are large and may contain personal or machine-specific data:

- `pi_backup/`
- `pi_backup.tar.gz`
- `duck_files.tar`
- `offline-packages/`
- `pip_install/`
- `miniconda3/`
- cache/config folders from the Raspberry Pi home directory

## License Status

No formal license has been selected yet. Some runtime code is based on the upstream Open Duck Mini Runtime project, so choose a license only after confirming the upstream licensing terms.
