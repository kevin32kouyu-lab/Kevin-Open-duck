# Models

This folder contains ONNX walking policies used during physical robot tests.

- `demo.onnx`: baseline model used during early integration.
- `kevin.onnx`: model used repeatedly in later walking tests.

Example:

```bash
cd runtime/scripts
python v2_rl_walk_mujoco.py --duck_config_path ~/duck_config.json --onnx_model_path ../../models/kevin.onnx
```
