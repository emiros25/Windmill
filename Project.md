# Windmill
School project
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
    <style>
        @keyframes roter{
            from{
                transform: rotate(0deg);
            }
            to{
                transform:rotate(360deg);
            }
        }
        .container>img{
            position:absolute;
        }
        .windmill>img{
            top: -40px;
            left:800px;
        }
        #blader{
            transform-origin:50% 205px;
            animation: roter 2s;
            animation-iteration-count: infinite;
            animation-timing-function: linear;
        }
    </style>
    </head>S
    <body>
        <input id="vindNavn">
        <span id="visVind"></span>
        <audio id="vindLyd" src="bilder/sommervind.mp3"></audio>
        
        <div class="container">
            <img src="bilder/bakgrunn2.jpg">
            <img class="windmill"src="bilder/vindm%C3%B8llestang2.png">
            <img id="blader" class="windmill"src="bilder/vindm%C3%B8lletegning2.png">
        </div>
        
        <script>
            var vindInput = document.getElementById("vindNavn");
            var vindOutput = document.getElementById("visVind");
            var vindLyd = document.getElementById("vindLyd");
            var rotor = document.getElementById("blader");
            
            function vindstyrke(navn){
                //tar navnet på en vindkategori og returnerer vindhastigheten det tilsvarer.
                if(navn==="stille"){
                return "0-0.2 m/s";
            }
            else if(navn==="lett bris"){
                return "3.4-5.4 m/s";
            }
            else if(navn==="stiv kuling"){
                return "13.9-17.1 m/s";
            }
        }
            
            function styrLyd(navn){
                //funskjon som starter eller stopper audioelementet avhengig av hva vindnavnet er.
                if(navn==="stiv kuling"||navn==="lett bris"){
                    lyd.play();
                }
                else{
                    //hvis stille, eller hvis brukeren skriver feil, spilles ikke lyden.
                    lyd.pause();
                }
            }
            function styrVindmoelle(navn){
                if(navn==="stille"){
                    rotor.style.animationDuration = "5s";
                }
                else if(navn==="lett bris"){
                    rotor.style.animationDuration = "2s";
                }
                else if(navn==="stiv kuling"){
                    rotor.style.animationDuration = "1s";
            }
        }
             function oppdater(){
              var navn = vindInput.value;
                vindOutput.innerHTML = vindstyrke(navn);
                styrVindmoelle(navn);
            }
            vindInput.onchange = oppdater;
        </script>
        <h1>Oppgave 2</h1>
        <input type="number" id="vindFartInput"><span>m/s</span>
        <script>
            var vindTall = document.getElementById("vindFartInput");
            
            function effekt(vind){
                //en funksjon som tar vindhastigheten som parameter og returnerer effekten til vindmøllen.
                if(vind<2.5){
                    return 0;
                }
                else if(vind<3.3){
                    return 2;
                }
                else if(vind<5.5){
                    return 10;
                }
                else if(vind<0.0){
                    return 60;
                }
                else if(vind<10.0){
                    return 150;
                }
                else if(vind<13.9){
                    return 400;
                }
                else if(vind<15.0){
                    return 500;
                }
                else{
                    return 0;
                }
            }
            function oppdaterEffekt(){
                var vind = Number(vindTall.value);
                var vindmoelleEffekt
                effekt.innerHTML = 'Effekten er ${regnEffekt(vind)}watt';
            }
            vindTall.oninput = oppdaterEffekt;
        </script>
        <h1>Oppgave 3</h1>
        <button>Regn ut døgnproduksjon</button>
        <script>
            var button = document.getElementById("btn");
            button.onclick = function(){
                var totalProduksjon = 0,
                var vind = Number(prompt("Hva er vinden mellom 2 og 8?"));
            }
            var produksjon = regnEffekt(vind)*6;
            totalProduksjon += produksjon;
            vind= Number(prompt("Hva er vinden mellom 8 og 14?"));
            
            produksjon = regnEffekt(vind)*6;
            totalProduksjon += produksjon;
            vind= Number(prompt("Hva er vinden mellom 20 og 2?"));
            
            produksjon = regnEffekt(vind)*6;
            totalProduksjon += produksjon;
            alert("Dagsproduksjon er "+totalProduksjon?+" Watt");
        </script>
    </body>
</html>
