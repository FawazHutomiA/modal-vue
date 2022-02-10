<template>
  <div id="myModal" class="modal" @click="closeModal">
    <div class="modal-content">
      <div class="modal-header">
        <span class="close" @click="closeModal">&times;</span>
        <h2>{{ payload.modal_header }}</h2>
      </div>
      <div class="modal-body">
        <div v-for="item in payload.modal_content" :key="item">
            <h1> {{ item }}. Fawaz Hutomi A  </h1>
        </div>
      </div>
      <div class="modal-footer">
        <h3>{{ payload.modal_footer }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    payload: {
      type: Object,
    },
  },
  setup(_, { emit }) {
    function closeModal() {
      emit("close-modal");
    }

    return {
      closeModal,
    };
  },
};
</script>

<style scoped>
.center {
  text-align: center;
}

.modal {
  display: block;
  position: fixed;
  z-index: 1;
  padding-top: 100px;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  position: relative;
  background-color: #fefefe;
  margin: auto;
  padding: 0;
  border: none;
  width: 60%;
  -webkit-animation-name: animatetop;
  -webkit-animation-duration: 0.4s;
  animation-name: animatetop;
  animation-duration: 0.4s;
}

@-webkit-keyframes animatetop {
  from {
    top: -100px;
    opacity: 0;
  }
  to {
    top: 0;
    opacity: 1;
  }
}

@keyframes animatetop {
  from {
    top: -100px;
    opacity: 0;
  }
  to {
    top: 0;
    opacity: 1;
  }
}

.close {
  color: white;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}

.modal-header {
  padding: 2px 16px;
  background-color: #008cba;
  color: white;
  text-align: center;
}

.modal-body {
  padding: 2px 16px;
  height: 300px;
  overflow: auto;
}

.modal-footer {
  padding: 2px 16px;
  background-color: #008cba;
  color: white;
  text-align: center;
}
</style>
