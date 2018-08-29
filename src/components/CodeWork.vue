<template>
    <div id="code-work">
        <b-row>
            <b-col id="numLines" cols="1" sm="1" md="1" lg="1" xl="1" >
                <div  v-for="n in num" :key="n">
                    {{n}}
                </div>
            </b-col>
            <b-col  cols="11" sm="11" md="11" lg="11" xl="11">
                <pre style="color: #2568ca; font-size: 14px">
{{codeWorked}}
                </pre>
            </b-col>
        </b-row>

    </div>
</template>

<script>
export default {
    data(){
        return {
            countKeyUp: 0,
            code: null,
            codeWorked: null,
            num: 1,
        }
    },
    created: function () {
        window.addEventListener('keyup', this.getKeyUp)
        this.$http.get('/index.html').then((resp)=>{
            this.code = resp.data.trim();
        });
    },
    methods: {
        getKeyUp(event){
            if(event.which == 8){
                if(this.countKeyUp){
                    this.countKeyUp = this.countKeyUp - 3;
                }
            }
            else{
                if(event.which >= 32 && event.which <= 128)
                this.countKeyUp = this.countKeyUp + 3;
            }

            if(this.countKeyUp > this.code.length){
                this.countKeyUp = this.countKeyUp / 2;
            }
            this.codeWorked = this.code.substring(0, this.countKeyUp);

            this.num = this.codeWorked.split('\n').length;
            document.getElementById('code-work').offsetHeight = 
                document.getElementById('code-work').offsetHeight + 3;
        }
    }
}
</script>

<style escoped>
    #code-work{
        height: 100%;
        width: 100%;
        overflow-x: visible;
        overflow-y: scroll;
    }
    #numLines{
        color: #AAA;
    }
</style>
