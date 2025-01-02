<script>
import globalConfigMixin from 'shared/mixins/globalConfigMixin';

const {
  LOGO_THUMBNAIL: logoThumbnail,
  BRAND_NAME: brandName,
  WIDGET_BRAND_URL: widgetBrandURL,
} = window.globalConfig || {};

export default {
  mixins: [globalConfigMixin],
  props: {
    disableBranding: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      globalConfig: {
        brandName,
        logoThumbnail,
        widgetBrandURL,
      },
    };
  },
};
</script>

<template>
  <div
    v-if="globalConfig.brandName && !disableBranding"
    class="px-0 py-3 flex justify-center"
  >
    <span class="branding--text justify-center items-center leading-3">
      {{ useInstallationName($t('POWERED_BY'), globalConfig.brandName) }}
    </span>
  </div>
  <div v-else class="p-3" />
</template>

<style scoped lang="scss">
@import 'widget/assets/scss/variables.scss';

.branding--text {
  color: $color-light-gray;
  font-size: $font-size-small;
  opacity: 0.9;
  text-align: center;
}
</style>
