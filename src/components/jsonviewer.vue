<template>
  <div>
    <label class="custom-input-label">
      <input
        class="custom-input"
        type="file"
        @change="loadJson"
      />
      Escolher arquivo JSON
    </label>
    <div v-if="jsonTree" class="file-name"> {{ fileName }}</div>
    <pre>{{ jsonTree }}</pre>
  </div>
</template>

  <style>

    .custom-input-label {
    position: relative;
    cursor: pointer;
    display: inline-block;
    padding: 0.5rem 1rem;
    background-color: rgb(37, 146, 9);
    color: #fff;
    border-radius: 0.25rem;
    }

    .custom-input {
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    width: 100%;
    height: 100%;
    cursor: pointer;
    }   


    .file-name {
        font-weight: 700;
        margin: 1rem;
        font-size: larger;
    }


    pre {
        font-weight: 400;
        color: rgb(37, 146, 9);
    }
  </style>
  
  <script>
  export default {
    data() {
      return {
        jsonTree: null,
      };
    },
    methods: {
      loadJson(event) {
        const file = event.target.files[0];
        if (file) {
          this.fileName = file.name;
          const reader = new FileReader();
          reader.onload = (e) => {
            try {
              const jsonData = JSON.parse(e.target.result);
              this.jsonTree = JSON.stringify(jsonData, null, 2);
            } catch (error) {
              console.error('Invalid JSON file');
            }
          };
          reader.readAsText(file);
        }
      },
    },
  };
  </script>
  