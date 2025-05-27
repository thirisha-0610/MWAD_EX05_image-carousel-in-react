# MWAD_EX05_image-carousel-in-react
## Date: 25/05/25

## AIM
To create a Image Carousel using React 

## ALGORITHM
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

## PROGRAM
# App.jsx :
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
# ImageCarousle.jsx :
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
# App.css :
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
# main.jsx:
```import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## OUTPUT

![445430748-5b5dbf4f-41f7-4bfb-bb5b-395e0f43463b](https://github.com/user-attachments/assets/782880de-144e-4b7d-9035-06048153155d)

![445430864-5556a811-136d-4c95-84ed-ea8389a2d0b8](https://github.com/user-attachments/assets/cd0e10ca-0a04-42b1-adfc-4f6b1a2f7bad)

![445430904-e56a31dc-da2a-4723-ba78-2dbc768284e2](https://github.com/user-attachments/assets/6d64c6ed-3596-4aa0-aae5-faaeee4a5c43)

![445430904-e56a31dc-da2a-4723-ba78-2dbc768284e2](https://github.com/user-attachments/assets/63788fb5-6dcc-4ed7-a353-fa77de7fbbd1)

![445432368-d982eaf7-6bb0-4c2c-a9c6-edb40e71ec7e](https://github.com/user-attachments/assets/f82a2d8d-9ee5-4518-a82e-227f531882f1)

![445432277-30317390-c1a7-447a-97de-f780dc3d5b7e](https://github.com/user-attachments/assets/54415817-279b-4999-8943-4c88f7318a2b)

![445431605-cc176ab2-c7e8-41b7-8844-5dd33a423e5b](https://github.com/user-attachments/assets/7b527ea5-708a-4b9f-adc6-8f8319054b97)

## RESULT
The program for creating Image Carousel using React is executed successfully.
