<template>
   <Page actionBarHidden="true">
        <StackLayout>
           <Image class="logo" src="~/images/teste.png" width="200" height="200" stretch="aspectFill" loadModule="async"></Image>
            <StackLayout class="padrao">

                 <TextField v-model="senha" hint="email@gmail.com" />
                 <TextField v-model="senha1" hint="senha" />
                <Button text="entrar" @tap="router" />  
                <Label text="esqueci minha senha"  @tap="aceito"/>   
            </StackLayout>
        </StackLayout>
    </Page>
</template>
<script>
    import Home from "./Home";
    import Senha from "./Senha";
    export default {
        data() {
            return {
                message: "Daqui vai para primeiro login."
            }
        },
        methods: {
            router() {
                this.$backendService.logout();
                this.$navigateTo(Home, {
                    clearHistory: true
                });
            },
            aceito() {
                this.$backendService.logout();
                this.$navigateTo(Senha, {
                    clearHistory: true
                });
            },
        }
    }
</script>  
<style scoped>
.padrao{
    margin-top: 30;
    width: 90%;
}
Button{
    margin-top: 10;
    border-radius: 25;
    background-color: #BD0048;
    color:#FFFFFF;
    text-transform: none;
    width: 80%;
}
Label{
    text-align: center;
}
</style>