<template>
  <div class="background">
    <div class="content">
      <h1>Top joueur monde tennis de table !</h1>
      <nuxt-link to="/players" class="discover-link">Découvrir !</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NuxtTutorial'
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.background {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-image: url("../public/assets/table-tennis-wallpapers.jpg");
  background-size: cover;
}

.content {
  text-align: center;
  color: white;
  font-family: Arial, Helvetica, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 20px;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 255, 255, 0.5);
}


.discover-link {
  text-decoration: none;
  border: 0 solid;
  box-shadow: inset 0 0 20px rgba(255, 255, 255, 0);
  outline: 1px solid;
  outline-color: rgba(255, 255, 255, .5);
  outline-offset: 0px;
  text-shadow: none;
  transition: all 1250ms cubic-bezier(0.19, 1, 0.22, 1);
  padding: 8px;
  color: white;
  border-radius: 10px;
  font-family: nature system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif
} 

.discover-link:hover {
  border: 1px solid;
  box-shadow: inset 0 0 20px rgba(255, 255, 255, .5), 0 0 20px rgba(255, 255, 255, .2);
  outline-color: rgba(255, 255, 255, 0);
  outline-offset: 15px;
  text-shadow: 1px 1px 2px #427388; 
}

</style>
