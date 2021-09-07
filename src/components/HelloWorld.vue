<template>
  <div class="counter">
    <div class="counter_wrapper">
      <p>Insert text below</p>
      <textarea
        v-on:click="hideRes"
        v-model="text"
        cols="30"
        rows="10"
        placeholder="Type something"
      ></textarea>
      <div class="button">
        <button type="button" v-on:click="toggleRes">Calculate Words</button>
      </div>
      <p v-bind:revele="revele" v-if="revele">
        the text contains {{ words }} words.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      text: "",
      revele: false,
    };
  },

  computed: {
    words() {
      const trimmedText = this.text.trim();

      return trimmedText.length === 0 ? 0 : trimmedText.split(" ").length;
    },
  },
  methods: {
    toggleRes: function() {
      this.revele = !this.revele;
    },
    hideRes: function() {
      this.revele = false;
    },
  },
};
</script>

<style scoped>
.counter {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.counter_wrapper {
  width: 70%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.counter_wrapper p {
  color: black;
  font-family: sans-serif;
  font-size: 1.3em;
  text-transform: uppercase;
}

.counter_wrapper textarea {
  height: 100%;
  width: 100%;
  border: 1px solid lightgrey;
  border-radius: 6px;
  outline: none;
  padding: 0 15px;
  font-size: 17px;
  padding-top: 10px;
  resize: none;
}

.counter_wrapper .button {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 47px;
  width: 100%;
  margin: 0;
  margin: 20px 0;
}

.counter_wrapper .button button {
  width: 60%;
  height: 100%;
  border: 2px solid #6c5cf4;
  background: #6c5cf4;
  color: #fff;
  font-size: 20px;
  font-weight: 500;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.counter_wrapper .button button:hover {
  color: #6c5cf4;
  background: none;
}
</style>
