<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Full Screen Horizontal Image Slideshow</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html, body {
      height: 100%;
      overflow: hidden; /* Prevent vertical scroll */
    }

    body {
      font-family: Arial, sans-serif;
      background-color: black; /* Optional: Dark background */
    }

    .slider-container {
      display: flex;
      width: 100%;
      height: 100vh; /* Full screen height */
      overflow: hidden; /* Hide overflow */
    }

    .image-slider {
      display: flex;
      transition: transform 0.5s ease-in-out;
      width: 100%;
      height: 100vh; /* Ensure the images stretch to full height */
    }

    .image-slider img {
      width: 100vw; /* Full screen width */
      height: 100vh; /* Full screen height */
      object-fit: cover; /* Ensure image aspect ratio is preserved */
    }
  </style>
</head>
<body>

  <div class="slider-container">
    <div class="image-slider" id="imageSlider">
      <!-- Images will be dynamically loaded here -->
    </div>
  </div>

  <script>
    // JSON data for the image URLs
    const imageData = {
      "images": [
        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRbDL3ld9Li7ZHEmHcpLLwn_IaMyTu0clyDXPuGE-h42vsapD7VY4-P6gFs&s=10",
        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTklPZPv3OuzgpPdQQTycxBo8ggOc39SrtyWReX-lkiJNgn2EDXmTzcXl5e&s=10",
        "https://m.media-amazon.com/images/M/MV5BNDZmMGEwMjQtNjFlNi00ZGIxLTlkZjItNmU3Mzg4Y2E0ZjUzXkEyXkFqcGc@._V1_FMjpg_UX1000_.jpg",
        "https://m.media-amazon.com/images/M/MV5BNDZmMGEwMjQtNjFlNi00ZGIxLTlkZjItNmU3Mzg4Y2E0ZjUzXkEyXkFqcGc@._V1_FMjpg_UX1000_.jpg",
      "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRbDL3ld9Li7ZHEmHcpLLwn_IaMyTu0clyDXPuGE-h42vsapD7VY4-P6gFs&s=10",
        "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTklPZPv3OuzgpPdQQTycxBo8ggOc39SrtyWReX-lkiJNgn2EDXmTzcXl5e&s=10"
        
      ]
    };

    // Function to load images from JSON data
    const imageSlider = document.getElementById('imageSlider');

    imageData.images.forEach(imageURL => {
      const img = document.createElement('img');
      img.src = imageURL;
      img.alt = "Image";
      imageSlider.appendChild(img);
    });

    // Optional: Add functionality to automatically scroll horizontally
    let currentPosition = 0;
    const totalImages = imageData.images.length;
    const slideInterval = setInterval(() => {
      if (currentPosition >= totalImages - 1) {
        currentPosition = 0;
      } else {
        currentPosition++;
      }

      imageSlider.style.transform = `translateX(-${currentPosition * 100}vw)`; // Move slider by 100% of the viewport width
    }, 2000); // Change image every 3 seconds
  </script>

</body>
</html>
