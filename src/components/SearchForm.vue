<template>
    <form @submit.prevent="onSubmit">
        <input
            type="text"
            placeholder="Buscar imagen"
            v-model="imgname"
            name="img-name"
            v-validate="'required|min:5'"
        >
				<span>{{errors.first('img-name')}}</span>
        <button type="submit">Buscar</button>
    </form>
</template>

<script>
export default {
    name: 'SearchForm',
    methods:{
        onSubmit (){
            this.$validator.validate().then((valid) => {
                if (valid){
                    this.$emit('searchGiphy',{
                        name: this.name,
                    })
                } else {
                    console.log("algo fallo");
                }
            })
        }
    },
    data () {
        return {
            imgname: ''
        }
    }
    
}
</script>

<style>

</style>
