
---

# Camera Calibration with Chessboard

This project demonstrates how to perform camera calibration using OpenCV. It uses images of a chessboard pattern to calculate the intrinsic and extrinsic parameters of a camera. These parameters can then be used to correct lens distortion and undistort images taken by the camera.

---

## Features

* **Camera Calibration**: Computes the intrinsic (focal length, optical center) and extrinsic parameters (rotation and translation vectors) of a camera.
* **Chessboard Pattern**: Uses a chessboard pattern to detect corner points for calibration.
* **Distortion Correction**: Corrects radial and tangential distortion in images.
* **Customizable Configuration**: Allows easy configuration of chessboard size, square size, and the image folder path.
* **Undistortion of Test Image**: After calibration, you can undistort a test image.

---

## Requirements

Before you start, ensure you have the following installed:

* **Python 3.x**
* **OpenCV**:

  ```bash
  pip install opencv-python opencv-contrib-python
  ```

---

## Project Structure

```
/Camera_Calibration
    /image1.jpg
    /image2.jpg
    ...
/camerayaml.py  # Main Python script for camera calibration
README.md       # Project documentation (this file)
```

---

## How to Use

### 1. **Prepare Your Images**

Place your chessboard calibration images in a folder, e.g., `Camera_Calibration`. These images should contain clear views of a chessboard pattern, with internal corners visible in the frame. Make sure that you have at least **10 images** for accurate calibration.

### 2. **Configure the Script**

In the `camerayaml.py` script, you can customize the following parameters:

* **`image_directory`**: Path to the folder containing your calibration images. The default is set to `Camera_Calibration`.
* **`chessboard_size`**: The number of internal corners of the chessboard (e.g., `(8, 7)` means 8 columns and 7 rows of internal corners).
* **`square_size`**: Size of each square in the chessboard, in millimeters. This is used for real-world calibration (default: 30mm).

```python
calibrate_camera('Camera_Calibration', chessboard_size=(8, 7), square_size=30)
```

### 3. **Run the Script**

Once your images are in place and the script is configured, run the script:

```bash
python camerayaml.py
```

### 4. **View the Results**

The script will:

* Display the images with detected chessboard corners.
* Print the **camera matrix** and **distortion coefficients** in the terminal.
* Show and save an **undistorted image** (output: `calibresult.png`).

---

## Calibration Output

After running the script, the following results will be printed:

* **Camera Matrix (`mtx`)**: Contains the focal lengths and optical center of the camera.
* **Distortion Coefficients (`dist`)**: Radial and tangential distortion coefficients.
* **Rotation Vectors (`rvecs`)**: The rotation of the camera in 3D space.
* **Translation Vectors (`tvecs`)**: The position of the camera relative to the chessboard.
* The camera parameters are saved as a `.npz` file (e.g., `camera_calibration.npz`) for later use.

### Example Output:

```bash
Camera matrix:
[[1.2345e+03 0.0000e+00 6.0175e+02]
 [0.0000e+00 1.2345e+03 3.4870e+02]
 [0.0000e+00 0.0000e+00 1.0000e+00]]

Distortion coefficients:
[ 2.345e-01 -4.567e-02 -7.845e-05 -1.234e-04  1.234e-02]

Rotation vectors (rvecs):
[[-0.0234  0.1245  0.0365]]

Translation vectors (tvecs):
[[ 12.345  15.678  345.678]]
```

### Undistorted Image:

The script will also save the undistorted version of a test image (`left12.jpg`), which will be output as `calibresult.png`.

---

## Customization

* **Chessboard Size**: The default chessboard size is `(8, 7)`. Adjust the `chessboard_size` parameter for different chessboard dimensions (e.g., `(9, 6)` for a 9x6 grid of internal corners).
* **Square Size**: The default square size is 30mm. If you know the real-world square size in millimeters, change the `square_size` parameter accordingly.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### **Troubleshooting**

1. **No Images Found**:

   * Check if the images are correctly placed in the folder (`Camera_Calibration`) and have the correct file extension (e.g., `.jpg`).
   * Update the `glob.glob()` pattern if you're using a different image format (e.g., `.jpeg`, `.png`).

2. **Chessboard Corners Not Detected**:

   * Make sure the chessboard is visible and not obstructed in the images.
   * Try to take images from different angles and distances to ensure corners are detectable.


