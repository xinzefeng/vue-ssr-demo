<script type="text/ecmascript-6">
  export default {
    name: 'Tab',
    props: {
      index: {
        type: [Number, String],
        required: true
      },
      label: {
        type: String,
        default: 'tab'
      }
    },
    mounted(){
      this.$parent.panes.push(this)
    },
    computed:{
      active(){
        return this.$parent.value === this.index
      }
    },
    methods:{
      handleClick(){
        this.$parent.onChange(this.index)
      }
    },
    render() {
      const tab = this.$slots.label || <span>{this.label}</span>
      const classNames = {
        tab:true,
        active:this.active
      }
      return(
        <li class={classNames} on-click={this.handleClick}>{tab}</li>
      )
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .tab
    list-style none
    line-height 40px
    margin-right 30px
    position relative
    bottom -2px
    cursor pointer
    &.active
      border-bottom 2px solid blue
    &:last-child
      margin-right 0

</style>
