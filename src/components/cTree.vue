<template>
  <li>
    <div :class="{bold: isFolder}" @click="toggle" >
      <span v-if="isFolder">[{{open ? '-' : '+'}}]</span>
      <div v-if="isFolder" class="folder">
        <div v-if="open">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 51.65 36.35" width="20px" height="20px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M43.74,4.4H23.34L18.95,0H7.68A4.68,4.68,0,0,0,3,4.68V31.43a4.92,4.92,0,0,0,4.92,4.92H43.74a4.92,4.92,0,0,0,4.92-4.92V9.31A4.92,4.92,0,0,0,43.74,4.4Z" style="fill:#ff9800"/><path d="M43.74,36.35H7.92A4.83,4.83,0,0,1,3,31.62L0,14.17A4.83,4.83,0,0,1,4.92,9.44H46.74a4.83,4.83,0,0,1,4.92,4.73l-3,17.44A4.83,4.83,0,0,1,43.74,36.35Z" style="fill:#ffb74d"/><path d="M21.82,31.29H20.14a1.56,1.56,0,0,1-1.53-.82l-.31-1.14c-.14-.52.4-1,1.2-1,2.44.09,3.46.91,3.54,2.1C23.09,30.93,22.54,31.29,21.82,31.29Z" style="fill:#fff"/><path d="M26.18,31.34c-.65,0-1.22-.3-1.29-.72-.39-2.23-2.39-3.56-6.29-3.87a1.81,1.81,0,0,1-1.72-1.28c-.09-.68.6-1.19,1.53-1.11,5.79.51,8.92,2.86,9.14,6.1,0,.45-.52.84-1.24.88Z" style="fill:#fff"/><path d="M31.53,31.41c-.71,0-1.25-.33-1.23-.79.22-4.91-4-8.5-13.18-9.39a2.67,2.67,0,0,1-2.35-2c-.18-1.1.68-1.92,1.94-1.79,12.22,1.31,17.55,6.76,16.53,13-.08.49-.78.92-1.57,1Z" style="fill:#fff"/></g></g></svg>
        </div>
        <div v-else>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 45.65 36.35" width="20px" height="20px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M25.38,9.44,15.95,0H4.68A4.68,4.68,0,0,0,0,4.68V9.44Z" style="fill:#ff9800"/><rect y="4.4" width="45.65" height="31.95" rx="4.92" ry="4.92" style="fill:#ffb74d"/><path d="M18,29.42H15.88a1.65,1.65,0,0,1-1.65-1.65V25.64A1.65,1.65,0,0,1,15.88,24c2.74.15,3.81,1.56,3.78,3.78A1.65,1.65,0,0,1,18,29.42Z" style="fill:#fff"/><path d="M23.53,29.51A1.63,1.63,0,0,1,21.9,28c-.4-4-2.51-6.13-6.63-6.6a1.63,1.63,0,0,1,.37-3.25c5.66.65,9,3.94,9.51,9.53a1.63,1.63,0,0,1-1.47,1.79Z" style="fill:#fff"/><path d="M30.33,29.66a1.78,1.78,0,0,1-1.77-1.61c-.8-8.08-5.2-12.47-13.44-13.42a1.78,1.78,0,1,1,.41-3.54C25.41,12.23,31.14,18,32.11,27.7a1.78,1.78,0,0,1-1.6,2Z" style="fill:#fff"/></g></g></svg>
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
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 21.98 30.49" width="20px" height="20px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M15.82,0H2A2,2,0,0,0,0,2v26.4a2,2,0,0,0,2,2H19.93a2,2,0,0,0,2-2V6.16Z" style="fill:#e0e0e0"/><path d="M15.8,0h-.51V4.62a2.55,2.55,0,0,0,2.55,2.55H22v-1Z" style="fill:#bdbdbd"/><path d="M7.73,21.08H6.3A1.12,1.12,0,0,1,5.18,20V18.52A1.12,1.12,0,0,1,6.3,17.41c1.85.1,2.57,1.06,2.55,2.55A1.12,1.12,0,0,1,7.73,21.08Z" style="fill:#bdbdbd"/><path d="M11.46,21.14a1.1,1.1,0,0,1-1.1-1c-.27-2.73-1.69-4.14-4.48-4.46a1.1,1.1,0,1,1,.25-2.2c3.83.44,6.05,2.67,6.42,6.44a1.1,1.1,0,0,1-1,1.21Z" style="fill:#bdbdbd"/><path d="M16.06,21.24a1.21,1.21,0,0,1-1.2-1.09c-.54-5.46-3.51-8.43-9.08-9.07a1.21,1.21,0,0,1,.27-2.39c6.68.77,10.56,4.65,11.21,11.23a1.21,1.21,0,0,1-1.08,1.32Z" style="fill:#bdbdbd"/><path d="M0,25.5v2.93a2.06,2.06,0,0,0,2.06,2.06H19.92A2.06,2.06,0,0,0,22,28.43V25.5Z" style="fill:#ffc107"/></g></g></svg>
      </div>
      <div v-else-if="model.state === 1">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 21.98 30.49" width="20px" height="20px"><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M15.82,0H2A2,2,0,0,0,0,2v26.4a2,2,0,0,0,2,2H19.93a2,2,0,0,0,2-2V6.16Z" style="fill:#e0e0e0"/><path d="M15.8,0h-.51V4.62a2.55,2.55,0,0,0,2.55,2.55H22v-1Z" style="fill:#bdbdbd"/><path d="M7.73,21.08H6.3A1.12,1.12,0,0,1,5.18,20V18.52A1.12,1.12,0,0,1,6.3,17.41c1.85.1,2.57,1.06,2.55,2.55A1.12,1.12,0,0,1,7.73,21.08Z" style="fill:#bdbdbd"/><path d="M11.46,21.14a1.1,1.1,0,0,1-1.1-1c-.27-2.73-1.69-4.14-4.48-4.46a1.1,1.1,0,1,1,.25-2.2c3.83.44,6.05,2.67,6.42,6.44a1.1,1.1,0,0,1-1,1.21Z" style="fill:#bdbdbd"/><path d="M16.06,21.24a1.21,1.21,0,0,1-1.2-1.09c-.54-5.46-3.51-8.43-9.08-9.07a1.21,1.21,0,0,1,.27-2.39c6.68.77,10.56,4.65,11.21,11.23a1.21,1.21,0,0,1-1.08,1.32Z" style="fill:#bdbdbd"/><path d="M0,25.5v2.93a2.06,2.06,0,0,0,2.06,2.06H19.92A2.06,2.06,0,0,0,22,28.43V25.5Z" style="fill:#4caf50"/></g></g></svg>
      </div>
      <div v-else-if="model.state === 2">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 21.98 30.49" width="20px" height="20px" ><g id="Layer_2" data-name="Layer 2"><g id="Layer_1-2" data-name="Layer 1"><path d="M15.82,0H2A2,2,0,0,0,0,2v26.4a2,2,0,0,0,2,2H19.93a2,2,0,0,0,2-2V6.16Z" style="fill:#e0e0e0"/><path d="M15.8,0h-.51V4.62a2.55,2.55,0,0,0,2.55,2.55H22v-1Z" style="fill:#bdbdbd"/><path d="M7.73,21.08H6.3A1.12,1.12,0,0,1,5.18,20V18.52A1.12,1.12,0,0,1,6.3,17.41c1.85.1,2.57,1.06,2.55,2.55A1.12,1.12,0,0,1,7.73,21.08Z" style="fill:#bdbdbd"/><path d="M11.46,21.14a1.1,1.1,0,0,1-1.1-1c-.27-2.73-1.69-4.14-4.48-4.46a1.1,1.1,0,1,1,.25-2.2c3.83.44,6.05,2.67,6.42,6.44a1.1,1.1,0,0,1-1,1.21Z" style="fill:#bdbdbd"/><path d="M16.06,21.24a1.21,1.21,0,0,1-1.2-1.09c-.54-5.46-3.51-8.43-9.08-9.07a1.21,1.21,0,0,1,.27-2.39c6.68.77,10.56,4.65,11.21,11.23a1.21,1.21,0,0,1-1.08,1.32Z" style="fill:#bdbdbd"/><path d="M0,25.5v2.93a2.06,2.06,0,0,0,2.06,2.06H19.92A2.06,2.06,0,0,0,22,28.43V25.5Z" style="fill:#f44336"/></g></g></svg>
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
