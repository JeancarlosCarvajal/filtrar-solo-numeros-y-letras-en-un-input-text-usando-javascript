# filtrar-solo-numeros-y-letras-en-un-input-text-usando-javascript
Filtrar sólo Números y Letras en un Input Text usando JavaScript

    <body>
        <div style="display: inline-grid;">
            <input type="text" class="input" name="input" id="input">
            <strong>Sólo Números y Letras es Permitido</strong>
        </div>
    </body>
    <script>  
        // Evento que lee el Input Text
        document.getElementById('input').addEventListener('input', function(e){
            console.log(e); 
            // Identificamos el input
            var input = e.target; 
            // Elemento donde colocaremos la alerta
            var alerta = input.nextElementSibling; 
            // Variable que usaremos para determinar si el input es valido
            let isValid = false;  
            // El tamaño maximo de caracteres para nuestro input
            const maximo = 60; 
            // Patron permitido, acepta ñ y acentos. Y " " valida espacios
            const pattern = new RegExp('^[a-zA-Z0-9-\u00f1\u00d1\D@.,:áéíóú ]+$', 'i');
            // Primera, Si input esta vacio entonces no es valido
            if (!input.value) {
                isValid = false;
            } else {
                // Segunda, Si input es mayor que el maximo de caracteres
                if (input.value.length > maximo) {
                    isValid = false;
                } else {
                    // Tercera, Si input contiene caracteres diferentes a los permitidos
                    if (!pattern.test(input.value)) {
                        // Valida si el input contiene valores fuerade los permitidos
                        isValid = false;
                    } else {
                        // Si pasamos todas la validaciones anteriores el input es valido
                        isValid = true;
                    }
                }
            }
            // Ahora coloreamos el borde de nuestro input y escribimos algo
            if (isValid === false) { // Si no es valido
                input.style.outlineColor = 'red'; 
                input.style.borderColor = 'red';
                alerta.style.color = 'red'; 
                alerta.innerHTML = 'Error, sólo Números y Letras';
            } else { // Si es Valido
                input.style.outlineColor = 'green'; 
                input.style.borderColor = 'green'; 
                alerta.style.color = 'green'; 
                alerta.innerHTML = 'Vamos Bien';
            }
 
            return isValid;
        });  
    </script> 
