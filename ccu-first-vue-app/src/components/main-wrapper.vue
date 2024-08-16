<script>
 export default {
    name: 'main-wrapper',

 }
</script>
<template>
    <div>
    <header class="header">
        <slot name="header"></slot>
    </header>
    <main class="main">
        <slot name="main"></slot>
    </main>
    <footer class="footer">
        <slot name="footer"></slot>
    </footer>
    </div>
</template>

<style>
.header {
    border-color: black;
    border-bottom-style: solid;
    padding-top: 50px;
    padding-right: 30px;
    padding-left: 80px;
}
.footer {
    border-color: black;
    border-top-style: solid;
    padding-right: 30px;
    padding-bottom: 50px;
    padding-left: 80px;
}
.main {
  padding-top: 50px;
  padding-right: 30px;
  padding-bottom: 50px;
  padding-left: 80px;
}
</style>