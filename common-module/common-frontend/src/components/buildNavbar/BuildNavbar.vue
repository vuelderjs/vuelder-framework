<template>
  <nav>
    <v-app-bar>
        <v-row>
            <v-btn plain v-if="leftMenuState">
                <v-icon>menu</v-icon>
            </v-btn>
            <v-spacer></v-spacer>
                <v-btn plain class="font-weight-medium">{{title}}</v-btn>
            <v-spacer></v-spacer>
            <v-btn plain v-if="rightMenuState">
                <v-icon>person</v-icon>
            </v-btn>
        </v-row>
    </v-app-bar>
  </nav>
</template>

<script>
export default {
    props:{
        title: {
            type: String,
            default: 'Titulo'
        },
        leftMenu: {
            type: Object,
            default(){
                return{
                    value: true,
                    mobile: true,
                    desktop: true
                }
            }
        },
        rightMenu: {
          type: Object,
            default(){
                return{
                    value: true,
                    mobile: true,
                    desktop: true
                }
            }
        }
    },
    computed:{
        leftMenuState(){
            if(!this.leftMenu.value) return false
            if(this.leftMenu.mobile && this.$vuetify.breakpoint.smAndDown) return true
            if(this.leftMenu.desktop && this.$vuetify.breakpoint.smAndUp) return true
            return false
        },
        rightMenuState(){
            if(!this.rightMenu.value) return false
            if(this.rightMenu.mobile && this.$vuetify.breakpoint.smAndDown) return true
            if(this.rightMenu.desktop && this.$vuetify.breakpoint.smAndUp) return true
            return false
        },
    }
}
</script>

<style>

</style>