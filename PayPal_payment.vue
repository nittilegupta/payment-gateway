<template>
  <div>
    <h1>Paypal Integration</h1>
    <div id="paypal-button-container"></div>
  </div>
</template>
<script>
import { defineComponent, ref, onMounted } from 'vue';
export default defineComponent({
  name: 'PayPalButton',
  setup() {
    const scriptLoaded = ref(false);
    onMounted(() => {
      const script = document.createElement('script');
//      Paypal Access key
      script.onload = () => {
        scriptLoaded.value = true;
        // Render PayPal button once the script is loaded
        window.paypal.Buttons().render('#paypal-button-container');
      };
      document.body.appendChild(script);
    });
    return {
      scriptLoaded
    };
  }
});
</script>
