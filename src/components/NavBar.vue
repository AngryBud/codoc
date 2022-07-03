<template>
    <nav id="navBar">
        <div style="display:flex">
            <img id="logo" src='../assets/logo.jpg' alt='logo'>
            <div id="tab">
                <a style="border-bottom: 2px solid #233C73;color:#233C73;">Recherche</a>
                <a>Cohortes</a>
                <a>Export</a>
                <a>Admin</a>
            </div>
        </div>
        
        <div id='user'>
            <img id='userIcon' src='../assets/User1.svg' alt='user'>
        </div>
    </nav>
</template>


<script>
export default {
  name: 'NavBar',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#navBar{
  display: flex;
  height: 52px;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #E4E5E8;
}
#logo{
    object-fit: contain;
    width: 81px;
    margin-left: 20px;
    margin-right: 24px;
}
#tab{
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    width: 366px;
    height: 48px;
}
a{
    display: flex;
    align-items: center;
    font-size: 16px;
    line-height: 23px;
    letter-spacing: -0.3px;
    padding: 12px 16px;
    color:#696F78;
}
/* a:hover{
    border-bottom: 2px solid #233C73;
    color:#233C73;
} */
#user{
    height: 34px;
    width: 34px;
    background-color: #233C73;
    border-radius: 50%;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 20px;
}
#userIcon{
    position: absolute;
}
</style>