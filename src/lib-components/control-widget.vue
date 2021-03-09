<script>
export default /*#__PURE__*/ {
  name: "ControlWidget", // vue component name
  /* eslint-disable */
  props: ["change"],
  data() {
    return {
      status: "",
      statusLight: "",
      position: 0,
      receivePosition: this.change,
    };
  },
  watch: {
    change: function (val) {
      return (this.receivePosition = val);
    },
  },
  computed: {
    /* eslint-disable */
    margin() {
      if (this.receivePosition === true) {
        this.position = 80;
        this.status = "ON";
        this.statusLight = "rgb(52, 211, 65)";
      } else if (this.receivePosition === false) {
        this.position = -80;
        this.status = "OFF";
        this.statusLight = "rgb(232, 2, 2)";
      }
      return this.position;
    },
  },
  methods: {
    switchPosition() {
      this.receivePosition = !this.receivePosition;
      this.$emit("buttonClick", this.receivePosition);
    },
  },
};
</script>

<template>
  <div class="background">
    <div class="status">
      {{ status }}
    </div>
    <div
      class="light"
      :style="{
        backgroundColor: statusLight,
        boxShadow: '0 0 20px ' + statusLight,
        transition: '0.3s',
      }"
    />
    <div class="out">
      <div
        class="button"
        :style="{ marginLeft: margin + 'px' }"
        @click="switchPosition()"
      >
      </div>
      <div class="on">|</div>
      <div class="off">O</div>
    </div>
  </div>
</template>

<style scoped>
.background {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif !important;
  position: relative !important;
  width: 220px !important;
  height: 105px !important;
  background-color: rgb(145, 145, 145) !important;
  border-radius: 10px !important;
  box-shadow: 0 0 15px grey !important;
  user-select: none !important;
  padding-top: 15px !important;
}

.status {
  width: 100% !important;
  height: 100% !important;
  position: absolute !important;
  align-items: center !important;
  text-align: center !important;
  font-size: 21px !important;
  font-weight: bold !important;
  color: white !important;
}

.light {
  width: 120px !important;
  height: 25px !important;
  border-radius: 2px !important;
  margin: 0 auto !important;
  text-align: center !important;
}

.out {
  position: relative !important;
  display: flex !important;
  justify-content: center !important;
  align-items: center !important;
  padding-top: 20px !important;
}

.on {
  width: 70px !important;
  height: 40px !important;
  display: flex !important;
  justify-content: center !important;
  align-items: center !important;
  background-color: rgb(52, 211, 65) !important;
  border-bottom-left-radius: 10px !important;
  border-top-left-radius: 10px !important;
  font-size: 25px !important;
  font-weight: bold !important;
  color: white !important;
  box-shadow: 0 0 5px rgb(52, 211, 65) !important;
  border: 2px solid rgb(52, 255, 65) !important;
}

.off {
  width: 70px !important;
  height: 40px !important;
  display: flex !important;
  justify-content: center !important;
  align-items: center !important;
  background-color: rgb(232, 2, 2) !important;
  border-bottom-right-radius: 10px !important;
  border-top-right-radius: 10px !important;
  font-size: 30px !important;
  font-weight: bold !important;
  color: white !important;
  box-shadow: 0 0 5px rgb(232, 2, 2) !important;
  border: 2px solid rgb(255, 56, 56) !important;
}

.button {
  position: absolute !important;
  width: 90px !important;
  height: 50px !important;
  background-color: rgb(89, 89, 89) !important;
  border-radius: 10px !important;
  transition: 0.3s !important;
  box-shadow: inset 0 0 15px rgb(42, 42, 42) !important;
  border: 2px solid rgb(0, 0, 0) !important;
  cursor: pointer !important;
  text-align: center !important;
}
</style>
