<template>
    <div class="App">
        <p class="App-intro">
            <paystack
                :amount="amount"
                :email="email"
                :paystackkey="paystackkey"
                :reference="reference"
                :callback="callback"
                :close="close"
                :embed="false"
            >
                <i>Pay me, My Money</i>
            </paystack>
        </p>
    </div>
</template>

<script type="text/javascript">
import paystack from '../../src';
export default {
    components: {
        paystack
    },
    data(){
        return{
          paystackkey: "pk_test_a137d402b5975716e89952a898aad2832c961d69",
          email: "foobar@example.com",
          amount: 1000000
        }
    },
    computed: {
      reference(){
        let text = "";
        let possible = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

        for( let i=0; i < 10; i++ )
          text += possible.charAt(Math.floor(Math.random() * possible.length));

        return text;
      }
    },
    methods: {
      callback: function(response){
        console.log(response)
      },
      close: function(){
        console.log("Payment closed")
      }
    }
}
</script>
<style>
    .App {
        text-align: center;
    }

    .App-intro {
        font-size: large;
    }
    .payButton{
        color: #61DAFB;
        width: 250px;
        height: 50px;
        font-weight: 800;
    }
</style>
