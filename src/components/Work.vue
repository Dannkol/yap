<template>

  <div class="container">
    <div class="search">
      <div class="input">
        <input type="text" placeholder="Search.." name="search">
        <button type="submit"><i class="fa fa-search"></i></button>
      </div>
      <div draggable="true" class="dropzone box" data-item="B" data-index-number="1">D</div>
      <div draggable="true" class="dropzone box" data-item="D" data-index-number="2">D</div>
      <div draggable="true" class="dropzone box" data-item="E" data-index-number="3">E</div>
    </div>
    <div class="content">
      <div id="slide1">
        <div class="card">
          <div class="titlecard">
            <h1>Silder 1</h1>
            <div>
              <Switchbtn />
            </div>
          </div>
          <div class="contenidocard">
            <div draggable="true" class="dropzone box" data-item="A" data-index-number="4">A</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
          </div>

        </div>

      </div>

      <div id="slide1">
        <div class="card">
          <div class="titlecard">
            <h1>Silder 2</h1>
            <div>
              <Switchbtn />
            </div>
          </div>
          <div class="contenidocard">
            <div draggable="true" class="dropzone box" data-item="C" data-index-number="5">PAN</div>
            <div draggable="true" class="dropzone box" data-item="Empy" data-index-number="0">Empy</div>
          </div>

        </div>

      </div>

      <div id="slide1">
        <div class="card">
          <div class="titlecard">
            <h1>Silder 3</h1>
            <div>
              <Switchbtn />
            </div>
          </div>
          <div class="contenidocard">
            <div draggable="true" class="dropzone box" data-item="B" >jabon</div>
            <div draggable="true" class="dropzone box" data-item="Empy" >Empy</div>
          </div>

        </div>

      </div>
      
      <div id="slide1">
        <div class="card">
          <div class="titlecard">
            <h1>Silder 4</h1>
            <div>
              <Switchbtn />
            </div>
          </div>
          <div class="contenidocard mt-4">
            <div draggable="true" class="dropzone box" data-item="B" >jabon</div>
            <div draggable="true" class="dropzone box" data-item="Empy" >Empy</div>
            <i class="icon-female" style="font-size: 20px" ></i>
          </div>

        </div>

      </div>
      
      <div id="slide1">
        <div class="card">
          <div class="titlecard">
            <h1>Silder 5</h1>
            <div>
              <Switchbtn />
            </div>
          </div>
          <div class="contenidocard">
            <div draggable="true" class="dropzone box" data-item="B" >jabon</div>
            <div draggable="true" class="dropzone box" data-item="Empy" >Empy</div>
          </div>

        </div>

      </div>
    </div>
  </div>




</template>

<script>

import Switchbtn from './Switchbtn.vue'

let dicCards = []

let draggedElement = null
let items

function handleDragStart(e) {

  this.style.opacity = "0.4"
  draggedElement = this

  e.dataTransfer.effectAllowed = "move"
  e.dataTransfer.setData("item", this.innerHTML)
}

function handleDragOver(e) {
  if (e.preventDefault)
    e.preventDefault()

  e.dataTransfer.dropEffect = "move"
  return false
}

function handleDragEnter(e) {
  this.classList.add("dragover")
}

function handleDragLeave(e) {
  this.classList.remove("dragover")
}

function handleDrop(e) {
  if (e.stopPropagation)
    e.stopPropagation()

  if (draggedElement != this) {
    draggedElement.innerHTML = this.innerHTML
    draggedElement.setAttribute("data-item", this.innerHTML)

    let replacedItem = e.dataTransfer.getData("item")
    this.innerHTML = replacedItem
    this.setAttribute("data-item", replacedItem)
  }

  return false
}

function arrayslide() {

  let slider = document.querySelectorAll('#slide1')

  let arraycard = []

  slider.forEach((data) => {
    data.childNodes.forEach((items) => {
      items.childNodes[1].childNodes.forEach((card) => {
        arraycard.push(card.innerText)
      })
      arraycard.push('/')
    })
  })

  let datos = []

  arraycard.join(' ').split('/').forEach((data) => {
    data != '' ?
      data.split(' ').forEach((items) => {
        datos.push(items)
      })
      :
      false;

  })


  let dicdatos = {
    silder1: [],
    silder2: [],
    silder3: []
  }
  let cont = 0

  for (let i = 0; i < datos.length; i++) {
    if (datos[i] == '') {
      cont++
    } if (cont == 0) {
      dicdatos.silder1.push(datos[i])
    } if (cont == 2) {
      datos[i] != '' ? dicdatos.silder2.push(datos[i]) : false;
    } if (cont == 4) {
      datos[i] != '' ? dicdatos.silder3.push(datos[i]) : false;
    }

  }
  dicCards = dicdatos
}


function handleDragEnd(e) {
  this.style.opacity = "1";

  items.forEach(function (item) {
    item.classList.remove("dragover");
  });

  arrayslide()
  console.log(dicCards)
}




document.addEventListener("DOMContentLoaded", event => {

  items = document.querySelectorAll(".container .box");


  items.forEach(function (item) {

    item.addEventListener("dragstart", handleDragStart);
    item.addEventListener("dragenter", handleDragEnter);
    item.addEventListener("dragover", handleDragOver);
    item.addEventListener("dragleave", handleDragLeave);
    item.addEventListener("drop", handleDrop);
    item.addEventListener("dragend", handleDragEnd);

  });

});


export default {
  name: 'Work',
  components: {
    Switchbtn
  }

}
</script>

<style scoped>
.search {
  width: 310px;
  height: 90vh;
  display: flex;
  flex-direction: column;
  gap: 20px;

}

.search .input {
  display: inline-flex;
}

input[type=text] {
  padding: 6px;
  margin-top: 8px;
  font-size: 17px;
  border: none;
}

button {
  padding: 6px 10px;
  margin-top: 8px;
  margin-right: 16px;
  background: #ddd;
  font-size: 17px;
  border: none;
  cursor: pointer;
}

.card {
  margin-top: 10px;
  width: 260px;
  height: 85vh;
  display: flex;
  gap: 20px;
  flex-wrap: nowrap;
  overflow: auto;
  overflow-x: hidden;
  background-color: #DFE4E8;
}

.titlecard {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  height: 65px;
  background-color: #adadad;
  padding: 0 10px;
  width: 94%;
  position: sticky;
  top: 0;
}

.card .titlecard div {
  margin-top: 35px;
}

.contenidocard {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin: 0 0 5px 5px;
}

.container {
  display: flex;
  gap: 15px;
  flex-direction: row;
  padding-left: 10px;
  padding-right: 10px;
  justify-content: space-between;
  width: 100vw;
}

.dropzone {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 34px;
  border: 2px solid #1576C1;
  background-color: #94DBFD;
  border-radius: 10px;
  transition: transform 0.5s;
}

.dropzone.dragover {
  transform: scale(0.9);
}

.box {
  width: 230px;
  height: 100px;
  cursor: move;
  user-select: none;
  margin-left: 10px;
}

.box[data-item="A"] {
  background-color: #FFDCA9;
  border-color: #F97D02;
}

.box[data-item="B"] {
  background-color: #BCF8B9;
  border-color: #3CB43C;
}

.box[data-item="D"] {
  background-color: #BCF8B9;
  border-color: #acb43c;
}

.box[data-item="E"] {
  background-color: #f8efb9;
  border-color: #b43c3c;
}


.box[data-item="Empy"] {
  background-color: #e6ffe4;
  border-color: #eefdee;
}

.content{
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  gap : 20px;
  overflow: auto;
  overflow-y: hidden;
}
</style>