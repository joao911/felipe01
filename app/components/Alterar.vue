<template>
    <Page actionBarHidden="true">
        <StackLayout>
           <Image class="logo" src="~/images/teste.png" width="200" height="200" stretch="aspectFill" loadModule="async"></Image>
            <StackLayout class="padrao">
                <Label textWrap="true" text="Esqueci a senha" class="h1"></Label>   
                <StackLayout>
                      <TextField v-model="Nsenha" hint="Nova Senha" />
                      <TextField v-model="Csenha" hint="Confirmar" />
                </StackLayout>
                <Button class="btn enviar"  text="Enviar email" @tap="router" 
                 :class="isSenhaValida() ? 'btn--habilitado' : 'btn--desabilitado'"/>  
            </StackLayout>
        </StackLayout> 

        
    </Page>
</template>

<script>
    import Alterar from "./Alterar";

    export default {
        data() {
            return {
             Nsenha:"",  
             CSenha:"" 
            }
        },
        methods: {
            router() {
                this.$backendService.logout();
                this.$navigateTo(Alterar, {
                    clearHistory: true
                });
            },
            isSenhaValida() {
                return (this.Nsenha >3 && this.CSenha >3) && (this.Nsenha === this.CSenha);
            },
        }
    }
</script>

<style>
.padrao{
    width: 90%;
    height: 400;
}
Label{
    text-align: center;
}
.enviar{  
    color: #FFFFFF;
}
.btn--desaabilitado{
background-color: #616161;
}
.btn--habilitado{
    background-color: #BD0048;
}
</style>
