<template>
  <custom-button
    :class="classes"
    :style="styles"
    :href="href"
    :link="link"
    class="mdc-fab"
    v-on="listeners">
    <span
      :class="{'material-icons': icon}"
      class="mdc-fab__icon"
    >
      <slot>{{ icon }}</slot>
    </span>
    <span class="mdc-fab__label">{{ label }}</span>
  </custom-button>
</template>

<script>
import { DispatchEventMixin, CustomButtonMixin } from '../base'
import { RippleMixin } from '../ripple'

export default {
  name: 'mdc-fab',
  mixins: [DispatchEventMixin, CustomButtonMixin, RippleMixin],
  props: {
    icon: String,
    mini: Boolean,
    absolute: Boolean,
    fixed: Boolean,
    label: String
  },
  data() {
    return {
      classes: {
        'material-icons': this.icon,
        'mdc-fab--mini': this.mini,
        'mdc-fab--absolute': this.absolute,
        'mdc-fab--fixed': this.fixed,
        'mdc-fab--extended': this.label
      },
      styles: {}
    }
  },
  watch: {
    // icon() {
    //   this.$set(this.classes, 'material-icons', this.icon)
    // },
    mini() {
      this.$set(this.classes, 'mdc-fab--mini', this.mini)
    },
    label() {
      this.$set(this.classes, 'mdc-fab--extended', true)
    }
  }
}
</script>
