<template>
  <div class="baner">

    <div class="titulo">Tecnology Net</div>
    <button class="carrito" @click="mostrarCarritoModal">🛒 {{ carrito.length }}</button>

    <transition name="modal-fade">
      <div class="carrito-overlay" v-if="carritoVisible">
        <div class="carrito-modal">
          <button class="cerrar-modal" @click="ocultarCarritoModal">Cerrar</button>
          <h2>Productos en el carrito:</h2>


          <div class="grid">
            <div class="carrito-producto" v-for="(item, index) in carrito" :key="index">
              <img :src="item.producto.img" alt="Producto en el carrito">
              <div class="carrito-producto-info">
                <p>{{ item.producto.text }}</p>
                <p>{{ item.producto.text2 }}</p>
                <p>Cantidad: {{ item.cantidad }}</p>
                <div class="botos">
                  <button class="suma" @click="aumentarCantidad(item)">+</button>
                  <button class="resta" @click="disCantidad(item)">-</button>
                  <button class="elimina" @click="eliminarProducto(index)">🗑️</button>
                </div>
              </div>
            </div>
          </div>
          <p>Total: {{ calcularTotal() }}</p>
          <button class="vaciar" @click="vaciar">vaciar carrito</button>
        </div>
      </div>
    </transition>

  </div>

  <div class="cards">
    <div v-for="(tar, index) in tarjetas" :key="index" class="card">

      <div class="face front">

        <h1 class="text1">{{ tar.text }}</h1>
        <img :src="tar.img">
        <h5 class="text2">{{ tar.text2 }}</h5>

      </div>

      <div class="face back">
        <h4 class="caracteristicas">{{ tar.Caracteristica1 }}</h4>
        <h4 class="caracteristicas">{{ tar.Caracteristica2 }}</h4>
        <h4 class="caracteristicas">{{ tar.Caracteristica3 }}</h4>
        <h4 class="caracteristicas">{{ tar.Caracteristica4 }}</h4>
        <h4 class="caracteristicas">{{ tar.Caracteristica5 }}</h4>
      </div>

      <div class="botones">
        <button class="button2" @click="agregarAlCarrito(tar)">Agregar al 🛒</button>
      </div>

    </div>
  </div>
</template>



<script setup>

const carrito = ref([]);
const encontrarIndiceProducto = (producto) => carrito.value.findIndex(item => item.producto.text === producto.text);


const agregarAlCarrito = (producto) => {
  const indiceExistente = encontrarIndiceProducto(producto);

  if (indiceExistente !== -1) {
    carrito.value[indiceExistente].cantidad++;
  } else {
    carrito.value.push({ producto: producto, cantidad: 1 });
  }
};

const ocultarCarritoModal = () => {
  carritoVisible.value = false;
};

const mostrarCarritoModal = () => {
  carritoVisible.value = true;
};

const carritoVisible = ref(false);

const aumentarCantidad = (item) => {
  item.cantidad++;
};
const disCantidad = (item) => {
  item.cantidad--;
};

const eliminarProducto = (index) => {
  carrito.value.splice(index, 1);
};
const vaciar = (index) => {
  carrito.value.splice(index, 12);
};


const calcularTotal = () => {
  let total = 0;
  for (const item of carrito.value) {
    total += item.producto.precio * item.cantidad;
  }
  return total;
};

import { ref } from 'vue';
const tarjetas = ref([

  {
    img: 'src/assets/images/img1.jpg',
    text: "Xiaomi redmi Note 10s",
    text2: "Precio: 950.000",
    precio: 950000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img2.jpg',
    text: "Xiaomi 11T Pro",
    text2: "Precio: 1.350.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img1.jpg',
    text: "Xiaomi redmi Note 10",
    text2: "Precio: 950.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img2.jpg',
    text: "Xiaomi 11T Pr",
    text2: "Precio: 1.350.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img1.jpg',
    text: "Xiaomi redmi Nte 10s",
    text2: "Precio: 950.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img2.jpg',
    text: "Xiami 11T Pro",
    text2: "Precio: 1.350.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img1.jpg',
    text: "Xiaomi redm Note 10s",
    text2: "Precio: 950.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img2.jpg',
    text: "Xiaomi 1 Pro",
    text2: "Precio: 1.350.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img1.jpg',
    text: "Xiaomi remi ote 10s",
    text2: "Precio: 950.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img2.jpg',
    text: "Xiaomi 11T o",
    text2: "Precio: 1.350.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img1.jpg',
    text: "Xiami edmi Note 10s",
    text2: "Precio: 950.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

  {
    img: 'src/assets/images/img2.jpg',
    text: "Xaomi 11T Pro",
    text2: "Precio: 1.350.000",
    precio: 1350000,
    Caracteristica1: "Memoria interna: 126GB",
    Caracteristica2: "Memoria Ram: 6GB",
    Caracteristica3: "Bateria: 5.000 mAh",
    Caracteristica4: "Procesador: Helio 95",
    Caracteristica5: "Optacore: (8 Nucleos)"
  },

])
</script>

<style scoped>
.baner {
  width: 100%;
  height: 150px;
  background-color: rgb(255, 47, 113);
  display: flex;
  justify-content: center;
  margin: 0%;
  gap: 20px;
}

.titulo {
  color: white;
  font-size: 40px;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  position: relative;
  top: 29%;
}

.carrito {
  font-size: 30px;
  background-color: rgb(255, 47, 113);
  border: 0px;

}

.carrito-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;

}



.card {
  border-radius: 30px;
  box-shadow: 1px 2px 10px 4px rgb(95, 92, 92);
  width: 330px;
  height: 540px;
}


img {
  width: 50%;
  height: 74%;
}

.cards {
  margin: 3%;
  display: flex;
  flex-wrap: wrap;
  gap: 40px;
  justify-content: space-around;
  text-align: center;
  padding: 0px 100px;

}

.card .face {
  backface-visibility: hidden;
  overflow: hidden;
  transition: .5s;

}

.card .front {
  transform: perspective(600px) rotateY(0deg);
  position: relative;
  top: 10%;
}

.card .back {
  transform: perspective(600px) rotateY(180deg);
  position: relative;
  bottom: 30%;
  background-color: antiquewhite;
  border: 2px solid black;
  height: 200px;
  text-align: center;
}

.card:hover .front {
  transform: perspective(600px) rotateY(180deg);
}

.card:hover .back {
  transform: perspective(600px) rotateY(360deg);
}

.button2 {
  background-color: rgb(217, 160, 52);
  border: 0px;
  width: 120px;
  height: 50px;
  border-radius: 20px;
  position: relative;
  bottom: 95%;
}

.vaciar {
  background-color: rgb(217, 160, 52);
  border: 0px;
  width: 120px;
  height: 50px;
  border-radius: 20px;

}

.botos {
  display: grid;
  grid-template-columns: 33% 33% 33%;
  justify-items: center;
}

.suma {
  background-color: rgb(91, 217, 52);
  border: 0px;
  border-radius: 20px;
  width: 40px;
  height: 35px;
}

.resta {
  background-color: rgb(247, 184, 48);
  border: 0px;
  border-radius: 20px;
  width: 40px;
  height: 35px;
}

.elimina {
  background-color: rgb(255, 0, 0);
  border: 0px;
  border-radius: 20px;
  width: 40px;
  height: 35px;
}

.text1 {
  font-size: 30px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  color: rgb(255, 47, 113);

}

.text2 {
  font-size: 25px;
  position: relative;
  top: 3%;
}

.botones {
  display: flex;
  justify-content: center;
}



.cerrar-modal {
  background-color: #dc3545;
  cursor: pointer;
}


.carrito-modal {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  text-align: center;
  width: 1000px;
  max-height: 70vh; 
  overflow-y: auto; 
}

.grid {
  margin: 5%;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-around;
  text-align: center;
  gap: 20px;
}

.modal-fade-leave-active {
  transition: opacity 0.5s;
}
</style>





