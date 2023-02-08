
<template>
   <nav class="container-fluid d-flex justify-content-between p-3 shadow-sm align-items-center fixed-top px-5 bg-white">
        <div class="portal-manager-restaurant">
            Portal Manager de Restaurantes
        </div>
        <div>
            <ul class="navbar-nav flex-row d-flex align-items-center gap-4">
                <li class="nav-item">
                    <div class="d-flex alignt-items-center justify-content-center shadow-sm">
                        <i class="fa-solid fa-headset"></i>
                    </div>
                </li>
                <li class="nav-item">
                    <a class="nav-link active text-bg-primary border-5 bg-opacity-10 rounded-5 text-black px-3"
                        aria-current="page" href="#">Restaurantes</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">Comercios</a>
                </li>
                <li class="nav-item">
                    <div class="user"></div>
                </li>
            </ul>
        </div>
    </nav>
</template>


<script>
export default {
  name: 'Cabecera',
  props: {

  }
}
</script>

<style scoped>

*{
    font-size: 14px;
}

.navbar{
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid black ;
}

ul{
    display: flex;
    justify-content: center;
    align-items: center;
    list-style-type: none;
    gap: 30px;
}

a:link, a:visited, a:active {
    text-decoration:none;
}
.noti{
    width: 25px;
    height: 25px;
    border: 2px solid #c5fbff;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 10px 0 20px rgba(0, 0, 0, 0.19), 6px 0 6px rgba(0, 0, 0, 0.23);
}

.boton{
    width: 150px;
    height: 25px;
    border: 2px solid #c5fbff;
    border-radius: 20%;
    color: #000 !important;
    background-color: #c5fbff;
    display: flex;
    justify-content: center;
    align-items: center;
}

</style>