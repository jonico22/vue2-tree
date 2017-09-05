<template>
  <li>
    <div :class="{bold: isFolder}" @click="toggle" >
      <span v-if="isFolder">[{{open ? '-' : '+'}}]</span>
      <div v-if="isFolder" class="folder">
        <div v-if="open">
         <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Capa_1" x="0px" y="0px" width="20px" height="20px" viewBox="0 0 45 45" style="enable-background:new 0 0 45 45;" xml:space="preserve">
          <g>
            <path d="M44.45,13.436c-0.474-0.591-1.192-0.936-1.95-0.936H40c0-1.381-1.119-2.5-2.5-2.5H35V7.5C35,6.119,33.881,5,32.5,5h-30   C1.119,5,0,6.119,0,7.5v30C0,38.881,1.119,40,2.5,40h5h25h5c1.172,0,2.188-0.814,2.439-1.958l5-22.5   C45.105,14.802,44.925,14.027,44.45,13.436z M2.5,7.5h30V10H30c-1.381,0-2.5,1.119-2.5,2.5h-15c-1.172,0-2.186,0.814-2.44,1.958   c0,0-5.058,22.862-5.058,23.042H2.5V7.5L2.5,7.5z" fill="#FFDA44"/>
          </g>
          </svg>
        </div>
        <div v-else>
          <svg id="Capa_1" data-name="Capa 1" width="20px" height="20px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 416.81"><title>locked-folder</title><path d="M448,47.59H351.21A64,64,0,0,0,289,96.4H64a64,64,0,0,0-64,64v240a64,64,0,0,0,64,64H448a64,64,0,0,0,64-64V111.59A64,64,0,0,0,448,47.59Z" transform="translate(0 -47.59)" style="fill:#ffda44"/></svg>       
        </div>
      </div>  
      <span>{{model.name}}</span>
    </div>
    
    <ul v-show="open" v-if="isFolder" class="tree">
      <item class="child" 
        v-for="model in model.children"
        :model="model">
      </item>
    </ul>
    <span v-else class="file">
      <div>
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Capa_1" x="0px" y="0px" 
          viewBox="0 0 60 60" style="enable-background:new 0 0 60 60;" xml:space="preserve" width="15px" height="15px">
          <g>
            <path d="M42.5,22h-25c-0.552,0-1,0.447-1,1s0.448,1,1,1h25c0.552,0,1-0.447,1-1S43.052,22,42.5,22z" fill="#006DF0"/>
            <path d="M17.5,16h10c0.552,0,1-0.447,1-1s-0.448-1-1-1h-10c-0.552,0-1,0.447-1,1S16.948,16,17.5,16z" fill="#006DF0"/>
            <path d="M42.5,30h-25c-0.552,0-1,0.447-1,1s0.448,1,1,1h25c0.552,0,1-0.447,1-1S43.052,30,42.5,30z" fill="#006DF0"/>
            <path d="M42.5,38h-25c-0.552,0-1,0.447-1,1s0.448,1,1,1h25c0.552,0,1-0.447,1-1S43.052,38,42.5,38z" fill="#006DF0"/>
            <path d="M42.5,46h-25c-0.552,0-1,0.447-1,1s0.448,1,1,1h25c0.552,0,1-0.447,1-1S43.052,46,42.5,46z" fill="#006DF0"/>
            <path d="M38.914,0H6.5v60h47V14.586L38.914,0z M39.5,3.414L50.086,14H39.5V3.414z M8.5,58V2h29v14h14v42H8.5z" fill="#006DF0"/>
          </g>
          </svg>
        </div>
    </span>
  </li>
</template>

<script>
export default {
  name: 'item',
  props: {
    model: Object
  },
  data () {
    return {
      open: true
    }
  },
  computed: {
    isFolder: function () {
      return this.model.children &&
        this.model.children.length
    }
  },
  methods: {
    toggle: function (el) {
      console.log(el)
      if (this.isFolder) {
        this.open = !this.open
      }
    }
  }
}
</script>

<style lang="scss">
 
  .list{
    border-radius: .2rem;
    margin: 1rem .2rem;
    padding: 1rem;
    // background-color: red;
    display: block;
    // width: 100%;
    text-align: left;
  }
  .child{
    display: block;
    cursor: pointer;
    padding: .4em .2em .1em .6em;
    margin: 0;
    position: relative;
    ul {
      margin-left: 35px;
    }
  }
  .bold {
    font-weight: 800;
    cursor: pointer;
  }
  .folder {
    display: inline-block;
    vertical-align: middle;
  }
  .file {
    position: absolute;
    top: 8px;
    left: -12px;
  }
  .tree {
    margin-left: 10px;
    position: relative;
    margin-top: -5px;
  }
</style>
