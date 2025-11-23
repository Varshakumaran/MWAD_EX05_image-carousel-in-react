# MWAD_EX05_image-carousel-in-react
## Date: 23-11-2025

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
```
import React, { useState, useEffect } from "react";

const Carousel = ({ images }) => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  }, [images.length]);

  return (
    <div style={styles.container}>
      <img
        src={images[currentIndex]}
        alt={`Slide ${currentIndex}`}
        style={styles.image}
      />
      <button onClick={prevImage} style={styles.buttonLeft}>❮</button>
      <button onClick={nextImage} style={styles.buttonRight}>❯</button>
    </div>
  );
};

const styles = {
  container: {
    position: "relative",
    width: "800px",
    height: "500px",
    overflow: "hidden",
    borderRadius: "20px",
    boxShadow: "0 8px 20px rgba(0, 0, 0, 0.3)",
    margin: "0 auto", // center horizontally
  },
  image: {
    width: "100%",
    height: "100%",
    objectFit: "cover",
    borderRadius: "20px",
  },
  buttonLeft: {
    position: "absolute",
    top: "50%",
    left: "20px",
    transform: "translateY(-50%)",
    background: "rgba(0,0,0,0.5)",
    color: "white",
    border: "none",
    padding: "15px 20px",
    borderRadius: "50%",
    cursor: "pointer",
    fontSize: "24px",
  },
  buttonRight: {
    position: "absolute",
    top: "50%",
    right: "20px",
    transform: "translateY(-50%)",
    background: "rgba(0,0,0,0.5)",
    color: "white",
    border: "none",
    padding: "15px 20px",
    borderRadius: "50%",
    cursor: "pointer",
    fontSize: "24px",
  },
};

export default Carousel;
```
```
import React from "react";
import Carousel from "./carousel";

function App() {
  const images = [
     "4.jpeg",
    "5.jpeg",
    "6.jpeg"
  ];

  return (
    <div style={styles.appContainer}>
      <div style={styles.content}>
        <h1 style={styles.title}>React Image Carousel</h1>
        <Carousel images={images} />
      </div>
    </div>
  );
}

const styles = {
  appContainer: {
    display: "flex",
    alignItems: "center",
    height: "100vh", 
    backgroundColor: "#f2f2f2",
  },
  content: {
    textAlign: "center",
  },
  title: {
    fontSize: "32px",
    color: "#333",
    fontFamily: "Arial, sans-serif",
  },
};

export default App;
```

## OUTPUT

<img width="1030" height="595" alt="image" src="https://github.com/user-attachments/assets/143f51ad-2748-48fd-9b5e-7365cf8b8346" />

<img width="1028" height="581" alt="image" src="https://github.com/user-attachments/assets/fc929957-9b3a-4269-921b-747c3849d0f3" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
