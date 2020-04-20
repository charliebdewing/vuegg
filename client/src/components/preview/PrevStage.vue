<template>
  <div :id="page.id" :style="pageStyles" :class="[page.classes]" :key="breakpoint">
    <prev-stage-el
      v-for="element in page.children"
      :key="element.id"
      :elem="element"
      :breakpoint="breakpoint">
    </prev-stage-el>
  </div>
</template>


<script>
import PrevStageEl from './PrevStageEl'

export default {
  name: 'prev-stage',
  components: { PrevStageEl },
  props: ['page', 'breakpoint'],
  computed: {
    pageStyles () {
      let styles = {
        ...this.page.styles,
        width: (typeof this.page.width === 'string') ? this.page.width : (this.page.width + 'px'),
        minHeight: '100%'
      }
      // height: (typeof this.page.height === 'string') ? this.page.height : (this.page.height + 'px'),

      styles = {
        ...styles,
        ...(this.breakpoint === 'sm' || this.breakpoint === 'md')
          ? {display: 'flex', flexWrap: 'wrap', justifyContent: 'center', alignItems: 'center', alignContent: 'center'}
          : {}}

      return styles
    }
  }
}
</script>
