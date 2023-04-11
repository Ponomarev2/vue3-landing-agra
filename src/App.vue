<script setup>

import { ref } from 'vue'

const square = ref(50);
let scrollDirection = true;

function scrollTo(){
  if (scrollDirection) {
    window.scrollTo({ top: 30, behavior: "smooth" });
    // document.querySelector(".image").style.width = "calc(100% - 30px)";
    document.querySelector(".image").style.transform = "translateX(30px)";
    document.querySelector(".button-scroll").style.transform = "rotate(180deg)";

  } else {
    window.scrollTo({ top: -30, behavior: "smooth" });
    // document.querySelector(".image").style.width = "100%";
    document.querySelector(".image").style.transform = "translateX(0)";
    document.querySelector(".button-scroll").style.transform = "rotate(0deg)";
  }
  scrollDirection = !scrollDirection;
}

function toggleDropdown(e){
  const curStyle = e.target.children[0].style.display;
  if (curStyle){
    e.target.children[0].style.display = "";
  } else {
    e.target.children[0].style.display = "block";
  }
}

</script>


<template>
  <div class="container">
    <div class="header">
      <div class="logo">logo</div>
      <div class="nav-bar">
        <div class="nav-bar-menu" @click="toggleDropdown">МЕНЮ
          <div class="drop-down-container">
            <div>Услуги</div>
            <div>Статьи</div>
            <div>Вакансии</div>
            <div>Франшиза</div>
          </div>
        </div>
        <div>ПОРТФОЛИО</div>
        <div>ЦЕНЫ</div>
        <div>СХЕМА РАБОТЫ</div>
        <div>ОТЗЫВЫ</div>
        <div>КОНТАКТЫ</div>
        <div>ГАРАНТИЯ</div>
      </div>
      <div class="button-contact">
        <div class="button">ОБРАТНЫЙ ЗВОНОК</div>
      </div>
    </div>

    <div class="body">
      <div class="content-left">
        <div class="heading">Ремонт под ключ от 2900 руб/м².</div>
          <div class="block2">
            <div class="text">При заказе ремонта делаем дизайн-проект в подарок</div>
            <div class="bar"></div>
          </div>
          <div class="block3">
            <div>
              <div class="icon1"></div>
              <div class="text">Бесплатный выезд в день обращения</div>
            </div>
            <div>
              <div class="icon2"></div>
              <div class="text">Гарантия на работу до 5 лет</div>
            </div>
            <div>
              <div class="icon3"></div>
              <div class="text">Жесткое соблюдение сроков</div>
            </div>
          </div>
      </div>
      <div class="mid-block">
        <div class="heading">Рассчитайте стоимость ремонта</div>
        <div class="set-square">
          <div class="heading">
            <div class="title">Площадь квартиры:</div>
            <div class="square-value">{{ square }}м²</div>
          </div>
          <div class="slidecontainer">
            <input type="range" min="1" max="100" v-model="square" class="slider">
          </div>
        </div>
        <div class="set-type">
          <div class="heading">
            <div class="title">Тип жилья:</div>
          </div>
          <div class="radio-container">
            <div class="option">
              <input type="radio" id="second" name="estate"><label for="second">Вторичное жильё</label>
            </div>
            <div class="option">
              <input type="radio" id="new" name="estate"><label for="new">Новостройка</label>
            </div>
            <div class="option">
              <input type="radio" id="office" name="estate"><label for="office">Офис</label>
            </div>
          </div>
        </div>
        <div class="set-roomcount">
          <div class="heading">
            <div class="title">Кол-во комнат:</div>
          </div>
          <div class="radio-container">
            <div class="option">
              <input type="radio" id="1" name="roomcount"><label for="1">1</label>
            </div>
            <div class="option">
              <input type="radio" id="2" name="roomcount"><label for="2">2</label>
            </div>
            <div class="option">
              <input type="radio" id="3" name="roomcount"><label for="3">3+</label>
            </div>
            <div class="option">
              <input type="radio" id="studio" name="roomcount"><label for="studio">Студия</label>
            </div>
          </div>
        </div>
        <div class="button-send">
          <div class="button">ОТПРАВИТЬ</div>
        </div>
      </div>
      <div class="image"></div>
      <div class="button-scroll-container">
        <div class="button-scroll" @click="scrollTo"></div>
        <label>scroll</label>
      </div>

    </div>

  </div>

</template>


<style>

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@600&family=Roboto:wght@400;500;700;900&display=swap');

.container{
  display: grid;
  background: linear-gradient(99.89deg, #3625AF 0%, #C46BD5 98.82%);
}

.nav-bar > div:hover{
  color: plum;
  cursor: pointer;
}

.button:hover,
.button:hover,
.logo:hover{
  background-color: plum;
  cursor: pointer;
}

.header{
  width: 100%;
  display: inline-flex;
  justify-content: space-evenly;
  margin-top: 1em;

  font-family:  'Inter';
  font-style: normal;
  font-weight: 600;
  font-size: 1em;
  line-height: normal;
  text-transform: uppercase;
  color: #FFFFFF;
}

.logo{
  display: flex;
  align-items: center;
  justify-content: center;
  width: 10em;
  height: 3em;
  background-color: magenta;
  margin-top: 1em;
  line-height: normal;
}

.nav-bar{
  width: 56em;
  display: grid;
  justify-content: space-around;
  grid-template-columns: repeat(7, auto);
}

.nav-bar > div{
  width: auto;
  height: fit-content;;
  padding: 1em;
}

.button{
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: #FFFFFF;
  width: 15em;
  height: 4em;
  border-radius: 0.4em;
  background-color: rgba(48, 37, 148, 1);
  box-shadow: 0px 1em 1em rgba(0, 0, 0, 0.15);
  margin-top: 1em;
  line-height: normal;
}

@keyframes slideInFromLeft {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(0);
  }
}

@keyframes slideInFromRight {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(0);
  }
}

.body{
  display: grid;
  grid-template-columns: 30% 30% 40%;
  grid-template-rows: auto 0;
}

.image{
  position: relative;
  margin-left: auto; 
  margin-right: 0;
  margin-top: 4em;
  width: 100%;
  height: 50em;
  background: url(./assets/0b7eb342eeac23eee20a7d433d8f33d7.png);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 3vh 0vh;
  border-radius: 20% 0 0 0;
  transition: all 0.5s ease-out;
  animation: 1s ease-out 0s 1 slideInFromRight;
}

.content-left > div{
  left: 10vw;
}

.content-left{
  margin-top: 8em;
  animation: 1s ease-out 0s 1 slideInFromLeft;
}

.content-left > .heading{
  position: relative;
  width: 10em;
  color: #FFFFFF;
  font-family: 'Roboto', sans-serif;
  font-style: normal;
  font-weight: 900;
  font-size: 4em;
  line-height: normal;
}

.block2{
  margin-top: 3em;
  position: relative;
  width: 28em;
}

.block2 .bar{
  margin-top: 3%;
  height: 0.5vh;
  width: 14em;
  background-color: rgba(186, 241, 255, 1);
}

.block2 .text{
  color: white;
  font-family: 'Roboto', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 2em;
  line-height: normal;
}

.block3{
  display: grid;
  grid-template-columns: repeat(2, 20em);
  position: relative;
  top: 3em;
  width: 28em;
  color: white;
}

.block3 > div{
  margin-top: 2em;
  display: flex;
  align-items: center;
}

.block3 > div > .text{
  padding-left: 1em;
  width: 12em;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 500;
  font-size: 1em;
}

.icon1{
  background: url(./assets/icon1.svg);
  background-repeat: no-repeat;
  background-size: cover;
  width: 4.5vh;
  height: 3.6vh;
  transform: scale(calc(40/45));
}

.icon2{
  background: url(./assets/icon2.svg);
  background-repeat: no-repeat;
  background-size: cover;
  width: 3.0vh;
  height: 4.0vh;
}

.icon3{
  background: url(./assets/icon3.svg);
  background-repeat: no-repeat;
  background-size: cover;
  width: 4.0vh;
  height: 3.8vh;
  margin-right: 1vh;
}

.mid-block{
  color: #000;
  position: relative;
  left: 14vw;
  top: 10vh;
  width: 40em;
  height: 35em;
  background: #FFFFFF;
  border-radius: 2%;  
  z-index: 3;
  animation: 1s ease-out 0s 1 slideInFromRight;
}

.mid-block > div{
  width: 86%;
  margin-left: 7%;
}

.mid-block > .heading{
  margin-top: 1.5em;
  width: 10em;
  color: #000;
  position: relative;
  font-family: 'Roboto', sans-serif;
  font-weight: 700;
  font-size: 2em;
  line-height: normal;
}

.button-send{
  margin-top: 1em;
  display: flex;
  align-items: center;
  justify-content: center;
  
}

.slidecontainer {
  width: 100%;
}

input[type="range"] {
  border-radius: 2vh;
	color: rgba(190, 105, 213, 1);
	--thumb-height: 3vh;
	--track-height: 1vh;
	--track-color: rgba(186, 241, 255, 1);
	--brightness-hover: 180%;
	--brightness-down: 80%;
	--clip-edges: 0.55vh;
}


input[type="range"] {
  width: 100%;
	position: relative;
	background: #fff0;
	overflow: hidden;
}

/* === WebKit specific styles === */
input[type="range"],
input[type="range"]::-webkit-slider-runnable-track,
input[type="range"]::-webkit-slider-thumb {
	-webkit-appearance: none;
	transition: all ease 100ms;
	height: var(--thumb-height);
}

input[type="range"]::-webkit-slider-runnable-track,
input[type="range"]::-webkit-slider-thumb {
	position: relative;
}

input[type="range"]::-webkit-slider-thumb {
	--thumb-radius: calc((var(--thumb-height) * 0.5) - 1px);
	--clip-top: calc((var(--thumb-height) - var(--track-height)) * 0.5 - 0.5px);
	--clip-bottom: calc(var(--thumb-height) - var(--clip-top));
	--clip-further: calc(100% + 1px);
	--box-fill: calc(-100vmax - var(--thumb-width, var(--thumb-height)) + 0.07vh) 0 0
		100vmax currentColor;

	width: var(--thumb-width, var(--thumb-height));
	background-color: rgba(48, 37, 148, 1);
	box-shadow: var(--box-fill);
	border-radius: var(--thumb-width, var(--thumb-height));
  cursor: pointer;

	clip-path: polygon(
		100% -1px,
		var(--clip-edges) -1px,
		0 var(--clip-top),
		-100vmax var(--clip-top),
		-100vmax var(--clip-bottom),
		0 var(--clip-bottom),
		var(--clip-edges) 100%,
		var(--clip-further) var(--clip-further)
	);
}

input[type="range"]::-webkit-slider-runnable-track {
	background: linear-gradient(var(--track-color) 0 0) scroll no-repeat center /
		100% calc(var(--track-height) + 1px);
}

.set-square > .heading,
.set-type > .heading,
.set-roomcount > .heading{
  margin-top: 1.7em;
  display: flex;
  justify-content: space-between;
  text-align: center;
  align-items: center;
}

.set-square > .heading > .title,
.set-type > .heading > .title,
.set-roomcount > .heading > .title{
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 100%;
  /* identical to box height, or 108% */

  text-transform: uppercase;
}

.set-square > .heading > .square-value{
  font-size: 1.4em;
  font-family: 'Arial';
  font-style: normal;
  font-weight: 700;
}

.radio-container{
  margin-top: 0.7em;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 500;
  font-size: 1.1em;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.option > label{
  display: block;
  width: min-content;
  position: relative;
  line-height: normal;
  padding-left: 0.7em;
}

.option{
  display: inline-flex;
  align-items: center;
  padding-right: 3em;
}

input[type="radio"] {
  appearance: none;
  background-color: #fff;
  margin: 0;
  width: 3vh;
  height: 3vh;
  border: 0.4vh double black;
  border-radius: 100%;
  place-content: center;
}

input[type="radio"]:checked {
  background: rgba(48, 37, 148, 1);
  border: solid white;
  outline: solid #000;
  transform: scale(0.88);
}

.button-scroll-container{
  display: block;
  position: relative;
  left: 48vw;
  bottom: 8em;
  width: 10em;
  z-index: 4;
}

.button-scroll{
  background: url(./assets/scroll.svg);
  background-repeat: no-repeat;
  background-size: cover;
  width: 3.11vh;
  height: 3vh;
  transition: ease 0.5s;
}

.button-scroll:hover{
  cursor: pointer;
}

.button-scroll-container > label{
  position: relative;
  text-align: center;
  text-transform: uppercase;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  color: white;
  top: 10px;
  left: -9px;
}


.drop-down-container{
  display: none;
  position: absolute;
  left: calc((100vw - 25em - 56em)/2 + 9.7em);
  background-color: white;
  color: #5C39BA;
  margin-top: 1em;
  padding-left: 1em;
  opacity: 1;
  width: 8em;
  z-index: 4;
  line-height: 2em;
  border-radius: 7%;
}

.drop-down-container > div:hover{
  color: plum;
  cursor: pointer;
}


</style>
