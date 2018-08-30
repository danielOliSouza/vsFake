<template>
    <div>
        <div v-for="msg in msgs" :key="msg.id">
            <div>WAIT Compiling...</div>
            <div>{{msg.per}}% after emitting CopyPlugin</div>
            <div v-if="msg.per == 98">DONE Compiled successfully in {{ Math.floor(Math.random() * 1000) +100}}ms</div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            msgs: null,
        }
    },
    created(){
        this.msgs = [];
        setInterval(()=>{ 
            let msg = {};
            this.msgs.push(msg);
    
            msg.id = this.msgs.length;
            msg.per = 0;
 
            setTimeout(()=>{
                msg.per = 98
            }, 1000);

        }, 5000);
    },
    methods: {
        sleep(m){
            let start = new Date().getTime();
            for(var i = 0; i < 1e7; i++){
                if((new Date().getTime() - start) > m){
                    break;
                }
            }
        }
    }
}
</script>

<style scoped>

</style>
