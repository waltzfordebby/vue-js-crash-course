<template>
    <div class="test">
        <span v-html="title1"></span>
        <p>{{title2}}</p>
        <p>{{user.firstName}}</p>
        <p>{{user.lastName}}</p>
        <p v-if="showName">{{user.firstName}}</p>
        <p v-else>Nobody</p>
        <ul>
            <li v-for="item in items" :key="item.id">{{item.title}}</li>
        </ul>
        <button v-on:click="greet('Hello World')">Say Greeting</button>
        <br>
        <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
        <hr>
        <label for="">FirstName</label><input type="text" v-model="user.firstName">
        <br>
        <label for="">LastName</label><input type="text" v-model="user.lastName">
        <h3>{{fullName}}</h3>
        <h2>{{msg}}</h2>
    </div>
</template>

<script>
export default {
    name:'test',
    props:{
        msg:{
            type:String,
            default:'Foobar'
        }
    },
    data (){
        return {
            title1:'<h1>Hello World</h1>',
            title2:'Hello World',
            user:{
                firstName:'John',
                lastName:'Doe'
            },
            showName:true,
            items:[
                {title:'Item One'},
                {title:'Item Two'},
                {title:'Item Three'}
            ]
        }
    },
    methods:{
        greet:function(greeting){
            alert(greeting);
        },
        pressKey:function(e){
            console.log(e.target.value);
        },
        enterHit:function(){
            alert('You hit enter!');
        }
    },
    computed:{
        fullName:function(){
            return this.user.firstName+' '+this.user.lastName;
        }
    }
}
</script>

