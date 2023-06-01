<script>
  import { Router, Link, Route, navigate } from "svelte-routing";
  import FaArrowLeft from "svelte-icons/fa/FaArrowLeft.svelte";
  import MedKitImg from '../../assets/MedKit.png';
  import CalcImg from '../../assets/Calculator.png';
  import CookImg from '../../assets/CookApp.png';
  import pokeImg from '../../assets/Poke.png'
  import soundImg from '../../assets/SoundCloud.png';
  export let theme;
 let medKitLink = "http://50.16.178.129/";
 let calcLink = "https://bat-calculator.web.app/";
 let cookLink = "https://github.com/hsilv/Proyecto-Software";
 let pokeLink = "https://lab8-5a432.web.app/";
 let soundLink = "https://soundcloud-artists-1.web.app/";
    

  let projOpt = "MedKit";
  let projImg = MedKitImg;
  let projDesc = "MedKit fue una aplicación realizada en Angular para el Frontend y PostgreSQL y ExpressJS en el Backend. Su objetivo es brindar a los centros médicos e instituciones información instantánea acerca de los pacientes y los estados de centros médicos, inventario, doctores, etc.";
  let projLink = medKitLink;

  function goBack() {
    navigate("/", { replace: true });
  }

  function setOpt(event){
    let opt = event.target.id;
    if(opt === 'MedKit'){
        projOpt = "MedKit";
        projImg = MedKitImg;
        projDesc = "MedKit fue una aplicación realizada en Angular para el Frontend y PostgreSQL y ExpressJS en el Backend. Su objetivo es brindar a los centros médicos e instituciones información instantánea acerca de los pacientes y los estados de centros médicos, inventario, doctores, etc.";
        projLink = medKitLink;
    } else if (opt === 'Calculator'){
        projOpt = "Calculator";
        projImg = CalcImg;
        projDesc = "Bat Calculator es una calculadora hecha en React únicamente junto con tecnologías de manejo de paquetes y compilación como Babel y Webpack, además de utilizar un Linter como ESLint, está programada con los complaints de AirBnb para un código más limpio, en cuanto a funcionalidad, se buscó hacerla lo más parecido a las calculadoras que los sistemas operativos ya traen";
        projLink = calcLink;
    } else if (opt === 'CookApp'){
        projOpt = 'CookApp';
        projImg = CookImg;
        projDesc = "CookApp es una aplicación que aún se encuentra en desarrollo, está se está programando con React para el Frontend, y PostgreSQL y Flask para el Backend. Esta aplicación está destinada a hacer el seguimiento de una receta de forma más sencilla, está orientada hacia personas que quieren aprender a cocinar. También para chef's y profesionales de la cocina que quieren recibir feedback de sus recetas por medio de calificaciones y comentarios";
        projLink = cookLink;
    }else if (opt === 'PokeMemory'){
        projOpt = 'PokeMemory';
        projImg = pokeImg;
        projDesc = "PokeMemory es un juego de memoria hecho únicamente en React utilizando CSS Grid y transiciones de CSS comunes para lograr un juego de memoria. Las cartas se reparten de manera aleatoria, también posee un contador de turnos y un mensaje de victoria en caso de dar vuelta a todas las cartas";
        projLink = pokeLink;
    }else if (opt === 'SoundCloud'){
        projOpt = 'SoundCloud';
        projImg = soundImg;
        projDesc = "Este proyecto es una réplica exacta de la página SoundCloud for Artists oficial de SoundCloud. En este caso se implementó Server Side Rendering, además de manejar secciones responsivas y animaciones con CSS";
        projLink = soundLink;
    }
    console.log(event.target.id);
  }
</script>

<div class="Projects">
  <div class={"projCard " + (theme ? "dark" : "light")}>
    <div class={"cardHeader " + (theme ? "dark" : "light")}>
      <button on:click={goBack} class={theme ? "dark" : "light"}>
        <div class={"icon " + (theme ? "dark" : "light")}>
          <FaArrowLeft />
        </div>
      </button>
      <h1>Proyectos más relevantes</h1>
    </div>

    <div class="cardBody">
      <div class="projOpt">
        <h1>{projOpt}</h1>
        <img src={projImg} alt="Imagen de Proyecto" />
        <span>{projDesc}</span>
        <a href={projLink} class={"img "+(theme ? "dark" : "light")}>Link de {projOpt}</a>
      </div>

      <div class={"projList " + (theme ? "dark" : "light")}>
        <div class={"opt " + (theme ? "dark" : "light")} id="MedKit" on:mouseenter={setOpt}>
          <h2 id="MedKit" on:mouseenter={setOpt}>MedKit</h2>
        </div>
        <div class={"opt " + (theme ? "dark" : "light")} on:mouseenter={setOpt} id="Calculator">
          <h2 on:mouseenter={setOpt} id="Calculator">Calculator</h2>
        </div>
        <div class={"opt " + (theme ? "dark" : "light")} on:mouseenter={setOpt} id="CookApp">
          <h2 on:mouseenter={setOpt} id="CookApp">CookApp</h2>
        </div>
        <div class={"opt " + (theme ? "dark" : "light")} on:mouseenter={setOpt} id="PokeMemory">
          <h2 on:mouseenter={setOpt} id="PokeMemory">PokéMemory</h2>
        </div>
        <div class={"opt " + (theme ? "dark" : "light")} on:mouseenter={setOpt} id="SoundCloud">
          <h2 on:mouseenter={setOpt} id="SoundCloud">SoundCloud</h2>
        </div>
      </div>
    </div>
  </div>
</div>

<style lang="scss">
  $light-color: #ccc;
  $dark-color: #2b2b2b;
  $dark-hover: #404040;
  $light-hover: #bbbbbb;

  h1 {
    font-size: larger;
  }

  h2 {
    font-size: larger;
  }

  .cardBody {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    margin-block: 10px;
    word-wrap: break-word;

    .projOpt {
      width: 60%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      word-wrap: break-word;

      img {
        max-width: 35vw;
        width: 35vw;
        margin-block: 1vh;
        border-radius: 10px;
      }

      span{
        word-wrap: break-word;
        max-width: 94%;
        margin-right: 3.5%;
        margin-left: 2.5%;
      }

      .img{
        text-decoration: none;
        margin-top: 15px;
        border-radius: 10px;
      }

      .img.dark{
        padding: 10px;
        background-color: $light-color;
        color: $dark-color;
        &:visited{
            color: $dark-color;
        }
      }

      .img.light{
        padding: 10px;
        background-color: $dark-color;
        color: $light-color;
        &:visited{
            color: $light-color;
        }
      }
    }

    .projList {
      width: 40%;
      height: 100%;
      display: grid;
      grid-template-columns: 100%;
      grid-template-rows: repeat(1, 1fr);
      margin-top: 2vh;

      .opt {
        display: flex;
        top: 50%;
        left: 50%;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        h2 {
          padding: 0;
        }
      }

      .opt.dark {
        &:hover {
          background-color: $dark-hover;
        }
      }

      .opt.light {
        &:hover {
          background-color: $light-hover;
        }
      }
    }

    .projList.dark {
      border-left: 1px solid $light-color;
    }

    .projList.light {
      border-left: 1px solid $dark-color;
    }
  }

  .projCard {
    padding: 20px;
    border-radius: 10px;
    margin-inline: 15px;
    margin-left: 15px;
    width: 75%;

    .cardHeader {
      display: flex;
      flex-direction: row;
      align-items: center;
    }

    .cardHeader.dark {
      border-bottom: 1px solid $light-color;
    }

    .cardHeader.light {
      border-bottom: 1px solid $dark-color;
    }

    .icon {
      max-width: 40px;
    }

    .icon.dark {
      background-color: $dark-color;
      color: $light-color;
    }

    .icon.light {
      background-color: $light-color;
      color: $dark-color;
    }
  }

  .projCard.dark {
    border: 1px solid $light-color;
  }

  .projCard.light {
    border: 1px solid $dark-color;
  }

  .Projects {
    margin-top: 20px;
    margin-bottom: 20px;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    h1 {
      padding-inline: 3.5vw;
    }
    button {
      padding: 0;
      border: 0;
      max-height: 50px;
    }
  }

  @media (min-width: 745px) {
    h1 {
      font-size: xx-large;
    }

    h2 {
      font-size: x-large;
    }

    .projCard {
      max-width: 715px;

      .projOpt {
        width: 70%;
        img {
          max-width: 22vw;
          width: 22vw;
        }
      }

      .projList {
        width: 30%;
      }
    }
  }
</style>
