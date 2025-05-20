# EX-05 : IMAGE CAROUSEL
## DATE : 20.05.2025

## AIM :
To create a Image Carousel using React 

## ALGORITHM :
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM :

### App.jsx :
```
import React from 'react';
import ImageCarousel from './ImageCarousel';
import './App.css';

import greatWall from './assets/greatwall.jpg';
import christ from './assets/christ.jpg';
import machuPicchu from './assets/machu.jpg';
import chichenItza from './assets/chichen.jpg';
import colosseum from './assets/colosseum.jpg';
import petra from './assets/petra.jpg';
import tajMahal from './assets/tajmahal.jpg';

const wonders = [
  { title: 'Great Wall of China', url: greatWall },
  { title: 'Christ the Redeemer, Brazil', url: christ },
  { title: 'Machu Picchu, Peru', url: machuPicchu },
  { title: 'Chichen Itza, Mexico', url: chichenItza },
  { title: 'Roman Colosseum, Italy', url: colosseum },
  { title: 'Petra, Jordan', url: petra },
  { title: 'Taj Mahal, India', url: tajMahal },
];

const App = () => (
  <div>
    <h2 style={{ textAlign: 'center', marginTop: '20px' }}>
      🏛️ 7 Wonders of the World Carousel
    </h2>
    <ImageCarousel images={wonders} />
    <footer className="footer">
      <div className="footer-content">
        <p>Created By: <strong>NARRA RAMYA</strong></p>
        <p>Reg No: <strong>212223040128</strong></p>
      </div>
    </footer>
  </div>
);

export default App;

```

### ImageCarousle.jsx :
```
import React, { useState, useEffect } from 'react';

const ImageCarousel = ({ images }) => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prev) => (prev + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  }, [images.length]);

  return (
    <div style={styles.carousel}>
      <div style={styles.imageContainer}>
        <img
          src={images[currentIndex].url}
          alt={images[currentIndex].title}
          style={styles.image}
        />
      </div>
      <h3>{images[currentIndex].title}</h3>
      <div style={styles.buttons}>
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
  );
};

const styles = {
  carousel: {
    width: '90%',
    maxWidth: '700px',
    margin: '40px auto',
    textAlign: 'center',
    backgroundColor: '#f4f4f4',
    padding: '20px',
    borderRadius: '12px',
    boxShadow: '0 0 10px rgba(0,0,0,0.1)',
  },
  imageContainer: {
    display: 'flex',
    justifyContent: 'center',
    alignItems: 'center',
    height: '400px',
    backgroundColor: '#fff',
    marginBottom: '10px',
  },
  image: {
    maxWidth: '100%',
    maxHeight: '100%',
    objectFit: 'contain',
    borderRadius: '8px',
  },
  buttons: {
    marginTop: '10px',
    display: 'flex',
    justifyContent: 'center',
    gap: '10px',
  },
};

export default ImageCarousel;

```

### App.css :
```
.App {
  text-align: center;
}

footer.footer {
  background-color: #f8f9fa;
  border-top: 1px solid #e9ecef;
  margin-top: 30px;
  padding: 20px;
  width: 100%;
  text-align: center;
}

.footer-content {
  max-width: 600px;
  margin: 0 auto;
  font-size: 16px;
  color: #333;
}
```

### main.jsx :
```
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## OUTPUT :
![image](https://github.com/user-attachments/assets/5b5dbf4f-41f7-4bfb-bb5b-395e0f43463b)
![image](https://github.com/user-attachments/assets/97fa5079-4b2b-47d8-b5a3-c463acab6ad6)
![image](https://github.com/user-attachments/assets/5556a811-136d-4c95-84ed-ea8389a2d0b8)
![image](https://github.com/user-attachments/assets/e56a31dc-da2a-4723-ba78-2dbc768284e2)
![image](https://github.com/user-attachments/assets/8a8558cb-618a-47a3-b903-fbdc5bd93e78)
![image](https://github.com/user-attachments/assets/316e6815-8686-43f5-aff9-b318470ad76c)
![image](https://github.com/user-attachments/assets/cc176ab2-c7e8-41b7-8844-5dd33a423e5b)









## RESULT :
The program for creating Image Carousel using React is executed successfully.
