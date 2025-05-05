Camera Calibration with Chessboard
This project demonstrates how to perform camera calibration using OpenCV. It uses images of a chessboard pattern to find the intrinsic and extrinsic parameters of the camera, such as the camera matrix and distortion coefficients. The script is flexible and can handle different chessboard sizes and square dimensions.

Features
Camera Calibration: Uses chessboard images to compute camera parameters.

Chessboard Pattern: Detects the 2D image points from the chessboard corners.

Undistortion: Corrects lens distortion using the camera parameters.

Flexible Configuration: Allows customization of chessboard dimensions, square size, and image folder path.

Requirements
Before you start, ensure you have the following installed:

Python 3.x

OpenCV: Install OpenCV via pip:

bash
Copy
pip install opencv-python opencv-contrib-python
Project Structure
bash
Copy
/Camera_Calibration
    /image1.jpg
    /image2.jpg
    ...
/camerayaml.py  # Main Python script for camera calibration
README.md       # Project documentation (this file)
How to Use
1. Prepare Your Images
Place your chessboard calibration images in a folder (e.g., Camera_Calibration). These images should contain a clear view of a chessboard pattern with the internal corners visible.

2. Configure the Script
The script expects .jpg files in the Camera_Calibration folder. Ensure that your images have the .jpg extension, or modify the script to match your image format.

If your chessboard has different dimensions (e.g., 9x6 internal corners), you can adjust the chessboard_size parameter when calling the calibration function.

You can also adjust the square size to match your real-world chessboard measurements (in millimeters).

3. Run the Script
Once the images are in place and the script is configured, run the calibration script as follows:

bash
Copy
python camerayaml.py
4. View the Results
The script will:

Display the images with detected corners.

Print the camera matrix and distortion coefficients in the terminal.

Show and save an undistorted image (with the filename calibresult.png).

Example Usage
The script uses the following parameters:

python
Copy
calibrate_camera('Camera_Calibration', chessboard_size=(8, 7), square_size=30)
Where:

Camera_Calibration is the directory where your images are located.

chessboard_size=(8, 7) represents a chessboard with 8 columns and 7 rows of internal corners (adjust as needed).

square_size=30 is the size of each square in millimeters (adjust this to match your chessboard's square size).

Calibration Output
Camera Matrix: A 3x3 matrix containing the focal lengths and optical center.

Distortion Coefficients: Parameters that describe the lens distortion.

Rotation and Translation Vectors: Camera's position and orientation relative to the world coordinate system.

Undistorted Image: An image with corrected lens distortion.

The calibration results are saved to a .npz file (e.g., camera_calibration.npz) for future use.

Notes
The calibration works best with multiple images taken from different angles and distances to provide a better estimate of the camera parameters.

The chessboard must be flat and visible in the image to get accurate corner detection.

The undistorted image will be cropped to remove any unwanted borders.

License
This project is licensed under the MIT License – see the LICENSE file for details.
