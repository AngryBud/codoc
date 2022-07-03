<template>
            <div id='allCats'>
                <div id='date'>
                    <span>Date</span>
                    <img src='../assets/CaretDown.svg' alt='down'>
                </div>
                <div style="width:77px"></div>
                <div id='type'>
                    <span>Type</span>
                    <img src='../assets/CaretDown.svg' alt='down'>
                </div>
                <div id='origin'>
                    <span>Origin</span>
                    <img src='../assets/CaretDown.svg' alt='down'>
                </div>
                <div id='apercu'>
                    <span>Aperçu</span>
                    <img src='../assets/CaretDown.svg' alt='down'>
                </div>
                <div style="width:53px"></div>
            </div>
</template>

<script>
export default {
    name: 'all-categorie'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#allCats{
    display: flex;
    height: 40px;
    border-bottom: 1px solid #D6D7DF;
}
#date{
    width: 70px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-left: 10px;
}
#type{
    width: 220px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-left: 10px;
}
#origin{
    width: 150px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-left: 10px;
}
#apercu{
    width: 826px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-left: 10px;
}
</style>