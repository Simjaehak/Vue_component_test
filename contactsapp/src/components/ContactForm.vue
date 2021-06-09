<template>
    <div class="modal">
      <div class="form" @keyup.esc="cancelEvent">
        <h3 class="heading">::{{headingText}}</h3>
        <div v-if="mode=='update'" class="form-group">
          <label>일련번호</label>
          <input type="text" name="no" class="long" disabled v-model="contact.no">
        </div>
        <div class="form-group">
          <label>이름</label>
          <input type="text" name="name" class="long" v-model="contact.name"
          ref="name" placeholder="이름을 입력하시오">
        </div>
        <div class="form-group">
          <label>전화번호</label>
          <input type="text" name="tel" class="long" v-model="contact.tel" placeholder="전화번호를 입력하세요">
        </div>
        <div class="form-group">
          <label>주소</label>
          <input type="text" name="address" class="long" v-model="contact.address" placeholder="주소를 입력하세요">
        </div>
        <div class="form-group">
          <div>&nbsp;</div>
          <input type="button" class="btn btn-primary"
          :value="btnText" @click="submitEvent()">
          <input type="button" class="btn btn-primary" value="취소" @click="cancelEvent()">
        </div>
      </div>
    </div>
</template>

<script>
    export default {
        name: "contactForm",
        props : {
          mode : { type:String , default:'add'},
          contact : {
            type: Object,
            default: function(){
              return {no : '',name : '', tel : '', address : '', photo : ''}
            }
          }
        },
      mounted : function(){
          this.$refs.name.focus()
      },
      computed : {
          btnText : function(){
            if(this.mode != 'update') return '추가';
            else return '수정';
          },
          headingText : function(){
            if(this.mode != 'update') return '새로운 연락처 추가';
            else return '연락처 변경';
          }
      },
      methods : {
          submitEvent : function(){
            if(this.mode == "update"){
              eventBus.$emit("updateSubmit", this.contact)
            }else {
              eventBus.$emit("addSubmit",this.contact);
            }
          },
          cancelEvent : function(){
            eventBus.$emit('cacel');
          }
      }

    }
</script>

<style scoped>

</style>
