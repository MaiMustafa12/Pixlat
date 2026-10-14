# PIXLat – Advanced Image Processor

PIXLat is a C++ image-processing application developed as part of **CS213 – Object-Oriented Programming** at the Faculty of Computers and Artificial Intelligence, Cairo University (FCAI-CU).

The project includes a Windows desktop graphical user interface (GUI) and a console application source file. It provides image-loading and saving functionality, multiple image filters, image merging, and editing controls.

## 👥 Authors & Contributors

### 1. [Malak Khairy](https://github.com/malakkhairy2006)
- **Student ID:** 20251414
- **Assigned Filters:** Black and White, Rotate, Old TV, Oil Painting, Detect Edges

### 2. [Mai Mustafa](https://github.com/MaiMustafa12)
- **Student ID:** 20251443
- **Assigned Filters:** Infrared, Resize, Add Frame, Blur

### 3. [Fatma Alzahraa Aballah](https://github.com/f3tima-abd3llah)
- **Student ID:** 20250462
- **Assigned Filters:** Grayscale, Flip, Merge, Sunlight, Skew

### 4. [Mai Hussain](https://github.com/maihussain825-creator)
- **Student ID:** 20251442
- **Assigned Filters:** Darken / Lighten, Invert, Crop, Purple

## 🎓 Academic Acknowledgments

- **Course:** CS213 – Object-Oriented Programming
- **Institution:** Faculty of Computers and Artificial Intelligence, Cairo University (FCAI-CU)
- **Instructor:** Dr. Mohamed ElRamly

The project uses the provided `Image_Class.h` and the bundled `stb_image.h` and `stb_image_write.h` libraries.

## 🔗 Project Links

- **Project document:** [Open the Project Report](https://docs.google.com/document/d/1GVYAtmFMJ5dy2zax3Tx_cwXYbbG5u0RG2bPi3_Vj50Q/edit?tab=t.0#heading=h.g2hmbmrk2d62)
- **Demo Video:** (https://youtu.be/QACWwfRtDEI)

## 📜 Educational Use

This project was developed for educational purposes as part of the CS213 Object-Oriented Programming coursework. Refer to the licenses and usage terms of the bundled libraries for their respective conditions.

---

## 🌟 Project Overview

PIXLat brings together image processing, file handling, filter development, and graphical user-interface design in a C++ application.

The repository contains two application entry points or components:

1. **Windows GUI (`GUI/GUI.cpp`)** — The graphical desktop application built using the project's CMake configuration.
2. **Console source (`main.cpp`)** — The console application source. Its build instructions and dependencies may differ from those of the Windows GUI.

The current CMake configuration builds the Windows GUI application.

## 🖼️ Supported Image Formats

The bundled image-processing components support the following formats:

- **PNG:** `.png`
- **JPEG:** `.jpg`, `.jpeg`
- **Bitmap:** `.bmp`
- **Targa:** `.tga`

Actual support can depend on the image operation and the bundled library implementation.

---

## 🚀 Windows GUI Documentation

### GUI Layout and Features

The Windows GUI uses PIXLat branding and a purple/lavender visual theme.

- **BEFORE Preview:** Keeps the original loaded image as a reference during editing.
- **AFTER Preview:** Displays the current edited result.
- **Image Preview Scaling:** Displays images within the preview areas while aiming to preserve their aspect ratios.
- **Undo and Redo:** Navigate backward and forward through the editing history.
- **Clear Filters:** Restores the AFTER image to the original image and cancels an unfinished merge overlay.
- **Filter Intensity Slider:** Adjusts the effect strength for supported filters, from 0% to 100%.
- **Apply Changes:** Commits an effect so that additional filters can be applied to the result.
- **Open Image:** Loads an image from the available sample images or from the user's computer.
- **Save Image:** Saves the processed result in a supported image format.

### Filter Options

Depending on the selected filter, the GUI provides options such as:

- **Flip:** Horizontal or vertical reflection.
- **Rotate:** Rotation by 90°, 180°, or 270°.
- **Add Frame:** Frame thickness and color.
- **Resize:** Preset scaling or custom dimensions.
- **Crop:** Specify the image region to retain.
- **Merge:** Select a second image and choose an available merge mode.
- **Skew:** Select a horizontal skew angle.

The available controls may differ between filters.

---

## 🚀 Building and Running PIXLat

The Windows GUI is a C++17 application configured with CMake. Its current implementation uses Windows-specific APIs, so the GUI build instructions below apply to Windows.

### 🪟 Windows

#### Prerequisites

Install and configure:

- CMake
- MSYS2 with the MinGW-w64 UCRT64 toolchain
- `g++`
- `windres`
- `mingw32-make`

The following commands use the default MSYS2 UCRT64 installation path: `C:/msys64/ucrt64/`.

#### 1. Open PowerShell

Open PowerShell in the project root directory, where `CMakeLists.txt` is located.

#### 2. Configure the Project

Run:

```powershell
cmake -S . -B build -G "MinGW Makefiles" -DCMAKE_CXX_COMPILER=C:/msys64/ucrt64/bin/g++.exe -DCMAKE_RC_COMPILER=C:/msys64/ucrt64/bin/windres.exe
```

#### 3. Build the Application

Run:

```powershell
cmake --build build
```

Wait until the build completes successfully.

#### 4. Run PIXLat

Run:

```powershell
.\PIXLat.exe
```

The current CMake configuration places `PIXLat.exe` in the **project root directory**, not inside the `build` directory.

You can also launch the application by double-clicking `PIXLat.exe` in File Explorer.

#### 5. Rebuild After Source Changes

After modifying the source code, run:

```powershell
cmake --build build
```

Then launch the updated application using:

```powershell
.\PIXLat.exe
```

Close any running instance of PIXLat before rebuilding if Windows prevents the executable from being replaced.

### 🐧 Linux and 🍎 macOS

The current CMake configuration targets the Windows GUI and uses Windows-specific APIs. Native Linux and macOS GUI builds are not provided by the current configuration.

The `main.cpp` console application may require a separate build configuration and compatible dependencies. The following commands are examples only and have **not been verified** for this repository.

**Ubuntu/Debian prerequisites:**

```bash
sudo apt update
sudo apt install build-essential cmake
```

**Example Linux console build:**

```bash
g++ -std=c++17 main.cpp -o PIXLatProcessor
```

Run it with:

```bash
./PIXLatProcessor
```

**macOS prerequisites:** Install Xcode Command Line Tools and CMake.

```bash
xcode-select --install
```

If Homebrew is installed:

```bash
brew install cmake
```

**Example macOS console build:**

```bash
clang++ -std=c++17 main.cpp -o PIXLatProcessor
```

Run it with:

```bash
./PIXLatProcessor
```

Successful console builds depend on the source code, compiler compatibility, and required libraries. The Windows GUI requires platform-specific adaptations before it can be built natively on Linux or macOS.

---

## 🎨 Available Filters

PIXLat contains **18 filter implementation files** in the `Filters/` directory. The Darken/Lighten filter file provides two brightness effects, so they are listed separately in the table below.

| Filter | Description |
|---|---|
| **Grayscale** | Converts the image to shades of gray. |
| **Black and White** | Converts the image to a black-and-white effect. |
| **Darken** | Reduces image brightness. |
| **Lighten** | Increases image brightness. |
| **Invert** | Inverts image color values to create a negative effect. |
| **Infrared** | Creates an infrared-style false-color effect. |
| **Add Frame** | Adds a border around the image. |
| **Flip** | Reflects the image horizontally or vertically. |
| **Rotate** | Rotates the image by a supported angle. |
| **Blur** | Smooths the image and reduces detail. |
| **Crop** | Keeps a selected rectangular region. |
| **Resize** | Changes the image dimensions. |
| **Sunlight** | Adds a sunlight-inspired color effect. |
| **Old TV** | Creates a retro television-style effect. |
| **Purple** | Applies a purple color effect. |
| **Detect Edges** | Highlights boundaries and transitions in the image. |
| **Merge** | Combines two images using an available merge mode. |
| **Skew** | Slants the image. |
| **Oil Painting** | Creates an oil-painting-inspired effect. |

Filter parameters and intensity controls depend on the implementation of each filter.

---

## 🔀 Merge Filter Options

The Merge filter combines two images. The available behavior depends on the selected merge mode.

### 1. Resize to Maximum Dimensions

Resizes the images according to the selected mode before combining them. The exact resizing behavior depends on the implementation.

### 2. Common Area

Combines the overlapping top-left region using the smaller width and height of the two images.

For example, images sized `500 × 1000` and `1000 × 500` have a common region of `500 × 500`.

### 3. Drag-to-Overlap (GUI)

If this option is available in the current GUI build:

1. Select the drag-to-overlap merge option.
2. Choose the second image through the file picker.
3. Drag the second image within the AFTER preview to position it.
4. Click **Apply Changes** to commit the merge, or press **Esc** to cancel if cancellation is supported by the current implementation.

The original image defines the output canvas, so parts of the second image outside that canvas may be clipped.

---

## ✏️ Editing Workflow

A typical editing session follows these steps:

1. Open a sample image or select an image from your computer.
2. Use the BEFORE preview as a reference for the original image.
3. Select a filter and configure its available options.
4. Adjust the intensity slider if the selected filter supports it.
5. Click **Apply Changes** to commit the effect.
6. Apply additional filters to continue editing.
7. Use **Undo** and **Redo** to navigate the editing history.
8. Use **Clear Filters** to restore the AFTER image to the original and cancel an unfinished merge operation.
9. Save the finished image in a supported format.

The exact behavior of individual controls depends on the current GUI implementation.

---

## 📁 Project Directory Structure

The following tree represents the main project files and folders in the repository.

```text
OOP_Projectt/
├── Filters/
│   ├── Add_frame_filter.cpp
│   ├── Blur_filter.cpp
│   ├── Darken-lighten_filter.cpp
│   ├── Flip_filter.cpp
│   ├── Gray_scale_filter.cpp
│   ├── Infrared_filter.cpp
│   ├── Invert_filter.cpp
│   ├── Oil_painting_filter.cpp
│   ├── Resize_filter.cpp
│   ├── TV_filter.cpp
│   ├── black_and_white_filter.cpp
│   ├── crop_filter.cpp
│   ├── detect_image_edges_filter.cpp
│   ├── merge_filter.cpp
│   ├── purple_filter.cpp
│   ├── rotate_filter.cpp
│   ├── skew_filter.cpp
│   └── sunlight_filter.cpp
├── GUI/
│   └── GUI.cpp
├── Images/
│   └── Sample images
├── Libraries/
│   ├── Image_Class.h
│   ├── stb_image.h
│   └── stb_image_write.h
├── CMakeLists.txt
├── PIXLat.ico
├── PIXLat.rc
├── PIXLat_icon.png
├── PIXLat_logo.png
├── README.md
└── main.cpp
```

### Main Components

- **`Filters/`** — Contains the 18 filter implementation files.
- **`GUI/`** — Contains the Windows GUI source file.
- **`Images/`** — Contains sample images for testing the application.
- **`Libraries/`** — Contains the image class and bundled image-loading and image-saving libraries.
- **`CMakeLists.txt`** — Configures the current Windows GUI build.
- **`PIXLat.rc`** — Windows resource file used by the build.
- **`PIXLat.ico`, `PIXLat_icon.png`, and `PIXLat_logo.png`** — Project branding assets.
- **`main.cpp`** — Console application source file.
- **`README.md`** — Project documentation and build instructions.

---

## 🎨 PIXLat Branding Assets

PIXLat includes branding assets such as `PIXLat_logo.png`, `PIXLat_icon.png`, and `PIXLat.ico`.

The Windows resource file `PIXLat.rc` is included in the CMake build. Keep the required source files, libraries, resource files, and images in their expected relative locations when building the project.

---

## 📦 Source and Submission Notes

- Keep `CMakeLists.txt` and the source folders in the submitted project so the application can be rebuilt.
- Include the image samples and bundled libraries required by the application.
- Generated executables and build directories are build artifacts and should not be included in a source-only submission if the assignment instructions prohibit them.
- The current build instructions assume that MSYS2 is installed at `C:/msys64/`. Adjust the compiler paths if your installation uses a different location.
- The demonstration video link should be added once the final video has been uploaded.

---

## 📚 Project Purpose

PIXLat was developed to apply Object-Oriented Programming concepts to a practical image-processing application. It brings together image manipulation, file handling, filter development, and user-interface design in a single C++ project.
