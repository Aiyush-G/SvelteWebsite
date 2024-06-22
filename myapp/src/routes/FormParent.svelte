<script>
    import Form from './Form.svelte';
  
    /**
     * @param {{ detail: { name: any; email: any; }; }} event
     */
    function handleFormSubmit(event) {
      const { name, email } = event.detail;
      console.log('Form submitted with:', { name, email });
      // You can perform any action with the form data here, such as sending it to a server
    }
  </script>
  
  <Form on:submit={handleFormSubmit} />
  
  