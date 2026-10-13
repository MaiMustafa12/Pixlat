# PIXLat – Advanced Image Processor (Console & Windows GUI)

PIXLat is an Object-Oriented Image Processing application developed in C++ as part of **CS213 – Object-Oriented Programming** at the Faculty of Computers and Artificial Intelligence, Cairo University (FCAI-CU).

The project provides a console application and a Windows desktop GUI for loading images, applying filters, combining effects, previewing changes, and saving processed images.

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

- **Document:** [Project Report](https://docs.google.com/document/d/1GVYAtmFMJ5dy2zax3Tx_cwXYbbG5u0RG2bPi3_Vj50Q/edit?tab=t.0#heading=h.g2hmbmrk2d62)
- **Demo Video:**  : https://youtu.be/iVHv5LqoYbk?si=gqbhAl1JoRuJBrd_

## 📜 Educational Use

This project was developed for educational purposes as part of the CS213 Object-Oriented Programming coursework. Refer to the licenses and usage terms of the bundled libraries for their respective conditions.

---

## 🌟 Overview & Interfaces

PIXLat provides two interfaces powered by the image-processing code:

1. **Console Application (`main.cpp`)** – A terminal-based menu for loading images, selecting filters, and saving results.
2. **Windows GUI (`GUI/GUI.cpp`)** – A desktop application with image previews, filter controls, editing history, and save options.

## 🖼️ Supported Image Formats

PIXLat supports the following image formats through its image-loading and saving components:

- **PNG:** `.png`
- **JPEG:** `.jpg`, `.jpeg`
- **Bitmap:** `.bmp`
- **Targa:** `.tga`

Supported formats may depend on the operation and the capabilities of the bundled image libraries.

---

## 🚀 Windows GUI Documentation

### GUI Layout & Features

The Windows GUI features a purple/lavender theme and PIXLat branding.

- **BEFORE and AFTER previews**
  - **BEFORE:** Keeps the original loaded image as a reference.
  - **AFTER:** Displays the current edited result.
  - **Aspect-ratio preservation:** Scales and centers images in the preview areas without intentionally stretching them.

- **Undo and Redo:** Navigate through the editing history.

- **Clear Filters:** Restore the AFTER image to the original image and cancel an unfinished merge overlay.

- **Filter Intensity Slider:** For supported filters, adjust the effect intensity from 0% to 100%.

- **Apply Changes:** Commit the current effect so you can continue editing and combine multiple filters.

- **Filter options dialogs:**
  - **Flip:** Choose horizontal or vertical reflection.
  - **Rotate:** Choose 90°, 180°, or 270° rotation.
  - **Add Frame:** Configure the frame thickness and color.
  - **Resize:** Choose preset scaling or custom dimensions.
  - **Crop:** Specify the region to retain.
  - **Merge:** Select a second image and choose a supported merge mode.
  - **Skew:** Choose a horizontal skew angle.

- **Save Image:** Save the processed image using a supported extension, such as PNG, JPG/JPEG, BMP, or TGA. The application may append an extension when one is omitted.


## 🚀 Building and Running PIXLat

PIXLat is a C++17 image-processing project. The Windows GUI currently uses Windows-specific APIs and libraries. CMake is used to configure and build the Windows GUI.

### 🪟 Windows

#### Prerequisites

- CMake
- MSYS2 with MinGW-w64 UCRT64
- `g++`, `windres`, and `mingw32-make`

#### Build and Run

Open PowerShell in the project root directory, where `CMakeLists.txt` is located.

Configure the project:

```powershell
cmake -S . -B build -G "MinGW Makefiles" -DCMAKE_CXX_COMPILER=C:/msys64/ucrt64/bin/g++.exe -DCMAKE_RC_COMPILER=C:/msys64/ucrt64/bin/windres.exe
```

Build the application:

```powershell
cmake --build build
```

Run the GUI:

```powershell
.\build\PIXLat.exe
```

### 🐧 Linux

#### Prerequisites

Install a C++ compiler, CMake, and the required build tools using your distribution's package manager.

For Ubuntu or Debian:

```bash
sudo apt update
sudo apt install build-essential cmake
```

#### Build and Run the Console Version

If the console source and its dependencies compile successfully on Linux, build it from the project root:

```bash
g++ -std=c++17 main.cpp -o PIXLatProcessor
```

Run it:

```bash
./PIXLatProcessor
```

**GUI support:** The current Windows GUI target is not expected to compile on Linux without adapting its Windows-specific code and replacing or porting the GUI components.

### 🍎 macOS

#### Prerequisites

Install Xcode Command Line Tools and CMake.

```bash
xcode-select --install
```

If Homebrew is installed, CMake can be installed with:

```bash
brew install cmake
```

#### Build and Run the Console Version

If the console source and its dependencies compile successfully on macOS, run:

```bash
clang++ -std=c++17 main.cpp -o PIXLatProcessor
```

Launch it:

```bash
./PIXLatProcessor
```

**GUI support:** The current Windows GUI target requires platform-specific changes before it can be built and run natively on macOS.

### Build Notes

- Run build commands from the directory containing `main.cpp` or `CMakeLists.txt`, as appropriate.
- The commands above describe the current Windows GUI build and the potential console build on Unix-like systems; successful compilation depends on the source code and its dependencies.
- CMake currently configures the Windows GUI target. Linux and macOS GUI support would require a separate, platform-compatible GUI implementation or a cross-platform GUI framework.
- Generated executables and build directories do not need to be included in the source ZIP.

## 🎨 Available Filters

PIXLat implements **18 filter types** in the `Filters/` directory. Darken and Lighten are listed separately below because they provide different brightness effects.

| Filter | Description | GUI Parameter / Control |
|---|---|---|
| **Grayscale** | Converts the image to shades of gray. | One-click filter |
| **Black & White** | Converts the image to a black-and-white effect. | Intensity adjustment, where supported |
| **Darken** | Reduces image brightness. | Intensity adjustment, where supported |
| **Lighten** | Increases image brightness. | Intensity adjustment, where supported |
| **Invert** | Inverts image color values to create a negative effect. | One-click filter |
| **Infrared** | Creates a false-color infrared-style effect. | One-click filter |
| **Add Frame** | Adds a border around the image. | Thickness and color options |
| **Flip** | Reflects the image horizontally or vertically. | Horizontal / Vertical |
| **Rotate** | Rotates the image. | 90°, 180°, or 270° |
| **Blur** | Smooths the image to reduce detail. | One-click filter |
| **Crop** | Keeps a selected rectangular region. | X, Y, Width, and Height |
| **Resize** | Changes the image dimensions. | Preset or custom dimensions |
| **Sunlight** | Adds a warm, sunlight-inspired color effect. | One-click filter |
| **Old TV** | Adds a retro television-style scanline effect. | One-click filter |
| **Purple** | Adds a purple color tint. | One-click filter |
| **Detect Edges** | Highlights boundaries and transitions in the image. | One-click filter |
| **Merge** | Combines two images. | Image selection and merge mode |
| **Skew** | Slants the image horizontally. | Angle selection |
| **Oil Painting** | Creates an oil-painting-inspired effect by grouping nearby colors. | Intensity adjustment, where supported |

---

## 🔀 Merge Filter Options

The Merge filter supports different ways of combining two images.

1. **Resize to Maximum Dimensions**  
   Resizes the images to the maximum width and height required by the selected mode, then combines their corresponding pixels.

2. **Common Area**  
   Combines the top-left overlapping region using the smaller width and height of the two images. For example, images sized `500 × 1000` and `1000 × 500` produce a common region of `500 × 500`.

3. **Drag-to-Overlap (GUI)**  
   Select the drag-to-overlap option and choose the second image through the file picker. Drag the second image inside the AFTER preview to position it. Click **Apply Changes** to confirm the merge, or press **Esc** to cancel.

   The original image defines the output canvas, so any part of the second image outside that canvas is clipped.

The console version supports the first two modes and an X/Y-offset overlay mode.

---

## ✏️ Editing Workflow

- **BEFORE** retains the original image loaded at the beginning of the editing session.
- **AFTER** displays the current result, including committed filters and merges.
- Use the intensity slider for filters that support intensity adjustment.
- Click **Apply Changes** to commit an effect before applying another filter.
- Use **Undo** and **Redo** to navigate through the editing history.
- Use **Clear Filters** to restore the AFTER image to the original and cancel an unfinished merge overlay.
- Use **Open Image** to load a sample image or browse for an image on your computer.
- Save the finished result in a supported format.

---

## 📁 Project Directory Structure

The following tree illustrates the main project organization. The exact filenames and optional build assets should match the current repository.

```text
OOP_Projectt/
├── Filters/
│   ├── Add_frame_filter.cpp
│   ├── Blur_filter.cpp
│   ├── black_and_white_filter.cpp
│   ├── crop_filter.cpp
│   ├── Darken-lighten_filter.cpp
│   ├── detect_image_edges_filter.cpp
│   ├── Flip_filter.cpp
│   ├── Gray_scale_filter.cpp
│   ├── Infrared_filter.cpp
│   ├── Invert_filter.cpp
│   ├── purple_filter.cpp
│   ├── Resize_filter.cpp
│   ├── rotate_filter.cpp
│   ├── sunlight_filter.cpp
│   ├── TV_filter.cpp
│   ├── Merge_filter.cpp
│   ├── Skew_filter.cpp
│   └── Oil_Painting_filter.cpp
├── GUI/
│   └── GUI.cpp
├── Images/
│   └── Sample images
├── Libraries/
│   ├── Image_Class.h
│   ├── stb_image.h
│   └── stb_image_write.h
├── main.cpp
├── PIXLat.rc
├── Start_PIXLat.bat
├── BUILD_WINDOWS_EXE.bat
└── README.md
```

**Note:** The names of the Merge, Skew, and Oil Painting files, as well as the presence of `PIXLat.rc` and the batch files, should be checked against the actual repository before publishing this tree.

---

## 🎨 PIXLat Branding Assets

The Windows GUI uses PIXLat branding assets, including `PIXLat_logo.png` and `PIXLat.ico`, when they are present in the project root and referenced by the application.

Keep the project folder structure intact when extracting the repository so that source files, libraries, resources, and images remain in their expected locations.

---

## ⚡ Performance Notes

- The Windows launcher builds the GUI using the `-O2` compiler optimization option.
- Image loading, saving, and preview conversion may use optimized bitmap operations to reduce processing overhead.
- Cached preview data can reduce repeated work during window repainting.
- Large images may still require additional processing time, particularly for computationally expensive effects such as Blur and Oil Painting.
- Close any running instance of PIXLat before rebuilding because Windows may prevent an executable from being replaced while it is in use.

---

## 📚 Project Purpose

PIXLat was developed to apply Object-Oriented Programming concepts to a practical image-processing application. It brings together image manipulation, file handling, user-interface design, filter development, and editing workflows in a single C++ project.
