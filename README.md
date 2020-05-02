>
<html>
    <head>
        <title>Polski Kinklist</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script src="//code.jquery.com/jquery-2.1.4.min.js"></script>
        <link rel="icon" type="image/x-icon" href="data:image/x-icon;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAAWdEVYdENyZWF0aW9uIFRpbWUAMTAvMjEvMTV5ehY1AAAAZElEQVQ4jaWTwQ3AIAwDbcT+I9f9hjYQA/mAkO7igKAACWdFAF0A2gb0hP0uCyTATyAJSoaK5xGyEmTC9lktmORUdAQvBQ5cJshktoDk0HkmKRNUEmuE6ztYVXe7bT+jW7z9zi8qYiodCjCHKgAAAABJRU5ErkJggg==">
        <style>
            body {
                font-family: 'Verdana', 'Arial';
                font-size: 12px;
            }
            h2 {
                padding: 0;
                margin: 0;
                margin-top: 10px;
                margin-bottom: 5px;
                font-size: 18px;
            }
            table {
                border-collapse: collapse;
                margin-bottom: 10px;
                width: 100%;
            }
            th {
                border: solid #999 1px;
                border-right: none;
                margin: 0px;
                padding: 4px;
                background-color: #666;
                color: #FFF;
            }
            th.choicesCol {
                box-sizing: border-box;
                width: 125px;
            }
            th + th {
                border-left: none;
            }
            th:last-child {
                border-right: solid #999 1px;
            }
            td {
                border-left: solid #999 1px;
                border-bottom: solid #999 1px;
                border-right: solid #999 1px;
                margin: 0px;
                padding: 4px;
                padding-right: 2px;
            }
            @-moz-document url-prefix() { 
              td {
                 padding: 3.3px;
              }
            }            
            td + td {
                border-left-style: none;
            }
            .choice {
                box-sizing: border-box;
                width: 15px;
                height: 15px;
                opacity: 0.35;
                overflow: hidden;
                text-indent: 100px;
                border: solid #000 1px;
                border-radius: 50%;
                outline-style: none!important;
                vertical-align: middle;
                display: inline-block;
                cursor: pointer;
                font-size: 0;
                padding: 0;
            }
            .choices .choice {
                transition: all 0.3s ease-in-out;
            }
            .choice + .choice {
                margin-left: 5px;
            }
            .choices .choice:hover {
                opacity: 0.75;
            }
            .choice.selected, .selected > .choice {
                opacity: 1;
                border-width: 2px;
            }
            
            .legend {
                vertical-align: middle;
                font-size: 14px;
            }
            .legend div {
                display: inline-block;
            }
            .legend .choice {
                opacity: 1;
                cursor: default;
            }
            .legend-text {
                vertical-align: middle;
            }
            
            #ExportWrapper {
                width: 460px;
                height: 36px;
            }
            #URL {
                display: none;
                position: absolute;
                top: 3px;
                box-sizing: border-box;
                width: 300px;
                height: 30px;
                border-radius: 4px;
                border: solid #CCC 1px;
                font-size: 16px;
                padding: 10px;
                text-align: center;
                color: #666;
                font-weight: bold;
            }
            #Export {
                position: absolute;
                left: 310px;
                box-sizing: border-box;
                color: #FFF;
                text-transform: uppercase;
                background-color: #4980ae;
                font-size: 18px;
                width: 150px;
                height: 36px;
                border-style: none;
                border-radius: 4px;
                cursor: pointer;
                transition: all 0.3s ease-in-out;
            }
            #Export:hover {
                opacity: 0.85;
            }
            #Loading {
                display: none;
                overflow: visible;
                line-height: 26px;
                font-size: 16px;
                color: #999;
                font-weight: bold;
                position: absolute;
                top: 4px;
                left: 220px;
            }
            #Loading:before {
                content: '';
                position: absolute;
                box-sizing: border-box;
                width: 26px;
                height: 26px;
                border-radius: 50%;
                border: solid #999 2px;
                border-top-color: transparent;
                border-left-color: #CCC;
                border-right-color: #666;
                animation: spin .5s infinite linear;
                margin-left: -40px;
            }
            @media (min-width: 1700px) {
                .legend {
                    position: absolute;
                    top: 7px;
                    left: 160px;
                }
                .legend div {
                    width: 130px;
                }
                #ExportWrapper {
                    position: absolute;
                    top: -3px;
                    right: 46px;
                }
                h1 {
                    margin-bottom: 0;
                }
            }
            @media (max-width: 1700px) and (min-width: 800px) {
                .legend div {
                    width: 130px;
                    padding-bottom: 10px;
                }
                #ExportWrapper {
                    position: absolute;
                    top: -3px;
                    right: 46px;
                }
            }
            @media (max-width: 800px) and (min-width: 598px) {
                .legend div {
                    width: 180px;
                    padding-bottom: 10px;
                    padding-left: 10px;
                }
                #ExportWrapper {
                    position: relative;
                    margin-top: 10px;
                    margin-left: 5px;
                }
                #URL {
                    left: 155px;
                    width: 190px;
                    font-size: 10px;
                }
                #Export {
                    left: 0px;
                }
                #Loading {
                    left: 230px;
                }
            }
            @media (max-width: 597px) {
                body {
                    font-size: 10px;
                }
                table {
                    min-width: 345px;
                }
                .legend div {
                    width: 150px;
                    padding-bottom: 10px;
                    padding-left: 10px;
                }
                #ExportWrapper {
                    position: relative;
                    margin-top: 10px;
                    margin-left: 0px;
                    width: 345px;
                }
                #URL {
                    left: 155px;
                    width: 190px;
                    font-size: 10px;
                }
                #Export {
                    left: 0px;
                }
                #Loading {
                    left: 230px;
                }
            }
            @keyframes spin {
                0% {transform: rotate(0deg);}
                100% {transform: rotate(-360deg);}
            }
            
            #ExportWrapper :last-child:after {
                content: '';
                display: block;
                clear: both;
            }
            .kinkCategory {
                
            }
            .col {
                float: left;
                box-sizing: border-box;
                margin: 0;
                padding: 5px;
            }
            .col.col25 { width: 25%; }
            .col.col33 { width: 33.33333%; }
            .col.col50 { width: 50%; }
            .col.col100 { width: 100%; padding: 0px; }
            .widthWrapper {
                max-width: 1700px;
                margin-left: auto;
                margin-right: auto;
                position: relative;
            }
            #Edit {
                width: 18px;
                height: 18px;
                background-color: transparent;
                background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAASCAYAAABWzo5XAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAAWdEVYdENyZWF0aW9uIFRpbWUAMTAvMTIvMTUsb8MLAAABaElEQVQ4jZWUvY3jMBCF390mzpQ6I1wBS5A6oDuQOxi4Ap4rUAlqwR1M7IhQBYRCR1To7G1giJBkes/7gElGg4/zK7AgVaWI0FpLAIwxlsJWwtbRdR0BrKzruvw9pUTnHEMIP4NCCC8gay2991TVnGVVVSvYCyil9AJ6Z0sY5nJCCEwp5Rc/NefcE6Sqb4OMMRQRigiNMcWSU0pPkIgUIW3b5gmqKkmybdtVzOwnSZRKMcaQJOu6zr66rklylZn3PoO+7vf7P2x0Op2w2+1wuVyybxxHNE0DALjdbgCAaZrweDyw3+/xN8aIvu9hrd3y/qthGHA+n3E4HJDH773/dWnLpmfQdnqfNHs2EeEfkpymCU3TYBiGVerGGByPRwDA9XrFOI7FElX1WZpz7ldLOO9PCCHfIeb7qqrqY9C8hEvlHi1h1lqqKr33xZPZXv4KNMOcc6sX+77/8bdSBJUUY8xZisjqLJb6Bpjss/W5PAkOAAAAAElFTkSuQmCC');
                background-repeat: no-repeat;
                float: left;
                border-style: none;
                outline-style: none!important;
                margin-top: 6px;
                margin-right: 4px;
                opacity: 0.5;
                cursor: pointer;
            }
            #Edit:hover {
                opacity: 1;
            }
            
            .overlay {
                position: fixed;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                background-color: rgba(0, 0, 0, 0.8);
                display: none;
            }
            #EditOverlay #Kinks {
                box-sizing: border-box;
                position: absolute;
                top: 10px;
                bottom: 50px;
                width: 330px;
                left: 50%;
                margin-left: -165px;
                resize: none;
                padding: 10px;
                border-radius: 5px;
                font-family: monospace, 'Courier new', Courier;
            }
            #EditOverlay #KinksOK {
                box-sizing: border-box;
                position: absolute;
                bottom: 10px;
                width: 330px;
                height: 30px;
                left: 50%;
                margin-left: -165px;
                color: #FFF;
                text-transform: uppercase;
                background-color: #4980ae;
                font-size: 18px;
                border-style: none;
                border-radius: 5px;
                cursor: pointer;
            }
            
            #InputOverlay {
                text-align: center;
                white-space: nowrap;
            }
            #InputOverlay:before {
                content: '';
                display: inline-block;
                height: 100%;
                vertical-align: middle;
                margin-right: -0.25em;
            }
            #InputOverlay .widthWrapper {
                display: inline-block;
                vertical-align: middle;
                width: 400px;
                text-align: left;
                max-width: 100%;
            }
            #InputOverlay .widthWrapper #InputCurrent, #InputOverlay .widthWrapper .kink-simple {
                display: block;
                box-sizing: border-box;
                padding: 10px;
                background-color: #EEE;
            }
            #InputOverlay .widthWrapper .kink-simple {
                position: relative;
                height: 40px;
                line-height: 20px;
                cursor: pointer;
            }
            #InputOverlay .widthWrapper .kink-simple .choice {
                margin-right: 5px;
            }
            #InputOverlay .widthWrapper .kink-simple .txt-category {
                position: absolute;
                right: 5px;
                top: 5px;
                text-transform: uppercase;
                font-size: 90%;
                font-weight: bold;
                opacity: 0.6;
                line-height: 1em;
            }
            #InputOverlay .widthWrapper .kink-simple .txt-field, #InputOverlay .widthWrapper .kink-simple .txt-kink {
                vertical-align: middle;
            }
            #InputOverlay .widthWrapper .kink-simple .txt-field:empty {
                display: none;
            }
            #InputOverlay .widthWrapper .kink-simple .txt-field:before {
                content: '(';
            }
            #InputOverlay .widthWrapper .kink-simple .txt-field:after {
                content: ') ';
            }
            
            #InputOverlay .widthWrapper #InputPrevious .kink-simple:first-child,
            #InputOverlay .widthWrapper #InputNext .kink-simple:nth-child(3) {
                background-color: #BBB;
                font-size: 10px;
                margin-left: 12px;
                margin-right: 12px;
                height: 33px;
            }
            #InputOverlay .widthWrapper #InputPrevious .kink-simple:nth-child(2),
            #InputOverlay .widthWrapper #InputNext .kink-simple:nth-child(2) {
                background-color: #CCC;
                font-size: 11px;
                margin-left: 6px;
                margin-right: 6px;
                height: 37px;
            }
            #InputOverlay .widthWrapper #InputPrevious .kink-simple:nth-child(3),
            #InputOverlay .widthWrapper #InputNext .kink-simple:first-child {
                background-color: #DDD;
                margin-left: 3px;
                margin-right: 3px;
            }
            #InputOverlay .widthWrapper #InputPrevious .kink-simple:first-child {
                padding-bottom: 4px;
                padding-top: 7px;
            }
            #InputOverlay .widthWrapper #InputNext .kink-simple:nth-child(3) {
                padding-top: 4px;
            }
            #InputOverlay .widthWrapper #InputPrevious .kink-simple:nth-child(2) {
                padding-bottom: 7px;
                padding-top: 9px;
            }
            #InputOverlay .widthWrapper #InputNext .kink-simple:nth-child(2) {
                padding-top: 7px;
            }
            
            #InputPrevious .kink-simple {
                border-top-left-radius: 2px;
                border-top-right-radius: 2px;
            }
            #InputNext .kink-simple {
                border-bottom-left-radius: 2px;
                border-bottom-right-radius: 2px;
            }
            
            #InputOverlay .widthWrapper #InputCurrent {
                position: relative;
            }
            #InputOverlay .widthWrapper #InputCurrent .closePopup {
                position: absolute;
                top: 0;
                right: 5px;
                border-style: none;
                background-color: transparent;
                font-size: 30px;
                cursor: pointer;
                outline-style: none!important;
                opacity: 0.65;
            }
            #InputOverlay .widthWrapper #InputCurrent .closePopup:hover {
                opacity: 1;
            }
            #InputOverlay .widthWrapper #InputCurrent h2 {
                text-transform: uppercase;
                opacity: 0.6;
                margin: 0;
            }
            #InputOverlay .widthWrapper #InputCurrent h3 {
                margin-top: 3px;
                margin-bottom: 0;
                font-size: 14px;
            }
            #InputOverlay .widthWrapper #InputCurrent #InputValues .big-choice {
                padding: 10px;
                background-color: rgba(255,255,255,0.75);
                border-radius: 4px;
                margin-top: 5px;
                cursor: pointer;
            }
            #InputOverlay .widthWrapper #InputCurrent #InputValues .big-choice.selected {
                font-weight: bold;
            }
            #InputOverlay .widthWrapper #InputCurrent #InputValues .big-choice.selected .choice {
                opacity: 1;
            }
            #InputOverlay .widthWrapper #InputCurrent #InputValues .big-choice:hover {
                padding: 8px;
                border: solid #999 2px;
                background-color: rgba(255,255,255,1);
            }
            #InputOverlay .widthWrapper #InputCurrent #InputValues .big-choice .btn-num-text {
                float: right;
                display: inline-block;
                border: solid #CCC 1px;
                text-align: center;
                width: 16px;
                border-radius: 3px;
            }
            #StartBtn {
                position: absolute;
                top: -3px;
                right: 5px;
                box-sizing: border-box;
                width: 36px;
                height: 36px;
                background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACQAAAAkCAYAAADhAJiYAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAAWdEVYdENyZWF0aW9uIFRpbWUAMTAvMTUvMTWxuPuyAAACcElEQVRYhe3X30tTYRzH8fdz3FYTd1xamAuTLDbM3EwqNMnoQgxydVH0A6Ks/oG6Mvp1n1flVUJE3pjUTVPCCJxmEKTWRAuCApujkmhJoZu57ZwuwsCaOx7nbBf73D2H7/PldfjCc54j6CxXSaNI/xvwdzIgrWRAWsmAtJJ2IIOe4iLzejoqmym1lDAZ+UFEicatC8Vm6A++5Jb/Pm+nxlIHatl2keo8FwJBriGHREe8U7bjyrWz7/m51IHq1lWjqire4AAvJkf5qczGrduUvYHTRQdxyQ5dGN0gg8hCBc4MXyUQnliwbqO5kOO2/ZzyXQagONvGcO0DLrxp5m7As3ygxUZB4aTvEt1fnuGSHQgEnoleKnIdEEi8NymQ6h7555nocvJt9jsPJ3o4XFhHq/MaAkFF/xE+hD5p9kwKJLqccZ+HYjMcs9XTXnkdSUi0BToXhYEUnUM7rFvnYRqHryx6b1Ig1T2C6h4h0uDjqK0eSUi4ZAc9VbeRhMS76XFdGFjmkblkB3277yAbc3g/PY7D69bdc9lGNoexGi10fOzG7nWTb7KuLCh8YJAyy2YEgqE997AaLbQFOjnxqom1JiueXTd190xqZOZHOwFoLDrEVCxMm9/D+dfNSELiSVUrpZaSlQXNpTc4wJrHNX/W+SYr5bKdqBr/45soSxqZQWTNW/tDn+etV0umpbT93VtP8awSwZhl4EZZE/7wwgddsdmGJAQxRUktyPt1gIaCvTQU1Ca8eghAVVX6goO6QULPn2vBqnyatpylJm87RrHwu0TVKE+DQ7SMtSe8FSQNWomk3Z06A9JKBqSVDEgraQf6BTg8uT5wSV/pAAAAAElFTkSuQmCC');
                border-style: none;
                border-radius: 4px;
                cursor: pointer;
            }
            #StartBtn:hover {
                opacity: 0.8;
            }
            @media (max-height: 500px) {
                #InputPrevious, #InputNext {
                    display: none;
                }
            }
        </style>
    </head>
    <body>
        <div class="widthWrapper">
            <button id="Edit"></button>
            <h1>Kink list</h1>
            <div class="legend">
                <div><span data-color="#FFFFFF" class="choice notEntered"></span> <span class="legend-text">Not Entered</span></div>
                <div><span data-color="#6DB5FE" class="choice favorite"></span> <span class="legend-text">Favorite</span></div>
                <div><span data-color="#23FD22" class="choice like"></span> <span class="legend-text">Like</span></div>
                <div><span data-color="#FDFD6B" class="choice okay"></span> <span class="legend-text">Okay</span></div>
                <div><span data-color="#DB6C00" class="choice maybe"></span> <span class="legend-text">Maybe</span></div>
                <div><span data-color="#920000" class="choice no"></span> <span class="legend-text">No</span></div>
            </div>
            <div id="ExportWrapper">
                <input type="text" id="URL">
                <button id="Export">Export</button>
                <div id="Loading">Loading</div>
            </div>
            <button id="StartBtn"></button>
            <div id="InputList"></div>
        </div>
        <div id="EditOverlay" class="overlay">
            <textarea id="Kinks">
   #Cechy fizyczne
(Podoba mi się u kogoś?)
* Wiek - Efebofilia
* Wiek - Teleiofilia
* Wiek - MiLF/DiLF
* Wiek - Gerontofilia
* Sylwetka chuda
* Sylwetka wysportowana
* Sylwetka thicc
* Sylwetka pulchna
* Sylwetka otyła
* Piersi małe
* Piersi duże
* Piersi zrobione
* Piersi naturalne
* Pupa mała
* Pupa duża
* Wzrost niski
* Wzrost średni
* Wzrost wysoki
* Pochodzenie europeidalne
* Pochodzenie afroeuropejskie
* Pochodzenie negroidalne
* Pochodzenie afroazjatyckie
* Pochodzenie mongoloidalne
* Pochodzenie euroazjatyckie
* Włosy siwe
* Włosy blond
* Włosy rude
* Włosy szatynowe
* Włosy brunatne
* Włosy czarne
* Włosy kolorowe
* Pusia ini
* Pusia outi
* Pusia ogolona
* Pusia wzorek
* Pusia owłosiona
* Penis ogolony
* Penis wzorek
* Penis owłosiony
* Penis cieńszy
* Penis krótszy
* Penis grubszy
* Penis dłuższy
* Penis żylasty
* Penis obrzezany
* Penis nieobrzezany

#Inne cechy fizyczne
(Podoba mi się u kogoś?)
* Rozdwojony język
* Tatuaże
* Kolczyki
* Ogolone ciało
* Owłosione ciało
* Zarost
* Piegi
* Pieprzyki

#Estetyki
(Podoba mi się u kogoś?)
*Alternatywka/or
*Bimbo/Himbo
*Brutaliści
*Dandy
*Dolly
*E-Boy/Girl
*Geek
*Hipsterzy
*Insta girl
*Metale
*Otaku
*Preppy
*Streetwerowcy
*Normcore
*Butch
*Furry
*Goth
*Incel
*K-Boy/Girl
*Karyna
*Konserwatywka
*Kuguar
*Military brat
*Miś/Ursula
*Drag queen
*Punk
*Twink
*Wixapolowiec

#Strój
(Ja(Komuś), Partner(Mi/Sobie))
*Bodypainting
*Okulary
*Nekomimi(Uszy i ogon)
*Choker
*Koronkowa bielizna
*Podwiązki/Pończochy
*Skarpetki i Zakolanówki
*Obcasy z czerwoną podeszwą
*Męskie ubrania
*Damskie ubrania
*Gorsety
*Mundury
*Kostiumy
*Skóra
*Lateks

#Akcesoria
(Ja(Komuś), Partner(Mi/Sobie))
*Kostki lodu
*Czekolada
*Wino
*Czarna pościel
*Lustro
*Przepaska na oczy
*Zatyczki do uszu
*Bańki
*Lubrykant
*Korek analny
*Kulki gejszy
*Jajko Yoni
*Dildo
*Wibrator
*Wand
*Pierścień na penisa
*Strapon
*Knebel
*Obroża
*Smycz
*Bambusowa witka
*Flogger
*Bat
*Koło Wartenberga
*Klamerki na sutki
*Kajdanki
*Huśtawka
*Dyby
*Klatka
*Krzyż św. Andrzeja

#Czynności seksualne
(Ja(Komuś), Partner(Mi/Sobie))
*Romantyzm
*Przytulanie
*Łaskotanie
*Masaż
*Całowanie
*Sexting
*Wysyłanie nudli
*Stymulowanie karku
*Petting
*Graphoerotica
*Handjob(Robótka ręczna)
*Footjob
*Palcówka
*Fisting
*Squirting
*Frottage
*Stosunek hiszpański
*Stosunek między pośladkowy
*Stosunek międzyudowy
*Stosunek pachowy
*Turkey slap
*Wulgaryzmy
*Masturbowanie się
*Oglądanie porno
*Oglądanie hentai
*Własne porno
*Ekshibicjonizm
*Voyeryzm
*Krępowanie
*Kinbaku
*Deprywacja sensoryczna

#Seks Oralny
(Ja(Komuś), Partner(Mi/Sobie))
*Cunnilingus(Patelnia)
*Siadanie na mordzie
*69
*Fellatio(Obciąganie)
*Teabagging
*Głębokie gardło
*Face fucking
*Throat swab
*Wytrysk na twarz
*Bukkake
*Snowballing

#Seks
(Ja(Komuś), Partner(Mi/Sobie))
*W ubraniu
*Waniliowy
*Szybki numerek
*Na świeżym powietrzu
*W miejscach publicznych
*Ostry
*Tantryczny
*Pozycja na łyżeczkę
*Pozycja na jeźdźca
*Pozycja na pieska
*Pozycja na misjonarza
*Pozycja lateralna
*Pozycja stojąca
*Rożen
*Podwójna penetracja
*Potrójna penetracja

#Seks Analny
(Ja(Komuś), Partner(Mi/Sobie))
*Stosunek analny
*Donkey punch
*ATM(Z dupy do ust)
*Fisting analny
*Pegging
*Rimming
*Rusty trombone
*Felching

#Role
(Ja(Komuś), Partner(Mi/Sobie))
*Ageplay - Daddy/Mommy
*Ageplay - Little boy/girl
*Gender play - Man
*Gender play - Fem
*Animal play
*Primal - Hunter
*Primal - Prey

#Układy
(Ja(Komuś), Partner(Mi/Sobie))
*Z kobietą
*Z mężczyzną
*Z mężczyzną i kobietą
*Z pre-op MtF
*Z post-op MtF
*Z pre-op FtM
*Z post-op FtM
*Z dwoma mężczyznami
*Z dwoma kobietami
*Orgia
*Gangbang
*Cuckold
*Cuckquean
*Wifesharing
*Swing

#Chemsex
(Używam?)
*Sildenafil
*Poppers
*Empatogeny
*Oneirogeny
*Psychodeliki
*Dysocjanty
*Delirianty
*Depresanty
*Stymulanty
*Kannabinoidy
*Opioidy

#Dominacja
(Ja(Komuś), Partner(Mi/Sobie))
*Sleep play
*Nakazy
*Zakazy
*Edging
*Kontrola orgazmu
*Odmowa orgazmu
*Wymuszona wstrzemięźliwość seksualna
*Wymuszanie stosunków z osobami trzecimi
*Wymuszanie stosunków z osobami trzecimi bez świadomości
*Branding
*Branding trwały
*Switch
*Maledom
*Femdom
*Master
*Mistress
*Owner
*Money slave
*Sub
*Brat
*Brat tamer

#Sex Working
(Ja(Komuś), Partner(Mi/Sobie))
*Kamerki
*Filmy porno
*Masaż erotyczny
*Striptiz
*Prostytucja
*Prostytucja - GFE
*Prostytucja - Sugar girl/toy
*Prostytucja - Sugar daddy/mommy

#Degradacja
(Ja(Komuś), Partner(Mi/Sobie))
*Ghosting
*Upokorzenie/Poniżenie
*Dehumanizacja
*Stawianie w kącie
*Izolacja
*Ludzkie meble
*Obcinanie włosów
*Służba domowa
*Niewola
*Niewola 24/7
*Pozorowany gwałt

#Wydzieliny
(Ja(Komuś), Partner(Mi/Sobie))
*Ślina
*Połykanie śliny
*Laktacja
*Picie mleka z laktacji
*Sperma
*Połykanie spermy
*Śluz
*Jedzenie śluzu
*Krew
*Picie krwi
*Krew miesięczna
*Picie krwi miesięcznej
*Mocz
*Picie moczu
*Wymioty
*Picie wymiotów
*Fekalia
*Jedzenie fekaliów

#Ból
(Ja(Komuś), Partner(Mi/Sobie))
*Aftercare
*Ciągnięcie za włosy
*Wax Play
*Chili Play
*Figging
*Temperature play - Ciepło
*Temperature play - Zimno
*Fear play
*Knife Play
*Gun Play
*Deprywację snu
*Breath play
*Breath play - Podduszanie
*Breath play - Podduszanie do omdlenia
*Podtapiania
*Waterboarding
*Impact Play
*Impact Play - Drapanie
*Impact Play - Twarz, Otwarta dłoń
*Impact Play - Twarz, Pięść
*Impact Play - Klapsy
*Impact Play - Sutki/Zaciski
*Impact Play - Kopanie
*Impact Play - Pałka teleskopowa
*Impact Play - Kastet
*Impact Play - Siniaki
*Impact Play - Chłosta
*Impact Play - Chłosta do krwi
*Impact Play - Genitalia
*Impact Play - Gryzienie
*Elektrostymulacja
*Fire Play
*Fire Play - Oparzenia
*Piercing Play
*Needle Play
*Blood Play
*Blood Play - Cięcie
*Doprowadzenie do wymiotów
*Sondowanie penisa
*Sadyzm
*Sadomasochizm
*Masochizm

#Inne kinki
(Ja(Komuś), Partner(Mi/Sobie))
*Mile high club
*Ksenofilia
*Kazirodztwo
*Foot play
*Używana bielizna
*Dziewictwo/Prawictwo
*Ciąża
*Nekrofilia

#Choroby
(Mam?)
*Chlamydioza
*Rzeżączka
*Kiła
*HSV
*HPV
*HBV
*HIV
             
            </textarea>
            <button id="KinksOK">Accept</button>
        </div>
        <div id="InputOverlay" class="overlay">
            <div class="widthWrapper">
                <div id="InputPrevious"></div>
                <div id="InputCurrent">
                    <h2 id="InputCategory"></h2>
                    <h3 id="InputField"></h3>
                    <button class="closePopup">&times;</button>
                    <div id="InputValues"></div>
                </div>
                <div id="InputNext"></div>
            </div>
        </div>
        <script>
            
            var log = function(val, base) {
                return Math.log(val) / Math.log(base);
            };
            var strToClass = function(str){
                var className = "";
                str = str.toLowerCase();
                var validChars = 'abcdefghijklmnopqrstuvwxyz';
                var newWord = false;
                for(var i = 0; i < str.length; i++) {
                    var chr = str[i];
                    if(validChars.indexOf(chr) >= 0) {
                        if(newWord) chr = chr.toUpperCase();
                        className += chr;
                        newWord = false;
                    }
                    else {
                        newWord = true;
                    }
                }
                return className;
            };
            var addCssRule = function(selector, rules){
                var sheet = document.styleSheets[0];
                if("insertRule" in sheet) {
                    sheet.insertRule(selector + "{" + rules + "}", 0);
                }
                else if("addRule" in sheet) {
                    sheet.addRule(selector, rules, 0);
                }
            };
            
            var kinks = {};
            var inputKinks = {}
            var colors = {}
            var level = {};
            
            $(function(){
                
                var imgurClientId = '9db53e5936cd02f';
                
                inputKinks = {
                    $columns: [],
                    createCategory: function(name, fields){
                        var $category = $('<div class="kinkCategory">')
                                .addClass('cat-' + strToClass(name))
                                .data('category', name)
                                .append($('<h2>')
                                .text(name));
                        
                        var $table = $('<table class="kinkGroup">').data('fields', fields);
                        var $thead = $('<thead>').appendTo($table);
                        for(var i = 0; i < fields.length; i++) {
                            $('<th>').addClass('choicesCol').text(fields[i]).appendTo($thead);
                        }
                        $('<th>').appendTo($thead);
                        $('<tbody>').appendTo($table);
                        $category.append($table);
                        
                        return $category;
                    },
                    createChoice: function(){
                        var $container = $('<div>').addClass('choices');
                        var levels = Object.keys(level);
                        for(var i = 0; i < levels.length; i++) {
                            $('<button>')
                                    .addClass('choice')
                                    .addClass(level[levels[i]])
                                    .data('level', levels[i])
                                    .data('levelInt', i)
                                    .attr('title', levels[i])
                                    .appendTo($container)
                                    .on('click', function(){
                                        $container.find('button').removeClass('selected');
                                        $(this).addClass('selected');
                                    });
                        }
                        return $container;
                    },
                    createKink: function(fields, name){
                        var $row = $('<tr>').data('kink', name).addClass('kinkRow');
                        for(var i = 0; i < fields.length; i++) {
                            var $choices = inputKinks.createChoice();
                            $choices.data('field', fields[i]);
                            $choices.addClass('choice-' + strToClass(fields[i]));
                            $('<td>').append($choices).appendTo($row);
                        }
                        $('<td>').text(name).appendTo($row);
                        $row.addClass('kink-' + strToClass(name));
                        return $row;
                    },
                    createColumns: function(){
                        var colClasses = ['100', '50', '33', '25'];
                        
                        var numCols = Math.floor((document.body.scrollWidth - 20) / 400);
                        if(!numCols) numCols = 1;
                        if(numCols > 4) numCols = 4;
                        var colClass = 'col' + colClasses[numCols - 1];
                        
                        inputKinks.$columns = [];
                        for(var i = 0; i < numCols; i++){
                            inputKinks.$columns.push($('<div>').addClass('col ' + colClass).appendTo($('#InputList')));
                        }
                    },
                    placeCategories: function($categories){
                        var $body = $('body');
                        var totalHeight = 0;
                        for(var i = 0; i < $categories.length; i++) {
                            var $clone = $categories[i].clone().appendTo($body);
                            var height = $clone.height();;
                            totalHeight += height;
                            $clone.remove();
                        }
                        
                        var colHeight = totalHeight / (inputKinks.$columns.length);
                        var colIndex = 0;
                        for(var i = 0; i < $categories.length; i++) {
                            var curHeight = inputKinks.$columns[colIndex].height();
                            var catHeight = $categories[i].height();
                            if(curHeight + (catHeight / 2) > colHeight) colIndex++;
                            while(colIndex >= inputKinks.$columns.length) {
                                colIndex--;
                            }
                            inputKinks.$columns[colIndex].append($categories[i]);
                        }
                    },
                    fillInputList: function(){
                        $('#InputList').empty();
                        inputKinks.createColumns();
                        
                        var $categories = [];
                        var kinkCats = Object.keys(kinks);
                        for(var i = 0; i < kinkCats.length; i++) {
                            var catName = kinkCats[i];
                            var category = kinks[catName];
                            var fields = category.fields;
                            var kinkArr = category.kinks;
                            
                            var $category = inputKinks.createCategory(catName, fields);
                            var $tbody = $category.find('tbody');
                            for(var k = 0; k < kinkArr.length; k++) {
                                $tbody.append(inputKinks.createKink(fields, kinkArr[k]));
                            }
                            
                            $categories.push($category);
                        }
                        inputKinks.placeCategories($categories);
                        
                        // Make things update hash
                        $('#InputList').find('button.choice').on('click', function(){
                            location.hash = inputKinks.updateHash();
                        });
                    },
                    init: function(){
                        // Set up DOM
                        inputKinks.fillInputList();
                        
                        // Read hash
                        inputKinks.parseHash();
                        
                        // Make export button work
                        $('#Export').on('click', inputKinks.export);
                        $('#URL').on('click', function(){ this.select(); });
                        
                        // On resize, redo columns
                        (function(){
                            
                            var lastResize = 0;
                            $(window).on('resize', function(){
                                var curTime = (new Date()).getTime();
                                lastResize = curTime;
                                setTimeout(function(){
                                    if(lastResize === curTime) {
                                        inputKinks.fillInputList();
                                        inputKinks.parseHash();
                                    }
                                }, 500);
                            });
                            
                        })();
                    },
                    hashChars: "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789-_.=+*^!@",
                    maxPow: function(base, maxVal) {
                        var maxPow = 1;
                        for(var pow = 1; Math.pow(base, pow) <= maxVal; pow++){
                            maxPow = pow;
                        }
                        return maxPow;
                    },
                    prefix: function(input, len, char){
                        while(input.length < len) {
                            input = char + input;
                        }
                        return input;
                    },
                    drawLegend: function(context){
                        context.font = "bold 13px Arial";
                        context.fillStyle = '#000000';
                        
                        var levels = Object.keys(colors);
                        var x = context.canvas.width - 15 - (120 * levels.length);
                        for(var i = 0; i < levels.length; i++) {
                            context.beginPath();
                            context.arc(x + (120 * i), 17, 8, 0, 2 * Math.PI, false);
                            context.fillStyle = colors[levels[i]];
                            context.fill();
                            context.strokeStyle = 'rgba(0, 0, 0, 0.5)'
                            context.lineWidth = 1;
                            context.stroke();
                            
                            context.fillStyle = '#000000';
                            context.fillText(levels[i], x + 15 + (i * 120), 22);
                        }
                    },
                    setupCanvas: function(width, height, username){
                        $('canvas').remove();
                        var canvas = document.createElement('canvas');
                        canvas.width = width;
                        canvas.height = height;
                        
                        var $canvas = $(canvas);
                        $canvas.css({
                            width: width,
                            height: height
                        });
                        // $canvas.insertBefore($('#InputList'));
                        
                        var context = canvas.getContext('2d');
                        context.fillStyle = '#FFFFFF';
                        context.fillRect(0, 0, canvas.width, canvas.height);
                        
                        context.font = "bold 24px Arial";
                        context.fillStyle = '#000000';
                        context.fillText('Kinklist ' + username, 5, 25);
                        
                        inputKinks.drawLegend(context);
                        return { context: context, canvas: canvas };
                    },
                    drawCallHandlers: {
                        simpleTitle: function(context, drawCall){
                            context.fillStyle = '#000000';
                            context.font = "bold 18px Arial";
                            context.fillText(drawCall.data, drawCall.x, drawCall.y + 5);
                        },
                        titleSubtitle: function(context, drawCall){
                            context.fillStyle = '#000000';
                            context.font = "bold 18px Arial";
                            context.fillText(drawCall.data.category, drawCall.x, drawCall.y + 5);
                            
                            var fieldsStr = drawCall.data.fields.join(', ');
                            context.font = "italic 12px Arial";
                            context.fillText(fieldsStr, drawCall.x, drawCall.y + 20);
                        },
                        kinkRow: function(context, drawCall){
                            context.fillStyle = '#000000';
                            context.font = "12px Arial";
                            
                            var x = drawCall.x + 5 + (drawCall.data.choices.length * 20);
                            var y = drawCall.y - 6;
                            context.fillText(drawCall.data.text, x, y);
                            
                            // Circles
                            for(var i = 0; i < drawCall.data.choices.length; i++){
                                var choice = drawCall.data.choices[i];
                                var color = colors[choice];
                                
                                var x = 10 + drawCall.x + (i * 20);
                                var y = drawCall.y - 10;
                                
                                context.beginPath();
                                context.arc(x, y, 8, 0, 2 * Math.PI, false);
                                context.fillStyle = color;
                                context.fill();
                                context.strokeStyle = 'rgba(0, 0, 0, 0.5)'
                                context.lineWidth = 1;
                                context.stroke();
                            }
                            
                        }
                    },
                    export: function(){
                        var username = prompt("Please enter your name");
                        if(typeof username !== 'string') return;
                        else if (username.length ) username = '(' + username + ')';
                        
                        $('#Loading').fadeIn();
                        $('#URL').fadeOut();
                        
                        // Constants
                        var numCols = 6;
                        var columnWidth = 250;
                        var simpleTitleHeight = 35;
                        var titleSubtitleHeight = 50;
                        var rowHeight = 25;
                        var offsets = {
                            left: 10,
                            right: 10,
                            top: 50,
                            bottom: 10
                        };
                        
                        // Find out how many we have of everything
                        var numCats = $('.kinkCategory').length;
                        var dualCats = $('.kinkCategory th + th + th').length;
                        var simpleCats = numCats - dualCats;
                        var numKinks = $('.kinkRow').length;
                        
                        // Determine the height required for all categories and kinks
                        var totalHeight = (
                                (numKinks * rowHeight) +
                                (dualCats * titleSubtitleHeight) +
                                (simpleCats * simpleTitleHeight)
                        );
                        
                        // Initialize columns and drawStacks
                        var columns = [];
                        for(var i = 0; i < numCols; i++){
                            columns.push({ height: 0, drawStack: []});
                        }
                        
                        // Create drawcalls and place them in the drawStack
                        // for the appropriate column
                        var avgColHeight = totalHeight / numCols;
                        var columnIndex = 0;
                        $
                            var $cat = $(this);
                            var   
                            var category = kinks[catName];
                            var fields = category.fields;
                            var catKinks = category.kinks;
                            
                            var catHeight = 0;
                            catHeight += (fields.length === 1) ? simpleTitleHeight : titleSubtitleHeight;
                            catHeight += (catKinks.length * rowHeight);
                            
                            // Determine which column to place this category in
                            if((columns[columnIndex].height + (catHeight / 2)) > avgColHeight) columnIndex++;
                            while(columnIndex >= numCols) columnIndex--;
                            var column = columns[columnIndex];
                            
                            // Drawcall for title
                            var drawCall = { y: column.height };
                            column.drawStack.
                            if(fields.length < 2) {
                                column.height += simpleTitleHeight;
                                drawCall.type =  'simpleTitle';
                                drawCall.data = catName;
                            }
                            else {
                                column.height += titleSubtitleHeight;
                                drawCall.type =  'titleSubtitle';
                                drawCall.data = {
                                    category
                                    fields: fields
                                }
                            }
                            
                            // Drawcalls for kinks
                            $cat.find('.kinkRow').each(function()
                                var $kinkRow = $(this)
                                var drawCall = { y: column.height, type: 'kinkRow', data
                                        choices: []
                                        text: $kinkRow.data('kink'
                                }}
                                column.drawStack.push(drawCall)
                                column.height += rowHeight;
                                
                                // Add choices
                                $kinkRow.find('.choices').each(function()
                                    var $selection = $(this).find('.choice.selected')
                                    var selection = ($selection.length > 0
                                            ? $selection.data('level')
                                            : Object.keys(level)[0];
                                    
                                    drawCall.data.choices.push(selection);
                                });
                            });
                        });
                        
                        var tallestColumnHeight = 0;
                        for(var i = 0; i < columns.length; i++)
                            if(tallestColumnHeight < columns[i].height) {
                                tallestColumnHeight = columns[i].height;
                            }
                        }
                        
                        var canvasWidth = offsets.left + offsets.right + (columnWidth * numCols);
                        var canvasHeight = offsets.top + offsets.bottom + tallestColumnHeight;
                        var setup = inputKinks.setupCanvas(canvasWidth, canvasHeight, username);
                        var context = setup.context
                        var canvas = setup.canvas;
                        
                        for(var i = 0; i < columns.length; i++) {
                            var column = columns[i];
                            var drawStack = column.drawStack;
                            
                            var drawX = offsets.left + (columnWidth * i);
                            for(var j = 0; j < drawStack.length; j++){
                                var drawCall = drawStack[j];
                                drawCall.x = drawX;
                                drawCall.y += offsets.top;
                                inputKinks.drawCallHandlers[drawCall.type](context, drawCall);
                            }
                        }
                        
                        //return $(canvas).insertBefore($('#InputList'));
                        
                        // Send canvas to imgur
                        $.ajax({
                            url: 'https://api.imgur.com/3/image',
                            type: 'POST',
                            headers: {
                                // Your application gets an imgurClientId from Imgur
                                Authorization: 'Client-ID ' + imgurClientId,
                                Accept: 'application/json'
                            },
                            data: {
                                // convert the image data to base64
                                image:  canvas.toDataURL().split(',')[1],
                                type: 'base64'
                            },
                            success: function(result) {
                                $('#Loading').hide();
                                var url = 'https://i.imgur.com/' + result.data.id + '.png';
                                $('#URL').val(url).fadeIn();
                            },
                            fail: function(){
                                $('#Loading').hide();
                                alert('Failed to upload to imgur, could not connect')
                            }
                        });
                    },
                    encode: function(base, input){
                        var hashBase = inputKinks.hashChars.length;
                        var outputPow = inputKinks.maxPow(hashBase, Number.MAX_SAFE_INTEGER);
                        var inputPow = inputKinks.maxPow(base, Math.pow(hashBase, outputPow));
                        
                        var output = "";
                        var numChunks = Math.ceil(input.length / inputPow);
                        var inputIndex = 0;
                        for(var chunkId = 0; chunkId < numChunks; chunkId++) {
                            var inputIntValue = 0
                            for(var pow = 0; pow < inputPow; pow++) {
                                var inputVal = input[inputIndex++];
                                if(typeof inputVal === "undefined") break;
                                var val = inputVal * Math.pow(base, pow);
                                inputIntValue += val
                            }
                            
                            var outputCharValue = ""
                            while(inputIntValue > 0) {
                                var maxPow = Math.floor(log(inputIntValue, hashBase));
                                var powVal = Math.pow(hashBase, maxPow);
                                var charInt = Math.floor(inputIntValue / powVal);
                                var subtract = charInt * powVal
                                var char = inputKinks.hashChars[charInt];
                                outputCharValue += char;
                                inputIntValue -= subtract;
                            }
                            var chunk = inputKinks.prefix(outputCharValue, outputPow, inputKinks.hashChars[0]);
                            output += chunk;
                        }
                        return output
                    }
                    decode: function(base, output)
                        var hashBase = inputKinks.hashChars.length;
                        var outputPow = inputKinks.maxPow(hashBase, Number.MAX_SAFE_INTEGER);
                        
                        var values = [];
                        var numChunks = Math.max(output.length / outputPow)
                        for(var i = 0; i < numChunks; i++){
                            var chunk = output.substring(i * outputPow, (i + 1) * outputPow);
                            var chunkValues = inputKinks.decodeChunk(base, chunk);
                            for(var j = 0; j < chunkValues.length; j++) {
                                values.push(chunkValues[j]);
                            }
                        }
                        return values;
                    },
                    decodeChunk: function(base, chunk){
                        var hashBase = inputKinks.hashChars.length;
                        var outputPow = inputKinks.maxPow(hashBase, Number.MAX_SAFE_INTEGER);
                        var inputPow = inputKinks.maxPow(base, Math.pow(hashBase, outputPow));
                        
                        var chunkInt = 0;
                        for(var i = 0; i < chunk.length; i++) {
                            var char = chunk[i];
                            var charInt = inputKinks.hashChars.indexOf(char);
                            var pow = chunk.length - 1 - i;
                            var intVal = Math.pow(hashBase, pow) * charInt;
                            chunkInt += intVal;
                        }
                        var chunkIntCopy = chunkInt;
                        
                        var output = [];
                        for(var pow = inputPow - 1; pow >= 0; pow--) {
                            var posBase = Math.floor(Math.pow(base, pow));
                            var posVal = Math.floor(chunkInt / posBase);
                            var subtract = posBase * posVal;
                            output.push(posVal);
                            chunkInt -= subtract;
                        }
                        output.reverse();
                        return output;
                    },
                    updateHash: function(){
                        var hashValues = [];
                        $('#InputList .choices').each(function(){
                            var $this = $(this);
                            var lvlInt = $this.find('.selected').data('levelInt');
                            if(!lvlInt) lvlInt = 0;
                            hashValues.push(lvlInt);
                        });
                        return inputKinks.encode(Object.keys(colors).length, hashValues);
                    },
                    parseHash: function(){
                        var hash = location.hash.substring(1);
                        if(hash.length < 10) return;
                        
                        var values = inputKinks.decode(Object.keys(colors).length, hash);
                        var valueIndex = 0;
                        $('#InputList .choices').each(function(){
                            var $this = $(this);
                            var value = values[valueIndex++];
                            $this.children().eq(value).addClass('selected');
                        });
                    },
                    saveSelection: function(){
                        var selection = [];
                        $('.choice.selected').each(function(){
                            // .choice selector
                            var selector = '.' + this.className.replace(/ /g, '.');
                            // .choices selector
                            selector = '.' + $(this).closest('.choices')[0].className.replace(/ /g, '.') + ' ' + selector;
                            // .kinkRow selector
                            selector = '.' + $(this).closest('tr.kinkRow')[0].className.replace(/ /g, '.') + ' ' + selector;
                            // .kinkCategory selector
                            selector = '.' + $(this).closest('.kinkCategory')[0].className.replace(/ /g, '.') + ' ' + selector;
                            selector = selector.replace('.selected', '');
                            selection.push(selector);
                        });
                        return selection;
                    },
                    inputListToText: function(){
                        var KinksText = "";
                        var kinkCats = Object.keys(kinks);
                        for(var i = 0; i < kinkCats.length; i++){
                            var catName = kinkCats[i];
                            var catFields = kinks[catName].fields;
                            var catKinks = kinks[catName].kinks;
                            KinksText += '#' + catName + "\r\n";
                            KinksText += '(' + catFields.join(', ') + ")\r\n";
                            for(var j = 0; j < catKinks.length; j++){
                                KinksText += '* ' + catKinks[j] + "\r\n";
                            }
                            KinksText += "\r\n";
                        }
                        return KinksText;
                    },
                    restoreSavedSelection: function(selection){
                        setTimeout(function(){
                            for(var i = 0; i < selection.length; i++){
                                var selector = selection[i];
                                $(selector).addClass('selected');
                            }
                            location.hash = inputKinks.updateHash();
                        }, 300);
                    },
                    parseKinksText: function(kinksText){
                        var newKinks = {};
                        var lines = kinksText.replace(/\r/g, '').split("\n");

                        var cat = null;
                        var catName = null;
                        for(var i = 0; i < lines.length; i++){
                            var line = lines[i];
                            if(!line.length) continue;

                            if(line[0] === '#') {
                                if(catName){
                                    if(!(cat.fields instanceof Array) || cat.fields.length < 1){
                                        alert(catName + ' does not have any fields defined!');
                                        return;
                                    }
                                    if(!(cat.kinks instanceof Array) || cat.kinks.length < 1){
                                        alert(catName + ' does not have any kinks listed!');
                                        return;
                                    }
                                    newKinks[catName] = cat;
                                }
                                catName = line.substring(1).trim();
                                cat = { kinks: [] };
                            }
                            if(!catName) continue;
                            if(line[0] === '(') {
                                cat.fields = line.substring(1, line.length - 1).trim().split(',');
                                for(var j      
                                    cat.fields  
                                }
                            }
                            if(line[0] === '*'){
                                var   
                                cat.kinks.push(kink);
                            }
                        }
                        if(catName && !newKinks[catName]){
                            if(!(cat.fields instanceof Array) || cat.fields.length < 1){
                                alert(catName + ' does not have any fields defined!');
                                return;
                            }
                            if(!(cat.kinks instanceof Array) || cat  
                                alert(catName + ' does not have any kinks listed!');
                                return;
                            }
                            newKinks[  
                        }
                        return newKinks;
                    }
                }

                $('#Edit').on('click', 
                    var KinksText = inputKinks.
                    $('#Kinks').val(KinksText.trim());
                    $('#EditOverlay').fadeIn();
                });
                $('#EditOverlay').on('click', function(){
                    $(this).fadeOut();
                });
                $('#KinksOK').on('click', function
                    var selection = inputKinks.saveSelection(
                    try 
                        var kinksText = $('#Kinks').val();
                        kinks = inputKinks.parseKinksText(kinksText);
                        inputKinks.fillInputList();
                    }
                    catch(e){
                        alert('An error occured trying to parse the text entered, please correct it and try again'
                        return
                    }
                    inputKinks.restoreSavedSelection(selection)
                    $('#EditOverlay').fadeOut()
                })
                $('.overlay > *').on('click', function(e)
                    e.stopPropagation()
                });
        
                var stylesheet = document.styleSheets[0]
                $('.legend .choice').each(function()
                    var $choice = $(this)
                    var $parent = $choice.parent()
                    var text = $parent.text().trim()
                    var color = $choice.data('color');
                    var cssClass = this.className.replace('choice ', '').trim();
                    
                    addCssRule('.choice.' + cssClass, 'background-color: ' + color + ';');
                    colors[text] = color;
                    level[text] = cssClass;
                });
        
                kinks = inputKinks.parseKinksText($('#Kinks').text().trim());
                inputKinks.init();
                
                (function(){
                    var $popup = $('#InputOverlay');
                    var $previous = $('#InputPrevious');
                    var $next = $('#InputNext');

                    // current
                    var $category = $('#InputCategory')
                    var $field = $('#InputField')
                    var $options = $('#InputValues');

                    function getChoiceValue($choices)
                        var $selected = $choices.find('.choice.selected')
                        return $selected.data('level')
                    }

                    function getChoicesElement(category, kink, field){
                        var selector = '.cat-' + strToClass(category);
                        selector += ' .kink-' + strToClass(kink);
                        selector += ' .choice-' + strToClass(field);

                        var $choices = $(selector);
                        return $choices;
                    }

                    inputKinks.getAllKinks = function()
                        var list = [];

                        var categories = Object.keys(kinks);
                        for(var i      
                            var category = categories[i];
                            var fields = kinks[category].fields;
                            var   

                            for(var j =      
                                var field = fields[j]
                                for(var k = 0    
                                    var kink = kinkArr[k]
                                    var     
                                    var value = getChoiceValue($choices);
                                    var obj = { category: category, kink: kink, field: field, value: value, $choices: $choices 
                                    list.push(obj);
                                }
                            }

                        }
                        return list;
                    };

                    inputKinks.inputPopup = {
                        numPrev: 3,
                        numNext: 3,
                        allKinks
                        kinkByIndex: function
                            var numKinks = inputKinks.inputPopup.
                            i = (numKinks + 
                            return inputKinks.inputPopup.allKinks[i];
                        },
                        generatePrimary: function(kink){
                            var $container = $('<div>');
                            var btnIndex = 0;
                            $('.legend > div').each(function(){
                                var $btn = $(this).clone();
                                $btn.addClass(
                                $btn.appendTo($container);

                                $
                                        .addClass('btn-num-text')
                                        .text(btnIndex++
                                        .appendTo($btn)

                                var text = $btn.text().trim().replace(/[0-9]/g, '')
                                if(kink.value === text) 
                                    $btn.addClass('selected');
                                }

                                $btn.on('click', function
                                    $container.find('.big-choice').removeClass(
                                    $btn.addClass(
                                    kink.value = 
                                    $options.fadeOut(200, function
                                        $options.show();
                                        inputKinks.inputPopup.showNext();
                                    });
                                    var choiceClass = strToClass(text);
                                    kink.$choices.find('.' + choiceClass).click();
                                });
                            });
                            return $container;
                        },
                        generateSecondary: function(kink){
                            var $container = $('<div class="kink-simple">');
                            $('<span class="choice">').addClass(level[kink.value]).appendTo($container);
                            $('<span class="txt-category">').text(kink.category).appendTo($container)
                            if(kink.showField)
                                $('<span class="txt-field">').text(kink.field).appendTo($container
                            }
                            $('<span class="txt-kink">').text(kink.kink).appendTo($container
                            return 
                        }
                        showIndex: function(index
                            $previous.html(''
                            $next.html('')
                            $options.html('')
                            $popup.data('index', index);

                            // Current
                            var currentKink = inputKinks.inputPopup.kinkByIndex(index)
                            var $currentKink = inputKinks.inputPopup.generatePrimary(currentKink)
                            $options.append($currentKink)
                            $category.text(currentKink.category);
                            $field.text((currentKink.showField ? '(' + currentKink.field + ') ' : '') + currentKink.kink)
                            $options.append($currentKink);

                            // Prev
                            for(var i = inputKinks.inputPopup.numPrev; i > 0; i--){
                                var prevKink = inputKinks.inputPopup.kinkByIndex(index - i);
                                var $prevKink = inputKinks.inputPopup.generateSecondary(prevKink)
                                $previous.append($prevKink)
                                (function(skip)
                                    $prevKink.on('click', function(){
                                        inputKinks.inputPopup.showPrev(skip);
                                    });
                                })(i)
                            }
                            // Next
                            for(var i = 1; i <= inputKinks.inputPopup.numNext; i++)
                                var nextKink = inputKinks.inputPopup.kinkByIndex(index + i)
                                var $nextKink = inputKinks.inputPopup.generateSecondary(nextKink);
                                $next.append($nextKink);
                                (function(skip){
                                    $nextKink.on('click', function(){
                                        inputKinks.inputPopup.showNext(skip);
                                    });
                                })(i);
                            }
                        },
                        showPrev: function(skip){
                            if(typeof skip !== "number") skip = 1;
                            var index = $popup.data('index') - skip;
                            var numKinks = inputKinks.inputPopup.allKinks.length;
                            index = (numKinks + index) % numKinks;
                            inputKinks.inputPopup.showIndex(index);
                        },
                        showNext: function(skip){
                            if(typeof skip !== "number") skip = 1;
                            var index = $popup.data('index') + skip
                            var numKinks = inputKinks.inputPopup.allKinks.length;
                            index = (numKinks + index) % numKinks;
                            inputKinks.inputPopup.showIndex(index);
                        },
                        show: function(){
                            inputKinks.inputPopup.allKinks = inputKinks.getAllKinks()
                            inputKinks.inputPopup.showIndex(0);
                            $popup.fadeIn();
                        }
                    };

                    $(window).on('keydown', function(e){
                        if(e.altKey || e.shiftKey || e.ctrlKey) return;
                        if(!$popup.is(':visible')) return;

                        if(e.keyCode === 38) {
                            inputKinks.inputPopup.showPrev();
                            e.preventDefault();
                            e.stopPropagation();
                        }
                        if(e.keyCode === 40) {
                            inputKinks.inputPopup.showNext();
                            e.preventDefault();
                            e.stopPropagation();
                        }

                        var btn = -1
                        if(e.keyCode >= 96 && e.keyCode <= 101) {
                            btn = e.keyCode - 96;
                        }
                        else if(e.keyCode >= 48 && e.keyCode <= 53) {
                            btn = e.keyCode - 48
                        }
                        else 
                            return
                        }

                        var $btn = $options.find('.big-choice').eq(btn)
                        $btn.click();
                    });
                    $('#StartBtn').on('click', inputKinks.inputPopup.show);
                    $('#InputCurrent .closePopup, #InputOverlay').on('click', function()
                        $popup.fadeOut()
                    });                    
                })();
            });
        </script>
    </body>
</html>
