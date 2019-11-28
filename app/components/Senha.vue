<template>
    <Page actionBarHidden="true">
        <FlexboxLayout class="page">
            <StackLayout class="form" witdh="50%">
                <Image class="logo" src="~/images/teste.png" width="200" height="200" stretch="aspectFill" loadModule="async"></Image>
                <Label class="header" text="Bem vindo"></Label>
               <TextField v-model="user.email" class="email" hint="Nome de usuário" />
                <TextField v-model="user.password" hint="Nova senha****" />
                <TextField v-model="user.confirmPassword" hint="Confirmar senha****" />
                <FlexboxLayout class="condicoes">
                <Label text="aceitar termos e condições" @tap="router" textDecoration="Underline"></Label>
                 <Switch checked="true" />
                 </FlexboxLayout>
                <Button
                    @tap="logado" text="avançar" class="btn "></Button>
            </StackLayout>
        </FlexboxLayout>
    </Page>
</template>

<script>
    import LoginPadrao from "./LoginPadrao";
    import Termos from "./Termos";
    export default {
        data() {
            return {
                isLoggingIn: true,
                processing: false,
                user: {
                    email: "",
                    password: "",
                    confirmPassword: ""
                }
            };
        },
        methods: {
          router() {
                this.$backendService.logout();
                this.$navigateTo(Termos, {
                    clearHistory: true
                });
            } , 
            logado() {
                this.$backendService.logout();
                this.$navigateTo(LoginPadrao, {
                    clearHistory: true
                });
            }  
          

        }
    };
</script>

<style scoped>
    .page {
        align-items: center;
        flex-direction: column;
    }

    .form {
        margin-left: 30;
        margin-right: 30;
        flex-grow: 2;
        vertical-align: middle;
    }

    .logo {
        margin-bottom: 12;
        height: 90;
        font-weight: bold;
    }

    .header {
        horizontal-align: center;
        font-size: 25;
        font-weight: 600;
        margin-bottom: 70;
        text-align: center;
        color: #3A3A3A;
    }
    .condicoes{
        justify-content: center;
    }

    
    Button {
        border-radius: 25;
        background-color: #616161;
        color: #FFFFFF;
        margin-top: 20;
    }

    .btn-primary {
        margin: 30 5 15 5;
    }

    .login-label {
        horizontal-align: center;
        color: #A8A8A8;
        font-size: 16;
    }

    .sign-up-label {
        margin-bottom: 20;
    }

    .bold {
        color: #000000;
    }
    .email{
        margin-top: -40;
        width: 100%;
    }
</style>
