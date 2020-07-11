<template>
    <div class="component">
        <h1>The User Component</h1>
        <p>I'm an awesome User!</p>
        <button v-on:click="changeName">Change my name</button>
        <hr>
        <div class="row">
            <div class="col-xs-12 col-sm-6">
            <!-- make sure to use @ to listen to event passed from children components -->
              <!-- pass myName as a prop || nameWasReset, resentFn,userAge are props sent from the child component UserDetail.vue to parent User.vue -->
                <app-user-detail :myName="name" @nameWasReset="name = $event" :resentFn="resetName" :userAge="age"></app-user-detail>
            </div>
            <div class="col-xs-12 col-sm-6">
              <!-- pass userAge as a prop  -->
                <app-user-edit :userAge="age" @ageWasEdited="age = $event"></app-user-edit>
            </div>
        </div>
    </div>
</template>

<script>
    import UserDetail from './UserDetail.vue';
    import UserEdit from './UserEdit.vue';

    export default {

        data : function() {
          return {
            name: 'Fred',
            age: 26
          };
        },
        methods: {
          changeName() {
            this.name = "Ana";
          },
          resetName() {
            this.name = "Fred";
          }
        },
        components: {
            appUserDetail: UserDetail,
            appUserEdit: UserEdit
        }
    }
</script>

<style scoped>
    div {
        background-color: lightblue;
    }
</style>
