<template>
    <div id="pagewrap">
      <header>
        <slot name="header"></slot>
      </header>
      <aside id="sidebar">
        <slot name="sidebar"></slot>
      </aside>
      <section id="content">
        <slot name="content"></slot>
      </section>
      <footer>
        <slot name="footer"></slot>
      </footer>
    </div>
</template>

<style scoped>
  #pagewrap {
    padding: 5px;
    width: 960px;
    margin: 20px auto;
  }
  header{
    height: 100px;
    padding: 0 15px;
  }
  #content{
    width: 696px;
    float: left;
    padding: 5px 15px;
    min-height: 300px;
  }
  #sidebar {
    width: 200px;
    padding: 5px 15px;
    float: left;
  }
  footer{
    clear: both;
    padding: 0 15px;
  }

</style>
