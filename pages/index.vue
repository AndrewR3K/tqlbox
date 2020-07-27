<template>
 <div class="home">
   <div class="home-wrap">
    <h1>What is TQLBox?</h1>
    <div>
      TQLbox (pronounced tacklebox) is a handy box of all the equipment a Developer, Designer, or average person, might want on the web.
      You wouldn't go fishing without your TQLbox would you? Same goes for the web!
      <br/>
      <br/>
      <h3>More coming soon!</h3>
    </div>
  </div>
 </div>
</template>

<script>
export default {
  head () {
    return {
      title: 'home',
      meta: [{
        hid: 'description',
        name: 'description',
        content: 'My custom description'
      }]
    }
  }
}
</script>
<style>
  .home {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding-top: 10%;
  }
  .home-wrap {
    width: 80%;
    min-width: 200px;
    max-width: 700px;
  }

  .home-wrap h1 {
    padding-bottom: 10px;
  }
</style>
