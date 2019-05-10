<template>
  <div class="el-tabs__active-bar" :class="fixActiveBarClass" :style="barStyle">
    <div class="el-tabs__custom-active-bar" :style="customBarStyle"></div>
  </div>
</template>
<script>
  import { arrayFind } from 'element-ui/src/utils/util';
  export default {
    name: 'TabBar',

    props: {
      tabs: Array,
      activeWidth: [Number, String],
      hasItemPadding: { // 是否需要el-tabs__item padding(20px) 默认为false
        type: Boolean,
        default: () => (false)
      }
    },

    inject: ['rootTabs'],

    computed: {
      barStyle: {
        get() {
          let style = {};
          let offset = 0;
          let tabSize = 0;
          const sizeName = ['top', 'bottom'].indexOf(this.rootTabs.tabPosition) !== -1 ? 'width' : 'height';
          const sizeDir = sizeName === 'width' ? 'x' : 'y';
          const firstUpperCase = str => {
            return str.toLowerCase().replace(/( |^)[a-z]/g, (L) => L.toUpperCase());
          };
          this.tabs.every((tab, index) => {
            let $el = arrayFind(this.$parent.$refs.tabs || [], t => t.id.replace('tab-', '') === tab.paneName);
            if (!$el) { return false; }

            if (!tab.active) {
              offset += $el[`client${firstUpperCase(sizeName)}`];
              return true;
            } else {
              tabSize = $el[`client${firstUpperCase(sizeName)}`];
              // 因改为固定宽度下划线选中状态，不需进行padding计算，item内部控制即可
              if (sizeName === 'width' && this.tabs.length > 1 && this.hasItemPadding) {
                tabSize -= (index === 0 || index === this.tabs.length - 1) ? 20 : 40;
              }
              return false;
            }
          });

          // 修正固定宽度计算后offset的值
          if (sizeName === 'width' && offset !== 0 && this.hasItemPadding) {
            offset += 20;
          }
          const transform = `translate${firstUpperCase(sizeDir)}(${offset}px)`;
          style[sizeName] = tabSize + 'px';
          style.transform = transform;
          style.msTransform = transform;
          style.webkitTransform = transform;

          return style;
        }
      },
      customBarStyle: {
        cache: false,
        get() {
          let style = {};
          if (this.activeWidth && this.activeWidth >= 0) {
            style.width = this.activeWidth + 'px';
          }
          return style;
        }
      },
      fixActiveBarClass() {
        let classList = {
          [`is-${ this.rootTabs.tabPosition }`]: true
        };
        if (this.activeWidth) {
          classList['el-tabs__fix-width-active-bar'] = true;
        }
        return classList;
      }
    }
  };
</script>
