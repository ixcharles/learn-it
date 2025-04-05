
# Media & Camera Integration in React Native

**Introduction**  
This course covers integrating audio, video, and camera functionalities in React Native apps using powerful libraries like **expo-av**, **react-native-vision-camera**, and **expo-image-picker**. You will learn how to efficiently handle media playback, capture images and videos, and optimize media-heavy applications.

## Table of Contents  
1. [Working with Audio & Video](#working-with-audio--video)  
    - [Playing Media with expo-av](#playing-media-with-expo-av)  
    - [Streaming vs. Local Media Playback](#streaming-vs-local-media-playback)  
2. [Advanced Camera Implementation](#advanced-camera-implementation)  
    - [Capturing Photos & Videos with react-native-vision-camera](#capturing-photos--videos-with-react-native-vision-camera)  
    - [Image Selection & Editing with expo-image-picker](#image-selection--editing-with-expo-image-picker)  
3. [Performance & Optimization](#performance--optimization)  
    - [Managing Media Storage and Compression](#managing-media-storage-and-compression)  
    - [Best Practices for Media-heavy Applications](#best-practices-for-media-heavy-applications)  

---

## Working with Audio & Video

### Playing Media with expo-av
**expo-av** provides simple APIs for handling audio and video playback in your React Native apps.

**Example**  
```bash
expo install expo-av
```

```jsx
import { Audio } from 'expo-av';

const AudioPlayer = () => {
  const [sound, setSound] = useState();

  async function playAudio() {
    const { sound } = await Audio.Sound.createAsync(
      require('./assets/audio.mp3')
    );
    setSound(sound);
    await sound.playAsync();
  }

  return (
    <View>
      <Button title="Play Audio" onPress={playAudio} />
    </View>
  );
};
```

### Streaming vs. Local Media Playback
- **Local playback** involves playing media stored locally within the app or device.
- **Streaming** allows you to stream media from a URL, which can be more efficient for large files.

**Example**  
Streaming audio with **expo-av**:  
```jsx
const { sound } = await Audio.Sound.createAsync(
  { uri: 'https://example.com/audio.mp3' }
);
await sound.playAsync();
```

---

## Advanced Camera Implementation

### Capturing Photos & Videos with react-native-vision-camera
**react-native-vision-camera** provides advanced, high-performance camera capabilities for capturing images and videos.

**Example**  
```bash
npm install react-native-vision-camera
```

```jsx
import { Camera } from 'react-native-vision-camera';

const CameraComponent = () => {
  const camera = useRef(null);

  const takePicture = async () => {
    const photo = await camera.current.takePhoto();
    console.log(photo.uri);
  };

  return (
    <Camera
      style={{ flex: 1 }}
      ref={camera}
      device="back"
      isActive={true}
    >
      <Button title="Take Photo" onPress={takePicture} />
    </Camera>
  );
};
```

### Image Selection & Editing with expo-image-picker
**expo-image-picker** allows you to select images or videos from the device's gallery or camera and edit them if needed.

**Example**  
```bash
expo install expo-image-picker
```

```jsx
import * as ImagePicker from 'expo-image-picker';

const PickImage = async () => {
  let result = await ImagePicker.launchImageLibraryAsync({
    mediaTypes: ImagePicker.MediaTypeOptions.Images,
    allowsEditing: true,
    aspect: [4, 3],
    quality: 1,
  });

  if (!result.canceled) {
    console.log(result.assets[0].uri);
  }
};
```

---

## Performance & Optimization

### Managing Media Storage and Compression
For media-heavy apps, it’s essential to handle storage efficiently and compress images/videos before uploading or saving them.

**Example**  
Compressing an image with **expo-image-manipulator**:  
```bash
expo install expo-image-manipulator
```

```jsx
import * as ImageManipulator from 'expo-image-manipulator';

const compressImage = async (uri) => {
  const result = await ImageManipulator.manipulateAsync(uri, [{ resize: { width: 500 } }], { compress: 0.5 });
  console.log(result.uri);
};
```

### Best Practices for Media-heavy Applications
- **Lazy loading**: Load media only when it’s required, e.g., using `react-native-fast-image` for faster image loading.
- **Cache media**: Cache media files to reduce network load.
- **Optimize media quality**: Compress images and videos before uploading or displaying them.

**Example**  
Caching with **react-native-fast-image**:  
```bash
npm install react-native-fast-image
```

```jsx
import FastImage from 'react-native-fast-image';

const CachedImage = () => (
  <FastImage
    style={{ width: 200, height: 200 }}
    source={{ uri: 'https://example.com/image.jpg', priority: FastImage.priority.high }}
  />
);
```

---

## Conclusion

### Key Takeaways  
1. **expo-av** simplifies audio and video playback, supporting both local and streamed media.  
2. **react-native-vision-camera** provides advanced, high-performance capabilities for capturing photos and videos.  
3. **expo-image-picker** allows easy selection and editing of images and videos from the device’s gallery or camera.  
4. Media-heavy applications require performance optimization like media compression, lazy loading, and caching.  
5. Use libraries like **react-native-fast-image** and **expo-image-manipulator** for efficient media handling and storage.

### Practical Exercise  
1. Build an app that records a video using **react-native-vision-camera** and saves it locally.  
2. Implement image selection using **expo-image-picker** and compress the selected image using **expo-image-manipulator**.  
3. Add audio playback functionality with **expo-av** and implement streaming from an external URL.
