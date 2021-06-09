<template>
  <div>
    <h1 class="divider"></h1>
    <div>
      <table class="detail table table-bordered">
        <tbody>
        <tr class="active">
          <td>일련번호</td>
          <td>{{contact.no}}</td>
        </tr>
        <tr class="active">
          <td>이름</td>
          <td>{{contact.name}}</td>
        </tr>
        <tr class="active">
          <td>전화</td>
          <td>{{contact.tel}}</td>
        </tr>
        <tr class="active">
          <td>주소</td>
          <td>{{contact.address}}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
  import contactlist from '../ContactList'

  export default {
    name    : "ContactByNo",
    props : ['no'],
    data    : function () {
      return {
        contacts: contactlist.contacts
      }
    },
    computed: {
      contact: function () {
        var no = this.no;
        var arr = this.contacts.filter(function (item, index) {
          return item.no == no;
        });
        if (arr.length == 1) {
          return arr[0];
        } else {
          return {};
        }
      }
    },
    // watch   : {
    //   //to는 현재 라우트 객체, from은 이전의 라우트 객체
    //   '$route': function (to, from) {
    //     this.no = to.params.no;
    //   }
    // }
  }
</script>

<style scoped>
  table.detail {
    width: 400px;
  }

  .divider {
    height: 3px;
    margin-left: auto;
    margin-right: auto;
    background-color: #FF0066;
    color: #FF0066;
    border: 0 none;
  }
</style>
