<script>
  import { Router, Link, Route, navigate } from "svelte-routing";
  import back from "../../assets/arrow-left-svgrepo-com.svg";
  import FaArrowLeft from "svelte-icons/fa/FaArrowLeft.svelte";
  import myPic from '../../assets/34F1DF87-6D18-4B38-86E1-BCAF87A4B1B5.jpg'
  export let theme;

  function goBack() {
    navigate("/", { replace: true });
  }
</script>

<div class="About">
    <div class={"aboutCard "+ (theme? 'dark': 'light')}>
        <div class={"cardHeader "+ (theme? 'dark': 'light')}>
            <button on:click={goBack} class={(theme? 'dark': 'light')}>
                <div class={"icon "+(theme? 'dark': 'light')}>
                  <FaArrowLeft />
                </div>
              </button>
              <h1>Hola! Mi nombre es Sebastián Silva</h1>
        </div>
        <br>
        <div class="cardContent">
            <div class="text">
                Soy un estudiante (aún) de Ciencias de la Computación en la Universidad del Valle de Guatemala. Prácticamente escogí esta carrera porque desde muy pequeño siempre he estado envuelto de computadoras y es un campo que de verdad me apasiona. Además, me caracterizo por ser una persona muy curiosa que no se interesa únicamente por la computación, sino por otros rubros también, por ejemplo la física, la mecánica, las matemáticas, etc.
                <br>
                <br>
                Actualmente me encuentro aprendiendo todo lo que me es posible.
            </div>
            <img src={myPic} alt="miFoto :P" class={(theme? 'dark': 'light')}>
        </div>
    </div>
</div>

<style lang="scss">
  $light-color: #ccc;
  $dark-color: #2b2b2b;

  .cardContent{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .text{
    overflow-wrap: break-word;
    width: auto;
  }

  .aboutCard{
    padding: 20px;
    border-radius: 10px;
    margin-inline: 15px;
    margin-left: 15px;
    width: 75%;

    .cardHeader{
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    img{
        width: 40%;
        border-radius: 20px;
        margin: 20px;
    }
    img.light{
        border: 2px solid $dark-color;
    }
    img.dark{
        border: 2px solid $light-color;
    }
  }

  .aboutCard.light{
    border: 1px solid $dark-color;
  }

  .aboutCard.dark{
    border: 1px solid $light-color;
  }

  .cardHeader.dark{
    border-bottom: 1px solid $light-color;
  }

  .cardHeader.light{
    border-bottom: 1px solid $dark-color;
  }

  .icon{
    max-width: 40px;
  }

  .icon.dark{
    background-color: $dark-color;
    color: $light-color;
  }

  .icon.light{
    background-color: $light-color;
    color: $dark-color;
  }

  .About {
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

    h1{
        padding-inline: 3.5vw;
    }

    button {
        padding: 0;
        border: 0;
        max-height: 50px;     
    }

    button.light{
        background-color: $light-color;
    }

    button.dark{
        background-color: $dark-color;
    }
  }

   @media (min-width: 745px){
    .aboutCard{
        max-width: 715px;
        img{
            width: 30%;
        }
    }
  }
</style>
