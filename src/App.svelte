<script lang="ts">
  import LightLogo from "./assets/S_Logo_Light.png";
  import DarkLogo from "./assets/S_Logo_Dark.png";
  import Header from "./components/Header/Header.svelte";
  import Menu from "./components/Menu/Menu.svelte";
  import { Router, Link, Route } from "svelte-routing";
  import About from "./components/About/About.svelte";
  import Skills from "./components/Skills/Skills.svelte";
  import Projects from "./components/Projects/Projects.svelte";

  let theme;
  let clicks = 0;
  let classButton = "rojo";

  function handleClick() {
    clicks += 1;
  }
</script>

<main>
  <Header bind:dark={theme} />
  <div class={"content " + (theme ? "dark" : "light")}>
    <Router>

      <Route path="/">
        <Menu {theme} />
      </Route>

      <Route path="/about">
        <About theme={theme}/>
      </Route>

      <Route path="/skills">
        <Skills theme={theme}/>
      </Route>

      <Route path="/projects">
        <Projects theme={theme}/>
      </Route>

      <Route path="/contact">
        Contacto
      </Route>

    </Router>
  </div>
</main>

<style lang="scss">
  $light-color: #ccc;
  $dark-color: #2b2b2b;

  main {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
  }

  .content {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    transition: 0.4s ease;
  }

  .content.dark {
    background-color: $dark-color;
    color: $light-color;
  }

  .content.light {
    background-color: $light-color;
    color: $dark-color;
  }
</style>
