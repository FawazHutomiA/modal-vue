<template>
  <div class="center">
    <h2>Click this button bellow to show Modal</h2>
    <button id="myBtn" @click="openModal">Open Modal</button>
  </div>
  <Modal v-if="isModalOpen" @close-modal="closeModal" :payload="modalData" />
</template>

<script>
import { onMounted, reactive, ref } from "vue";
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  setup() {
    const isModalOpen = ref(false);
    const modalData = reactive({
      modal_header: "Modal Header", 
      modal_content: 100,
      modal_footer: "Modal Footer"
    })

    onMounted(() => {
      window.addEventListener("keydown", function (e) {
        if (e.key === "Escape") {
          isModalOpen.value = false;
        }
      });
    });

    function openModal() {
      isModalOpen.value = true;
    }

    function closeModal() {
      isModalOpen.value = false;
    }

    return {
      isModalOpen,
      modalData,
      openModal,
      closeModal,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

div button {
  font-size: 17px;
  background-color: #008cba;
  border: none;
  padding: 15px 32px;
  cursor: pointer;
  color: white;
  border-radius: 4px;
  transition-duration: 0.4s;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.4);
}

div button:hover {
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.24),
    0 17px 50px 0 rgba(0, 0, 0, 0.19);
}
</style>
