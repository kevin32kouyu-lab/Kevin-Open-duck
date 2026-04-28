# Debug Notes

These notes summarize the useful records found in the copied Raspberry Pi home folder. The raw backup is not included in this repository.

## Main Debug Timeline

1. Adjusted Raspberry Pi network / Wi-Fi power saving settings and used `raspi-config`.
2. Activated the `duck313` conda environment.
3. Tested foot contact switches with `python feet_contacts.py`.
4. Enabled / checked I2C access using `sudo usermod -aG i2c bdxv2` and `i2cdetect -y 1`.
5. Calibrated the IMU with `python calibrate_imu.py` and copied `imu_calib_data.pkl` into the runtime folder.
6. Checked and configured servos with `python scripts/check_motors.py` and `python configure_all_motors.py`.
7. Tuned standing posture with `python find_soft_offsets.py` and repeated edits to `~/duck_config.json`.
8. Repeated walking tests with `demo.onnx`, `BEST_WALK_ONNX_2.onnx`, and `kevin.onnx`.

## Final Tuned Config Highlights

- `imu_upside_down`: `true`
- `phase_frequency_factor_offset`: `0.0`
- optional expression devices disabled during walking debug
- non-zero offsets used for:
  - `left_hip_yaw`: `-0.1`
  - `left_hip_roll`: `-0.01`
  - `neck_pitch`: `0.03`
  - `head_yaw`: `0.2`
  - `head_roll`: `0.01`
  - `right_hip_roll`: `0.1`

## IMU Calibration Offsets

The runtime calibration file contained these values and they are also saved as JSON in `configs/imu_calibration_offsets.json`.
