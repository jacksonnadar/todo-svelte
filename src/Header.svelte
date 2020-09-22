<script>
</script>

<style type="text/scss">
  header {
    padding: 0 5vw;
    height: 60px;
    width: 100%;
    background-color: #fcf2f2;
    color: #232323;
    nav {
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      .logo {
        font-weight: bold;
        font-size: 18px;
        display: flex;
        align-items: center;
      }
      .auth {
        padding: 5px 15px;
        box-shadow: none;
        border: none;
        background: #232323;
        border-radius: 17px;
        color: #fcf2f2;
        font-size: 18px;
      }
    }
  }
</style>

<header>
  <nav>
    <div class="logo">Todo List</div>
    <button class="auth">Sign in</button>
  </nav>
</header>
