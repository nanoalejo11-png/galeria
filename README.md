<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Galería de Arte Interactiva</title>

<style>
    body {
        font-family: Arial, sans-serif;
        background: #f0f2f5;
        margin: 0;
        padding: 25px;
    }

    h1 {
        text-align: center;
        margin-bottom: 40px;
    }

    h2 {
        margin-top: 50px;
        border-left: 6px solid #4287f5;
        padding-left: 10px;
    }

    /* CONTENEDOR PRINCIPAL DE CADA GALERÍA */
    .gallery {
        max-width: 750px;
        margin: 25px auto;
        background: white;
        padding: 20px;
        border-radius: 12px;
        box-shadow: 0 0 12px rgba(0,0,0,0.2);
        position: relative;
    }

    /* CONTENEDOR DESLIZABLE */
    .slides {
        display: flex;
        overflow: hidden;
        border-radius: 10px;
    }

    .slide {
        min-width: 100%;
        text-align: center;
        padding: 10px;
        box-sizing: border-box;
    }

    .slide img {
        width: 85%;
        max-height: 380px;
        object-fit: cover;
        border-radius: 10px;
    }

    /* CAJA DE INFO */
    .info {
        background: #e9eef3;
        padding: 15px;
        border-radius: 10px;
        margin-top: 10px;
        text-align: left;
    }

    /* BOTONES */
    .btn {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        background: rgba(0,0,0,0.6);
        border: none;
        color: white;
        padding: 12px;
        font-size: 20px;
        cursor: pointer;
        border-radius: 50%;
    }

    .btn:hover {
        background: rgba(0,0,0,0.8);
    }
    .prev { left: 10px; }
    .next { right: 10px; }

</style>
</head>

<body>

<h1>Galería Interactiva de Artes</h1>

<!-- =====================================================
                    VAN GOGH
===================================================== -->
<h2>Vincent van Gogh</h2>
<div class="gallery" id="vangogh-gallery">
    <button class="btn prev" onclick="prevSlide('vangogh')">❮</button>
    <button class="btn next" onclick="nextSlide('vangogh')">❯</button>

    <div class="slides" id="vangogh-slides">

        <!-- LA NOCHE ESTRELLADA -->
        <div class="slide">
            <img src="https://upload.wikimedia.org/wikipedia/commons/e/ef/The_Starry_Night.jpg">
            <div class="info">
                <h3>La noche estrellada (1889)</h3>
                <p><b>Autor:</b> Vincent van Gogh</p>
                <p><b>Lugar actual:</b> MoMA, Nueva York</p>
                <p><b>Técnica:</b> Óleo sobre lienzo</p>
                <p>Una de las pinturas más emblemáticas del arte occidental, representando un cielo nocturno lleno de movimiento y emoción.</p>
            </div>
        </div>

        <!-- GIRASOLES -->
        <div class="slide">
            <img src="https://upload.wikimedia.org/wikipedia/commons/4/47/Vincent_Willem_van_Gogh_128.jpg">
            <div class="info">
                <h3>Los girasoles (1888)</h3>
                <p><b>Lugar actual:</b> National Gallery, Londres</p>
                <p>Parte de una famosa serie donde Van Gogh experimentó con tonos amarillos vibrantes.</p>
            </div>
        </div>

        <!-- NOCHE SOBRE EL RÓDANO -->
        <div class="slide">
            <img src="https://upload.wikimedia.org/wikipedia/commons/7/76/Starry_Night_Over_the_Rhone.jpg">
            <div class="info">
                <h3>Noche estrellada sobre el Ródano (1888)</h3>
                <p><b>Lugar actual:</b> Museo de Orsay, París</p>
                <p>Explora el reflejo de luces artificiales sobre el río y un cielo estrellado.</p>
            </div>
        </div>

    </div>
</div>

<!-- =====================================================
                    MAGRITTE
===================================================== -->
<h2>René Magritte</h2>
<div class="gallery" id="magritte-gallery">
    <button class="btn prev" onclick="prevSlide('magritte')">❮</button>
    <button class="btn next" onclick="nextSlide('magritte')">❯</button>

    <div class="slides" id="magritte-slides">

        <!-- EL HIJO DEL HOMBRE -->
        <div class="slide">
            <img src="https://upload.wikimedia.org/wikipedia/en/0/0c/Magritte_TheSonOfMan.jpg">
            <div class="info">
                <h3>El hijo del hombre (1964)</h3>
                <p><b>Lugar actual:</b> Colección privada</p>
                <p>El icónico hombre del bombín con su rostro oculto por una manzana verde.</p>
            </div>
        </div>

        <!-- LA TRAICIÓN DE LAS IMÁGENES -->
        <div class="slide">
            <img src="https://upload.wikimedia.org/wikipedia/en/b/b9/MagrittePipe.jpg">
            <div class="info">
                <h3>La traición de las imágenes (1929)</h3>
                <p><b>Lugar actual:</b> LACMA, Los Ángeles</p>
                <p>Con la frase “Esto no es una pipa”, cuestiona la relación entre objetos y sus representaciones.</p>
            </div>
        </div>

        <!-- LOS AMANTES -->
        <div class="slide">
            <img src="https://upload.wikimedia.org/wikipedia/en/0/0a/The_Lovers_(Magritte).jpg">
            <div class="info">
                <h3>Los amantes (1928)</h3>
                <p><b>Lugar actual:</b> MoMA, Nueva York</p>
                <p>Dos personas besándose con telas cubriendo sus rostros, símbolo del misterio y la incomunicación.</p>
            </div>
        </div>

    </div>
</div>

<script>
/* INDICE PARA CADA GALERÍA */
const index = { vangogh: 0, magritte: 0 };

function showSlide(artist) {
    const slides = document.getElementById(artist + "-slides");
    slides.style.transform = `translateX(-${index[artist] * 100}%)`;
}

function nextSlide(artist) {
    const total = document.getElementById(artist + "-slides").children.length;
    index[artist] = (index[artist] + 1) % total;
    showSlide(artist);
}

function prevSlide(artist) {
    const total = document.getElementById(artist + "-slides").children.length;
    index[artist] = (index[artist] - 1 + total) % total;
    showSlide(artist);
}
</script>

</body>
</html>
