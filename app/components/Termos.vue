<template>
    <Page actionBarHidden="true">
        <StackLayout>
           <Image class="logo" src="~/images/teste.png" width="200" height="200" stretch="aspectFill" loadModule="async"></Image>
            <StackLayout>

                <ScrollView orientation="vertical" class="termos">
                    <StackLayout>
                        <Label  class="h2"
                            text="Termos e condições" />
                       <Label textWrap="true" text="Lorem ipsum, dolor sit amet consectetur adipisicing elit. Iusto omnis consequatur quod nesciunt eos in eligendi aliquam sunt veniam vitae, corporis nobis reiciendis placeat repellendus voluptatibus totam quia doloremque voluptatem dignissimos cum quasi alias velit tempora recusandae? Placeat iusto fugiat quidem error, praesentium nam mollitia ea repellendus accusantium iste libero?." class="h3 description-label Lorem ipsum, dolor sit amet consectetur adipisicing elit. Iusto omnis consequatur quod nesciunt eos in eligendi aliquam sunt veniam vitae, corporis nobis reiciendis placeat repellendus voluptatibus totam quia doloremque voluptatem dignissimos cum quasi alias velit tempora recusandae? Placeat iusto fugiat quidem error, praesentium nam mollitia ea repellendus accusantium iste libero?."  />
                    
                    </StackLayout>
                    
                </ScrollView>
                <Button text="aceitar e continuar" class="continuar"  @tap="aceito"  />
                <Button text="não aceitar" class="n-aceitar" @tap="router" />
            </StackLayout>
        </StackLayout>
    </Page>
</template>
<script>
    import Login from "./Login";
    import Senha from "./Senha";
    import Email from "./Email";
    export default {
        data() {
            return {
                message: "Daqui vai para primeiro login."
            }
        },
        methods: {
            router() {
                this.$backendService.logout();
                this.$navigateTo(Login, {
                    clearHistory: true
                });
            },
            aceito() {
                this.$backendService.logout();
                this.$navigateTo(Email, {
                    clearHistory: true
                });
            },
        }
    }
</script>

<style scoped>
    Image {
        width: 100;
    }

    .termos{
        margin-top: 20;
        height: 200;
        width: 80%;
    }
    .h2{
        text-align: center;
        text-decoration: underline;
    }
    .continuar{
        text-transform: none;
        margin-top: 20;
        background-color: #BD0048;
        color: #FFFFFF;
         border-radius: 25;
        width: 80%;
    }
    .n-aceitar{
        text-transform: none;
        margin-top: 10;
        background-color:#616161;
        color: #FFFFFF;
         border-radius: 25;
        width: 80%;
    }
        
    
</style>