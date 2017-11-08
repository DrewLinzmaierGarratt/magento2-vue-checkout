<template>
  <div>
    <BaseShippingStep/>

    <BasePaymentStep/>

    <BaseSummaryStep/>

    <BaseSuccessStep/>

    <BaseItems/>

    <BaseLoader/>
  </div>
</template>

<script>
import BaseShippingStep from './components/steps/BaseShippingStep.vue'
import BasePaymentStep from './components/steps/BasePaymentStep.vue'
import BaseSummaryStep from './components/steps/BaseSummaryStep.vue'
import BaseSuccessStep from './components/steps/BaseSuccessStep.vue'
import BaseItems from './components/BaseItems.vue'
import BaseLoader from './components/BaseLoader.vue'

export default {
  components: {
    BaseShippingStep,
    BasePaymentStep,
    BaseSummaryStep,
    BaseSuccessStep,
    BaseItems,
    BaseLoader
  },
  data() {
    return {
      baseUrl: baseUrl,
      config: this.$store.state.config
    }
  },
  methods: {
    returnError(element, cssClass, text) {
      // Initial validation in future
    }
  },
  beforeMount() {
    this.$store.commit('setCartId', this.config.quoteData.entity_id);
  },
  mounted() {
    this.$store.state.loader = false;
  }
}
</script>
