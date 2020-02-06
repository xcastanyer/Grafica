<template>
  <div class="home">
    <img alt src />
    <canvas id="myCanvas" :width="ancho" :height="alto" style="border:1px solid #000000;"></canvas>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "grafica",
  props: ["alto", "ancho"],
  mounted() {
    var c = document.getElementById("myCanvas");
    this.contexto = c.getContext("2d");
    //this.dibujarLinea(10,0,100,200);
    this.dibujarLinea(this.ancho / 2, 0, this.ancho / 2, this.alto);
    this.dibujarLinea(0, this.alto / 2, this.ancho, this.alto / 2);
    this.escribirTexto(10, this.alto / 2 - 10, "x");
    this.escribirTexto(this.ancho / 2 - 15, 10, "y");

    for (let index = 0; index < this.alto; index += 10) {
      this.dibujarLinea(
        this.ancho / 2 - 5,
        0 + index,
        this.ancho / 2,
        0 + index
      );
    }
    for (let index = 0; index < this.ancho; index += 10) {
      this.dibujarLinea(0 + index, this.alto / 2 - 5, 0 + index, this.alto / 2);
    }
  },
  data() {
    return {
      contexto: null
    };
  },
  methods: {
    dibujarLinea(a, b, c, d) {
      this.contexto.moveTo(a, b);
      this.contexto.lineTo(c, d);
      this.contexto.stroke();
    },
    escribirTexto(a, b, texto) {
      this.contexto.font = "15px Arial";
      this.contexto.fillText(texto, a, b);
      this.contexto.stroke();
    }
  }
};
</script>
