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
  mounted() {
    this.switchControl();
  },
  methods: {
    switchPosition() {
      this.receivePosition = !this.receivePosition;
      this.$emit("buttonClick", this.receivePosition);
    },
    switchControl() {
      if (this.receivePosition === true) {
        this.receivePosition = false;
        this.position = 80;
        this.buton = document.querySelector("div.button");
        this.buton.style.marginLeft = `${this.position}px`;
      } else if (this.receivePosition === false) {
        this.receivePosition = true;
        this.position = -80;
        this.buton = document.querySelector("div.button");
        this.buton.style.marginLeft = `${this.position}px`;
      }
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
        <div class="draw">||</div>
      </div>
      <div class="on">|</div>
      <div class="off">O</div>
    </div>
  </div>
</template>

<style scoped>
.background {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  position: relative;
  width: 250px;
  height: 125px;
  background-color: rgb(145, 145, 145);
  border-radius: 10px;
  box-shadow: 0 0 15px grey;
  user-select: none;
  padding-top: 20px;
}

.status {
  width: 100%;
  height: 100%;
  position: absolute;
  align-items: center;
  text-align: center;
  font-size: 21px;
  font-weight: bold;
  color: white;
}

.light {
  width: 120px;
  height: 25px;
  border-radius: 2px;
  margin: 0 auto;
  text-align: center;
}

.out {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 20px;
}

.on {
  width: 90px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(52, 211, 65);
  border-bottom-left-radius: 20px;
  border-top-left-radius: 20px;
  font-size: 30px;
  font-weight: bold;
  color: white;
  box-shadow: 0 0 5px rgb(52, 211, 65);
  border: 2px solid rgb(52, 255, 65);
}

.off {
  width: 90px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(232, 2, 2);
  border-bottom-right-radius: 20px;
  border-top-right-radius: 20px;
  font-size: 30px;
  font-weight: bold;
  color: white;
  box-shadow: 0 0 5px rgb(232, 2, 2);
  border: 2px solid rgb(255, 56, 56);
}

.button {
  position: absolute;
  width: 110px;
  height: 50px;
  background-color: rgb(89, 89, 89);
  border-radius: 20px;
  transition: 0.3s;
  box-shadow: 0 0 10px rgb(41, 41, 41);
  border: 2px solid rgb(0, 0, 0);
  cursor: pointer;
  text-align: center;
  padding-top: 7px;
}

.draw {
  margin-top: 3px;
  color: rgb(121, 121, 121);
  font-size: 30px;
}
</style>
