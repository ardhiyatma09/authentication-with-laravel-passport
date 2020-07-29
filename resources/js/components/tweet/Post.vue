<template>
    <div>
        <form action="#" @submit.prevent="post">
            <div class="form-group">
                <textarea cols="30" rows="2" class="form-control" v-model="body"></textarea>
            </div>
            <button class="btn btn-primary" type="submit">Post</button>
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            body:null
        }
    },
    props:{
        tweets: Array
    },
    methods:{
        post(){
            axios.post('/tweets',{
                body:this.body
            }).then((result) => {
                this.tweets.unshift(result.data);
                this.body = null;
            }).catch((err) => {
                console.log(err);
            });
        }
    }
}
</script>