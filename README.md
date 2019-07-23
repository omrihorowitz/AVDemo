# AVDemo

Demo projects for iOS Audio & Video development.

### UIImagePicker Video Recorder

Demonstrates how to create a custom UI for the camera variant of the UIImagePickerController and how to programmatically control video recording.

### AVCam

AVCam demonstrates usage of AV Foundation capture API for recording movies, taking still images, and switching cameras. It runs only on an actual device, either an iPad or iPhone, and cannot be run in the simulator.

### VideoSnake

This sample demonstrates temporal synchronization of video with motion data from the accelerometer and gyroscope. It also includes a class which illustrates best practices for using the AVAssetWriter API to record movies.  This is based on the VideoSnake demo presented at WWDC 2012, Session 520, "What's new in Camera Capture".

### AVCamManualUsingtheManualCaptureAPI

AVCamManual adds manual controls for focus, exposure, and white balance to the AVCam sample application.

### AVCaptureToAudioUnit

AVCaptureAudioDataOutput To AudioUnit iOS

AVCaptureToAudioUnit for iOS demonstrates how to use the CMSampleBufferRefs vended by AVFoundation's capture AVCaptureAudioDataOutput object with various CoreAudio APIs. The application uses a AVCaptureSession with a AVCaptureAudioDataOutput to capture audio from the default input, applies an effect to that audio using a simple delay effect AudioUnit and writes the modified audio to a file using the CoreAudio ExtAudioFile API. It also demonstrates using and AUGraph containing an AUConverter to convert the AVCaptureAudioDataOutput provided data format into a suitable format for the delay effect.

The CaptureSessionController class is responsible for setting up and running the AVCaptureSession and for passing the captured audio buffers to the CoreAudio AudioUnit and ExtAudioFile. The setupCaptureSession method is responsible for setting up the AVCaptureSession, while the captureOutput:didOutputSampleBuffer:fromConnection: passes the captured audio data through the AudioUnit via AudioUnitRender into the file using ExtAudioFileWriteAsync when recording.

CoreMedia provides two convenience methods to easily use the captured audio data with CoreAudio APIs. The CMSampleBufferGetAudioBufferListWithRetainedBlockBuffer API fills in an AudioBufferList with the data from the CMSampleBuffer, and returns a CMBlockBuffer which references (and manages the lifetime of) the data in that AudioBufferList. This AudioBufferList can be used directly by AudioUnits and other CoreAudio objects. The CMSampleBufferGetNumSamples API returns the number of frames of audio contained within the sample buffer, a value that can also be passed directly to CoreAudio APIs.

Because CoreAudio AudioUnits process audio data using a "pull" model, but the AVCaptureAudioDataOutput object "pushes" audio sample buffers onto a client in real time, the captured buffers must be sent though the AudioUnit via an AudioUnit render callback which requests input audio data each time AudioUnitRender is called to retrieve output audio data. Every time captureOutput:didOutputSampleBuffer:fromConnection: receives a new sample buffer, it gets and stores the buffer as the Input AudioBufferList (so that the render callback can access it), and then immediately calls AudioUnitRender which synchronously pulls the stored input buffer list through the AudioUnit via the render callback. The output data is available in the output AudioBufferList passed to AudioUnitRender. This output buffer list may be passed to ExtAudioFile for final format conversion and writing to the file.

### AVBasicVideoOutput

The AVBasicVideoOutput This sample shows how to perform **real-time video processing** using `AVPlayerItemVideoOutput` and how to optimally display processed video frames on screen using CAEAGLLayer and CADisplayLink. It uses simple math to adjust the luma and chroma values of pixels in every video frame in real time.

An AVPlayerItemVideoOutput object vends CVPixelBuffers in real-time. To drive the AVPlayerItemVideoOutput we need to use a fixed rate, **hardware synchronized service** like CADisplayLink or GLKitViewController. These services send a callback to the application at the vertical sync frequency. Through these callbacks we can query AVPlayerItemVideoOutput for a new pixel buffer (if available) for the next vertical sync. This pixel buffer is then processed for any video effect we wish to apply and rendered to screen on a view backed by a CAEAGLLayer.

### CapturePause sample

iPhone CapturePause sample from http://www.gdcl.co.uk//2013/04/03/Fix-CapturePause.html

### GLCameraRipple

This sample demonstrates how to use the AVFoundation framework to capture YUV
frames from the camera and process them using shaders in OpenGL ES 2.0.
CVOpenGLESTextureCache, which is new to iOS 5.0, is used to provide optimal
performance when using the AVCaptureOutput as an OpenGL texture. In addition, a
ripple effect is applied by modifying the texture coordinates of a densely
tessellated quad.

### RosyWriter

Capture, process, preview, and save video using AV Foundation using various processing pipelines.

This sample demonstrates how to use AVCaptureVideoDataOutput to bring frames from the camera into various processing pipelines, including CPU-based, OpenGL (i.e. on the GPU), CoreImage filters, and OpenCV. It also demonstrates best practices for writing the processed output of these pipelines to a movie file using AVAssetWriter.

The project includes a different target for each of the different processing pipelines.

### AVSimpleEditoriOS

A simple AV Foundation based movie editing application for iOS.

### AVCustomEdit

AVCustomEdit is a simple AVFoundation based movie editing application demonstrating custom compositing to add transitions. The sample demonstrates the use of custom compositors to add transitions to an AVMutableComposition. It implements the AVVideoCompositing and AVVideoCompositionInstruction protocols to have access to individual source frames, which are then be rendered using OpenGL off screen rendering.

Note: The sample has been developed for iPhones 4S and above/iPods with 4-inch display and iPads. These developed transitions are not supported on simulator.

### AVLoupe

This sample demonstrates how to use multiple synchronized AVPlayerLayer instances, associated with a single AVPlayer, to efficiently produce non-trivial presentation of timed visual media. Using just one AVPlayer this sample demonstrates how you can display the same video in multiple AVPlayerLayers simultaneously. With minimal code you can create very customized and creative forms of video display. As an example, this sample demonstrates an interactive loupe, or magnifying glass, for video playback. This is similar to features that you might have used in iPhoto and Aperture.

This sample was explored in the WWDC 2012 session 517: Real-Time Media Effects and Processing during Playback. <https://developer.apple.com/library/ios/samplecode/AVLoupe/>

### VideoEditing-Final2

From [AVFoundation Tutorial: Adding Overlays and Animations to Videos](http://www.raywenderlich.com/30200/avfoundation-tutorial-adding-overlays-and-animations-to-videos)

This AVFoundation tutorial will build upon that by teaching all you budding video editors how to add the following effects to your videos:

- Colored borders with custom sizes.
- Multiple overlays.
- Text for subtitles or captions.
- Tilt effects.
- Twinkle, rotate, and fade animation effects!

### AVCompositionDebugVieweriOS

This sample application has an AVCompositionDebugView which presents a visual description of the underlying AVComposition, AVVideoComposition and AVAudioMix objects which form the composition made using two clips, adding a cross fade transition in between and audio ramps to the two audio tracks. The visualization provided by the sample can be used as a debugging tool to discover issues with an incorrect composition/video composition. For example: a break in video composition would render black frames to screen, which can easily be detected using the visualization in the sample.

### Frame Re-ordering Video Encoding

From [Frame Re-ordering Support in iOS Video Encoding](http://www.gdcl.co.uk/2014/04/22/Frame-Reordering.html)

### AVMovieExporter

This universal sample application reads movie files from the asset and media library then
exports them to a new media file with user defined settings. The user can adjust the exported file
in the following ways:

- Export presets can be chosen which influence the size and quality of the output.
- The file type can be changed.
- Tracks and existing metadata can be inspected.
- Metadata can be inserted or deleted.

### AudioTapProcessor

Sample application that uses the MTAudioProcessingTap in combination with AV Foundation to visualize audio samples as well as applying a Core Audio audio unit effect (Bandpass Filter) to the audio data.

*Note:* The sample requires at least one video asset in the Asset Library (Camera Roll) to use as the source media. It will automatically select the first one it finds.

### Sample Photos App

**Example app using Photos framework** From WWDC 2014

A basic Photos-like app which introduces the Photos framework.
- List albums, folders and moments
- Display the contents of the moments, or a single album
- Display the content of a single photo or video (and allow playback in the case of a video)
- Allow the following actions:
	* simple single-click edit of a photo
	* creating an album and adding assets to it
	* re-ordering of assets in an album
	* removing assets from an album
	* deleting assets and albums
	* (un)hiding an asset from moments
	* favoriting an asset

### CIFunHouse

**Core Image Filters with Photos and Video for iOS**

The CIFunHouse project shows how to apply Core Image built in and custom CIFilters to photos and video.
