<template>
    <Page actionBarHidden="true">
        <StackLayout>
           <Image class="logo" src="~/images/teste.png" width="200" height="200" stretch="aspectFill" loadModule="async"></Image>
            <StackLayout class="padrao">
                <Label textWrap="true" text="Esqueci a senha" class="h1 esqueci"></Label>
                <Label textWrap="true" text="Digete o endereço de email que usou para criar sua conta e nós lhe enviaremos um link para redefinir sua senha "  />
                <FlexboxLayout class="flex"> 
                    <Image  src="~/images/email.png" width="40" height="30" stretch="aspectFill" loadModule="async"></Image>              
                    <TextField v-model="email" class="field" hint="joaosilva@email.com" />               
                 </FlexboxLayout>
                <Button text="Enviar email" @tap="router" />  
              
            </StackLayout>
        </StackLayout> 

        
    </Page>
</template>

<script>
    import Alterar from "./Alterar";

    export default {
        data() {
            return {
             email:""   
            }
        },
        methods: {
            router() {
                this.$backendService.logout();
                this.$navigateTo(Alterar, {
                    clearHistory: true
                });
            }
        }
    }
</script>

<style>
.padrao{
    width: 90%;
    height: 400;
}
.esqueci{
    margin-top: 20;
    font-size: 40;
}
Label{
    text-align: center;
}
.flex{
width: 90%;
justify-content:space-between;
}
.field{
    width: 90%;
}
Button{
    text-transform: none;
    border-radius: 25;
    margin-top: 25;
    background-color: #BD0048;
    width: 60%;
    color: #FFFFFF;
}
</style>
