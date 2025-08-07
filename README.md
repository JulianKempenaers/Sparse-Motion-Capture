# SparseMotionCapture

A real-time video capture tool that stores only moving pixels in sparse matrix format to drastically reduce experimental data file sizes.
- Built in **Python**
- Works with **Picam2 camera** on [**Raspberry Pi**](https://www.raspberrypi.com/) computers.

## Summary
In research or home surveillance setups  with a fixed camera, most footage consists of a static background with occasional movement. This tool saves only the moving parts, enabling storage of hours of footage without wasting space on empty frames. This tool runs live in the backgorund while footage is recorded, so there is no need to manually sort through footage afterwards. Full key frames are saved periodically, allowing for accurate reconstruction of complete frames—even though most pixels are discarded in the compressed format.

<p align="center">
  <img src="https://github.com/JulianKempenaers/Sparse-Motion-Capture/blob/main/overlay_demonstration.gif?raw=true" width="700"/>
</p>

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


<p align="center">
  <img src="https://github.com/JulianKempenaers/Sparse-Motion-Capture/blob/main/side_by_side.gif?raw=true" width="700"/>
</p>


### License
[MIT License](LICENSE)
