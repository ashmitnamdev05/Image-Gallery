    body {
        font-family: Arial, sans-serif;
        background-color: #f0f0f0;
    }

    .gallery-container {
        max-width: 1000px;
        margin: 50px auto;
        padding: 20px;
        text-align: center;
    }

    .gallery-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 15px;
    }

    .gallery-item {
        width: 100%;
        height: auto;
        cursor: pointer;
        transition: transform 0.3s ease;
    }

    .gallery-item:hover {
        transform: scale(1.05);
    }

    .lightbox {
        display: none;
        position: fixed;
        z-index: 999;
        padding-top: 50px;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.8);
    }

    .lightbox-content {
        margin: auto;
        display: block;
        width: 80%;
        max-width: 700px;
    }

    .prev, .next {
        cursor: pointer;
        position: absolute;
        top: 50%;
        width: auto;
        padding: 16px;
        color: white;
        font-weight: bold;
        font-size: 20px;
        transition: 0.3s ease;
        user-select: none;
    }

    .prev {
        left: 0;
    }

    .next {
        right: 0;
    }

    .prev:hover, .next:hover {
        background-color: rgba(0, 0, 0, 0.5);
    }

    .close {
        position: absolute;
        top: 20px;
        right: 35px;
        color: white;
        font-size: 40px;
        font-weight: bold;
        cursor: pointer;
        transition: 0.3s ease;
    }

    .close:hover {
        color: #ccc;
    }
</style>
    </div>
</div>

<div id="lightbox" class="lightbox">
    <span class="close" onclick="closeLightbox()">&times;</span>
    <img id="lightbox-img" class="lightbox-content">
    <a class="prev" onclick="changeImage(-1)">&#10094;</a>
    <a class="next" onclick="changeImage(1)">&#10095;</a>
</div>

<script>
    let currentImageIndex = 0;
    const images = document.querySelectorAll('.gallery-item');
    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightbox-img');

    function openLightbox(index) {
        currentImageIndex = index;
        lightbox.style.display = 'block';
        lightboxImg.src = images[currentImageIndex].src;
    }

    function closeLightbox() {
        lightbox.style.display = 'none';
    }

    function changeImage(step) {
        currentImageIndex = (currentImageIndex + step + images.length) % images.length;
        lightboxImg.src = images[currentImageIndex].src;
    }
</script>
