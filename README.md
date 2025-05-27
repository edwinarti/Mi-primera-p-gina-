# Mi-primera-p-gina-
Creación de personajes épicos con un tono oscuro y muy tradicional.
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Creador de Personajes Oscuros</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: #0a0a0a;
            color: #e0e0e0;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        h1 {
            text-align: center;
            color: #7a1f1f;
            margin-bottom: 2rem;
            font-size: 2.5rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .creator-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            background-color: #1a1a1a;
            padding: 2rem;
            border-radius: 10px;
            border: 1px solid #2a2a2a;
        }

        .character-form {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        input, select, textarea {
            padding: 0.8rem;
            background-color: #2a2a2a;
            border: 1px solid #3a3a3a;
            color: #e0e0e0;
            border-radius: 5px;
        }

        .image-upload {
            border: 2px dashed #3a3a3a;
            padding: 1rem;
            text-align: center;
            cursor: pointer;
        }

        .image-preview {
            max-width: 100%;
            height: 300px;
            object-fit: cover;
            border-radius: 5px;
            display: none;
        }

        .race-class-select {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
        }

        .option-card {
            background-color: #2a2a2a;
            padding: 1rem;
            border-radius: 5px;
            cursor: pointer;
            transition: transform 0.3s;
            border: 2px solid transparent;
        }

        .option-card:hover {
            transform: translateY(-5px);
            border-color: #7a1f1f;
        }

        .option-card img {
            width: 100%;
            height: 150px;
            object-fit: cover;
            border-radius: 3px;
        }

        .character-preview {
            background-color: #2a2a2a;
            padding: 1rem;
            border-radius: 10px;
            position: sticky;
            top: 2rem;
        }

        .character-image {
            width: 100%;
            height: 400px;
            object-fit: cover;
            border-radius: 5px;
            margin-bottom: 1rem;
        }

        button {
            background-color: #7a1f1f;
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1.1rem;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #9a2f2f;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>CREADOR DE PERSONAJES OSCUROS</h1>
        
        <div class="creator-section">
            <div class="character-form">
                <div class="form-group">
                    <label>Nombre del Personaje</label>
                    <input type="text" id="characterName">
                </div>
                
                <div class="form-group">
                    <label>Subir imagen</label>
                    <div class="image-upload" onclick="document.getElementById('imageInput').click()">
                        <input type="file" id="imageInput" hidden accept="image/*">
                        <p>Haz clic para subir una imagen</p>
                        <img id="imagePreview" class="image-preview">
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Selecciona Raza</label>
                    <div class="race-class-select">
                        <div class="option-card" data-race="humano">
                            <img src="humano.jpg" alt="Humano">
                            <h3>Humano</h3>
                        </div>
                        <div class="option-card" data-race="elfo">
                            <img src="elfo.jpg" alt="Elfo Oscuro">
                            <h3>Elfo Oscuro</h3>
                        </div>
                    </div>
                </div>
                
                <button onclick="createCharacter()">Crear Personaje</button>
            </div>
            
            <div class="character-preview">
                <img id="previewImage" class="character-image" src="placeholder.jpg">
                <h2 id="previewName">Nombre del Personaje</h2>
                <div id="characterDetails"></div>
            </div>
        </div>
    </div>

    <script>
        // Manejar la subida de imagen
        document.getElementById('imageInput').addEventListener('change', function(e) {
            const reader = new FileReader();
            reader.onload = function() {
                const preview = document.getElementById('imagePreview');
                preview.src = reader.result;
                preview.style.display = 'block';
                
                // Actualizar vista previa
                document.getElementById('previewImage').src = reader.result;
            }
            reader.readAsDataURL(e.target.files[0]);
        });

        // Crear personaje
        function createCharacter() {
            const characterName = document.getElementById('characterName').value;
            document.getElementById('previewName').textContent = characterName;
            
            // Aquí puedes agregar más lógica para guardar/exportar el personaje
            alert('Personaje creado con éxito!');
        }

        // Selección de razas/clases
        document.querySelectorAll('.option-card').forEach(card => {
            card.addEventListener('click', function() {
                // Remover selección previa
                document.querySelectorAll('.option-card').forEach(c => 
                    c.style.borderColor = 'transparent');
                
                // Marcar selección actual
                this.style.borderColor = '#7a1f1f';
                
                // Actualizar vista previa
                const race = this.dataset.race;
                // Aquí puedes agregar lógica adicional según la raza seleccionada
            });
        });
    </script>
</body>
</html>
