<template>
<article class="user-card" :class="$mq">
  <aside class="profile">
    <h1 class="name">{{user.name.first}}</h1>
    <img :src="profileImage" alt="FACE">
    <p class="phone" v-if="$mq != 'mobile'">{{user.phone}}</p>
  </aside>
  <main class="details">
    <p class="full-name">{{fullName}}</p>
    <p class="description">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nobis molestiae unde amet. Suscipit corrupti, voluptas incidunt officia laboriosam quia debitis ipsum aperiam perspiciatis veniam natus ea autem? Inventore, esse in.</p>
    <p class="phone">{{user.phone}}</p>
    <p class="email">{{user.email}}</p>
  </main>
</article>
</template>

<script>
export default {
  props: {
    user: Object
  },
  computed: {
    fullName(){ return `${this.user.name.title} ${this.user.name.first} ${this.user.name.last}`},
    
    profileImage(){
      if(this.$mq == 'mobile'){
        return this.user.picture.thumbnail
      }else{
        return this.user.picture.large
      }
    }
  }
}
</script>

<style lang="scss" scoped>
p,h1,h2{ margin: 0.5rem;}
.user-card{
  max-width: 500px;
  max-height: 450px;
  margin: 1rem;
  box-shadow: 0px 2px 5px 1px rgba(61,61,61,0.57);
  border-radius: 5px;
  display: grid;


  grid-template-columns: 1fr 2fr;

  .profile{
    display: flex;
    flex-direction: column;    
    align-items: center;
    justify-content: space-between;
    background-color: #4db6ac;
    padding: 1rem;
    border-radius: inherit;
    box-sizing: border-box;


    .name{
      font-size: 1.5rem;
      color: white;
    }
    .phone{
      color: white;
    }
    img{
      border-radius: 50%;
      border: 10px solid rgba(255,255,255,0.5);      
    }
  }
  &:nth-of-type(2n) .profile{
    background-color: #ba68c8;
  }

  .details{
    padding: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    border-radius: inherit;

    .full-name{ 
      text-align: center; 
      font-size: 1.2rem;
      font-weight: 900;
    }
    .email, .phone{ 
      align-self: flex-end;
      color: grey;
    }
  }

  &.mobile{
    grid-template-columns: 100%;
    grid-template-rows: 1fr 5fr;

    .profile{
      flex-direction: row;

      img{
        order: -1;
      }
    }
  }
}
</style>