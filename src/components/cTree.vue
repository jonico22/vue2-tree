<template>
  <li>
    <div :class="{bold: isFolder}" @click="toggle" >
      <span v-if="isFolder">[{{open ? '-' : '+'}}]</span>
      <div v-if="isFolder" class="folder">
        <div v-if="open">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 62.96 36.35" width="30px" height="30px"><title>Asset 26ldpi</title><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M40.74,4.4H20.34L15.95,0H4.68A4.68,4.68,0,0,0,0,4.68V31.43a4.92,4.92,0,0,0,4.92,4.92H40.74a4.92,4.92,0,0,0,4.92-4.92V9.31A4.92,4.92,0,0,0,40.74,4.4Z" style="fill:#ff9800"/><path d="M39.44,36.35H3.62c-2.72,0-3.48-1.67-1.71-3.72L16.35,15.89a12.2,12.2,0,0,1,8.13-3.72H60.3c2.72,0,3.48,1.67,1.71,3.72L47.57,32.63A12.2,12.2,0,0,1,39.44,36.35Z" style="fill:#ffb74d"/><path d="M21.24,31.1H19.11c-.91,0-1.17-.56-.57-1.25l1.39-1.61A4.1,4.1,0,0,1,22.66,27c2.64.11,2.79,1.18,1.31,2.86A4.1,4.1,0,0,1,21.24,31.1Z" style="fill:#fff"/><path d="M26.7,31.18c-.83,0-1.13-.48-.66-1.12,2.23-3.05,1.5-4.64-2.32-5-.83-.08-.94-.69-.26-1.37a4,4,0,0,1,2.75-1.09c5.24.49,6.38,3,3.29,7.21a4,4,0,0,1-2.63,1.35Z" style="fill:#fff"/><path d="M33.4,31.29c-.91,0-1.23-.52-.72-1.22C37.15,24,35.62,20.63,28,19.92c-.91-.08-1-.75-.28-1.49a4.35,4.35,0,0,1,3-1.19c9.14.86,11.13,5.2,5.74,12.57a4.37,4.37,0,0,1-2.87,1.48Z" style="fill:#fff"/></g></g></svg>
        </div>
        <div v-else>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 45.65 36.35" width="25px" height="25px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M25.38,9.44,15.95,0H4.68A4.68,4.68,0,0,0,0,4.68V9.44Z" style="fill:#ff9800"/><rect y="4.4" width="45.65" height="31.95" rx="4.92" ry="4.92" style="fill:#ffb74d"/><path d="M18,29.42H15.88a1.65,1.65,0,0,1-1.65-1.65V25.64A1.65,1.65,0,0,1,15.88,24c2.74.15,3.81,1.56,3.78,3.78A1.65,1.65,0,0,1,18,29.42Z" style="fill:#fff"/><path d="M23.53,29.51A1.63,1.63,0,0,1,21.9,28c-.4-4-2.51-6.13-6.63-6.6a1.63,1.63,0,0,1,.37-3.25c5.66.65,9,3.94,9.51,9.53a1.63,1.63,0,0,1-1.47,1.79Z" style="fill:#fff"/><path d="M30.33,29.66a1.78,1.78,0,0,1-1.77-1.61c-.8-8.08-5.2-12.47-13.44-13.42a1.78,1.78,0,1,1,.41-3.54C25.41,12.23,31.14,18,32.11,27.7a1.78,1.78,0,0,1-1.6,2Z" style="fill:#fff"/></g></g></svg>
        </div>
      </div>  
      <span>{{model.name | trim }}</span>
      <span v-if="!isFolder">
        ({{model.count}})
      </span>
      
    </div>
    
    <ul v-show="open" v-if="isFolder" class="tree">
      <item class="child" 
        v-for="(model,key) in model.children"
        :model="model" :key='key.id'>
      </item>
    </ul>
    <span v-else class="file">
      <div v-if="model.state === 0">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 21.98 30.49" width="20px" height="20px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M15.82,0H2A2,2,0,0,0,0,2v26.4a2,2,0,0,0,2,2H19.93a2,2,0,0,0,2-2V6.16Z" style="fill:#ffc107"/><path d="M15.8,0h-.51V4.62a2.55,2.55,0,0,0,2.55,2.55H22v-1Z" style="fill:#ffb300"/><path d="M7.31,21.87H5.68a1.26,1.26,0,0,1-1.26-1.26V19a1.26,1.26,0,0,1,1.26-1.26c2.09.11,2.91,1.19,2.88,2.88A1.26,1.26,0,0,1,7.31,21.87Z" style="fill:#fff"/><path d="M11.52,21.95a1.25,1.25,0,0,1-1.24-1.13c-.31-3.08-1.91-4.68-5.06-5a1.25,1.25,0,1,1,.28-2.48c4.33.5,6.84,3,7.26,7.28a1.25,1.25,0,0,1-1.12,1.37Z" style="fill:#fff"/><path d="M16.72,22.06a1.36,1.36,0,0,1-1.35-1.23c-.61-6.18-4-9.53-10.27-10.25a1.36,1.36,0,1,1,.31-2.71c7.55.87,11.93,5.25,12.67,12.69a1.36,1.36,0,0,1-1.22,1.49Z" style="fill:#fff"/></g></g></svg>
      </div>
      <div v-else-if="model.state === 1">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 21.98 30.49" width="20px" height="20px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M15.82,0H2A2,2,0,0,0,0,2v26.4a2,2,0,0,0,2,2H19.93a2,2,0,0,0,2-2V6.16Z" style="fill:#4caf50"/><path d="M15.8,0h-.51V4.62a2.55,2.55,0,0,0,2.55,2.55H22v-1Z" style="fill:#388e3c"/><path d="M7.31,21.87H5.68a1.26,1.26,0,0,1-1.26-1.26V19a1.26,1.26,0,0,1,1.26-1.26c2.09.11,2.91,1.19,2.88,2.88A1.26,1.26,0,0,1,7.31,21.87Z" style="fill:#fff"/><path d="M11.52,21.95a1.25,1.25,0,0,1-1.24-1.13c-.31-3.08-1.91-4.68-5.06-5a1.25,1.25,0,1,1,.28-2.48c4.33.5,6.84,3,7.26,7.28a1.25,1.25,0,0,1-1.12,1.37Z" style="fill:#fff"/><path d="M16.72,22.06a1.36,1.36,0,0,1-1.35-1.23c-.61-6.18-4-9.53-10.27-10.25a1.36,1.36,0,1,1,.31-2.71c7.55.87,11.93,5.25,12.67,12.69a1.36,1.36,0,0,1-1.22,1.49Z" style="fill:#fff"/></g></g></svg> 
      </div>
      <div v-else-if="model.state === 2">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 21.98 30.49" width="20px" height="20px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M15.82,0H2A2,2,0,0,0,0,2v26.4a2,2,0,0,0,2,2H19.93a2,2,0,0,0,2-2V6.16Z" style="fill:#f44336"/><path d="M15.8,0h-.51V4.62a2.55,2.55,0,0,0,2.55,2.55H22v-1Z" style="fill:#d32f2f"/><path d="M7.31,21.87H5.68a1.26,1.26,0,0,1-1.26-1.26V19a1.26,1.26,0,0,1,1.26-1.26c2.09.11,2.91,1.19,2.88,2.88A1.26,1.26,0,0,1,7.31,21.87Z" style="fill:#fff"/><path d="M11.52,21.95a1.25,1.25,0,0,1-1.24-1.13c-.31-3.08-1.91-4.68-5.06-5a1.25,1.25,0,1,1,.28-2.48c4.33.5,6.84,3,7.26,7.28a1.25,1.25,0,0,1-1.12,1.37Z" style="fill:#fff"/><path d="M16.72,22.06a1.36,1.36,0,0,1-1.35-1.23c-.61-6.18-4-9.53-10.27-10.25a1.36,1.36,0,1,1,.31-2.71c7.55.87,11.93,5.25,12.67,12.69a1.36,1.36,0,0,1-1.22,1.49Z" style="fill:#fff"/></g></g></svg> 
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
