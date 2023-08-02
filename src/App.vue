<script>
import { StreamBarcodeReader } from "vue-barcode-reader";

export default {
  name: "App",
  components: {
    StreamBarcodeReader,
  },
  data: () => ({
    result: "",
  }),

  methods: {
    onDecode(decoded) {
      console.log(decoded);
      this.result = decoded;
    },
    onLoaded() {
      console.log("Barcode reader loaded.");
    },
  },
};
</script>

<template>
  <div v-if="!result">
    <StreamBarcodeReader @decode="onDecode" @loaded="onLoaded">
    </StreamBarcodeReader>
  </div>
  <div v-else>
    <h1>VIN : {{ result }}</h1>
    <button @click="result = ''">Reset</button>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
