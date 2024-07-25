<!-- ContactForm.vue -->
<template>
    <div v-if="isVisible" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content">
        <button class="close-button" @click="closeModal">&times;</button>
        <h2>Contact Us</h2>
        <form @submit.prevent="handleSubmit">
          <div class="form-group">
            <label for="name">Name:</label>
            <input type="text" id="name" v-model="form.name" required />
          </div>
          <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="form.email" required />
          </div>
          <div class="form-group">
            <label for="message">Message:</label>
            <textarea id="message" v-model="form.message" required></textarea>
          </div>
          <button type="submit">Send</button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      isVisible: {
        type: Boolean,
        required: true
      }
    },
    data() {
      return {
        form: {
          name: '',
          email: '',
          message: ''
        }
      };
    },
    methods: {
      closeModal() {
        this.$emit('close');
      },
      handleSubmit() {
        // Handle form submission logic
        console.log(this.form);
        this.closeModal();
      }
    }
  };
  </script>
  
  <style scoped>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }
  
  .modal-content {
    background: #fff;
    padding: 2em;
    border-radius: 10px;
    position: relative;
    width: 90%;
    max-width: 500px;
  }
  
  .close-button {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    font-size: 1.5em;
    cursor: pointer;
  }
  
  .form-group {
    margin-bottom: 1em;
  }
  
  label {
    display: block;
    margin-bottom: 0.5em;
  }
  
  input,
  textarea {
    width: 100%;
    padding: 0.5em;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  button {
    background-color: #007bff;
    color: #fff;
    border: none;
    padding: 0.75em 1.5em;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  </style>
  