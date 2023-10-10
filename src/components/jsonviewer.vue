<template>
    <div>
      <input type="file" @change="loadJson" />
      <pre>{{ jsonTree }}</pre>
    </div>
  </template>
  
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
  