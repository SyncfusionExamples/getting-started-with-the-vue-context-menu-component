<script setup>
  import { ContextMenuComponent } from '@syncfusion/ej2-vue-navigations';
  const menuItems = [
    { 
      text: 'Cut',
      iconCss: 'e-icons e-cut'
    },
    { 
      text: 'Copy',
      iconCss: 'e-icons e-copy'
    },
    { 
      text: 'Paste',
      iconCss: 'e-icons e-paste',
      items: [
        {text:'Paste as Plain Text'}, 
        {text:'Merge Formatting',
          items:[
            {text:'Match destination formatting'},
            {text:'Match Source formatting'},
          ]
        }
      ]
    },
    {
      text: 'Navigate', 
      url: 'https://ej2.syncfusion.com/vue/documentation/context-menu/accessibility'
    }
  ]
  const animation ={
    effect: 'FadeIn',
    duration: 800
  }
  const itemRender = (args)=>{
    args.element.classList.add('custom');
  }
  const beforeOpen = (args)=>{
    const contextMenu = args.element.ej2_instances[0];
    contextMenu.enableItems(['Paste'], false);
  }
</script>

<template>
  <div id="target" class="container">
    Right-click / Touch hold to open the context menu
    <ContextMenuComponent target="#target"
      :items="menuItems"
      :showItemOnClick="true"
      :animationSettings="animation"
      @beforeItemRender="itemRender"
      @beforeOpen="beforeOpen"
    ></ContextMenuComponent>
  </div>
</template>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-navigations/styles/material.css";

.container{
  padding: 10%;
  text-align: center;
  border: 1px solid black;
  margin-top: 8%;
  margin-left:25%;
  width: 500px;
}
.e-cut::before {
  content: '\e264';
}
.e-copy::before {
  content: '\e959';
}
.e-paste::before {
  content: '\e263';
}
.custom{
  float: left;
  font-size: 10px;
  font-style: italic;
}
</style>