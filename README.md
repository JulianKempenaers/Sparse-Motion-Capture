# SparseMotionCapture

A real-time video capture tool that stores only moving pixels in sparse matrix format to drastically reduce experimental data file sizes.
- Built in **Python**
- Works with **Picam2 camera** on [**Raspberry Pi**](https://www.raspberrypi.com/) computers.

## Summary
In home surveillance or research setups with a fixed camera, most footage consists of a static background with occasional movement. This tool saves only the moving parts, enabling storage of hours of footage without wasting space on empty frames. This tool runs live in the backgorund while footage is recorded, so there is no need to manually sort through footage afterwards.

## Technical details
### [SparseMotionCapture.py](SparseMotionCapture.py):
- Captures video at max 5 frames per second (fps).
- Periodically saves full key frames for reference 
- **Detects motion** by comparing each new frame to the latest key frame using **frame differencing, thresholding,** and **morphological operations** (erosion, dilation).
- Saves only the **detected motion** regions as sparse matrices (BSR format) compressed in.npz files.
- Dynamically manages frame capture rate based on **queue size** to avoid overload and frame drops.
- **Processes and batch-saves frames in real-time** during video capture.
- Designed for experimental setups or surveillance cameras with a static background and fixed camera.

### [NpzToMp4.py](NpzToMp4.py):
- Converts the compressed .npz files back into .mp4 videos for playback and analysis.
- Resulting .mp4 files are larger in size. For long-term storage, keeping data in .npz format is recommended. Use .mp4 primarily for temporary playback or review.

### License
[MIT License](LICENSE)
