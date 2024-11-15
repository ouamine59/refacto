< <template>
    <div class="input-wrapper">
      <label v-if="label" :for="id">{{ label }}</label>
      <input
        :id="id"
        :type="type"
        :value="modelValue"
        :placeholder="placeholder"
        :class="{ 'is-invalid': showError }"
        @input="updateValue($event.target.value)"
        @blur="handleBlur"
      />
      <span v-if="showError" class="error-message">{{ errorMessage }}</span>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      modelValue: String,
      label: String,
      type: {
        type: String,
        default: 'text',
      },
      placeholder: String,
      id: String,
      errorMessage: String,
      showError: Boolean,
    },
    emits: ['update:modelValue', 'blur'],
    methods: {
      updateValue(value) {
        this.$emit('update:modelValue', value);
      },
      handleBlur() {
        this.$emit('blur');
      },
    },
  };
  </script>
  
  <style scoped>
  .input-wrapper {
    display: flex;
    flex-direction: column;
    margin-bottom: 1rem;
  }
  
  input {
    padding: 0.5rem;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  
  .is-invalid {
    border-color: red;
  }
  
  .error-message {
    color: red;
    font-size: 0.875rem;
    margin-top: 0.25rem;
  }
  </style> 