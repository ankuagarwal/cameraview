# CameraView

* This repo is forked from https://github.com/google/cameraview

CameraView aims to help Android developers easily integrate Camera features.

Requires API Level 23. The library uses Camera1 and Camera2 both. 

| API Level | Camera API | Preview View | Fallback Camera API | Fallback Preview View |
|:---------:|------------|--------------|---------------------|-----------------------|                
| 23+       | Camera2    | TextureView  | Camera1             | SurfaceView           |

The library tries to use Camera2, but in case the camera device used legacy hardware (INFO_SUPPORTED_HARDWARE_LEVEL_LEGACY),
then it fallbacks to Camera1.

## Features

- Camera preview by placing it in a layout XML (and calling the start method)
- Configuration by attributes
  - Aspect ratio (app:aspectRatio)
  - Auto-focus (app:autoFocus)
  - Flash (app:flash)
  - Front/Back (app:facing)
- If layout_height is match_parent, then its displays camera is fullscreen mode

## Usage

```xml
<com.google.android.cameraview.CameraView
    android:id="@+id/camera"
    android:layout_width="match_parent"
    android:layout_height="wrap_content" 
    android:keepScreenOn="true"
    android:adjustViewBounds="true"
    app:autoFocus="true"
    app:aspectRatio="4:3"
    app:facing="back"
    app:flash="auto"/>
```

```java
    @Override
    protected void onResume() {
        super.onResume();
        mCameraView.start();
    }

    @Override
    protected void onPause() {
        mCameraView.stop();
        super.onPause();
    }
```

You can see a complete usage in the demo app.

## Contribution

See [CONTRIBUTING.md](/CONTRIBUTING.md).
