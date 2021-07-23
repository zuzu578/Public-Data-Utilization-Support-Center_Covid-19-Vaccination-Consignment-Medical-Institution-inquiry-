<template>
  <div>
      <h1>공공데이터활용지원센터_코로나19 예방접종 위탁의료기관 조회서비스</h1>
         <!-- 현재 페이지를 임시로 보여줍니다( paging ) -->
      <input type="hidden" name="current_page" id="current_page" value='1'>

      <div class="Search_bar">
<div class="input-group mb-3">
  
  <input type="text" class="form-control" name="location_title" id="location_title" v-model= "location_title" ref="location_title" placeholder="지역명으로 검색" aria-label="Username" aria-describedby="basic-addon1">
    <button type="button" @click="search()" class="btn btn-dark">검색</button>

</div>
</div>
<!-- data Area --> 
    <div class="data_area" v-for="(jsonData, idx) in boardData" :key="idx">
        <div class="day">
        요일:{{jsonData.dywk}}
        </div>
        <div class="end_time">
          종료시간:{{jsonData.endTm}}
        </div>
        <div class="lunch_end">
            점심 종료시간 :{{jsonData.lunchEndTm}}
        </div>
        <div class="phone">
              전화번호 :{{jsonData.orgTlno}}
        </div>
        <div class="add1">
                도로명 주소 :{{jsonData.orgZipaddr}}
        </div>
        <div class="add2">
                  기관 주소 :{{jsonData.orgnm}}
        </div>
        <div class="update_date">
                    업데이트 날짜 :{{jsonData.slrYmd}}
                </div>
               

   </div>
    <!-- 데이터가 없는경우 -->
    <div class="message">
    <a v-if="boardData.length == 0" class="list-group-item list-group-item-action">
      데이터가 존재하지 않습니다.
    </a>
    </div> 
           <!-- pageNation Area !-->
<div class="paging">
  <nav aria-label="Page navigation example">
  <ul class="pagination">
    
    <li class="page-item" @click="prev()">prev</li> 
    <li class="page-item" @click="next()">next</li>
    
  </ul>
</nav>
</div>
  </div>
 
  
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            boardData:'',
            location_title:'',
            defaultPageNum : '',
        }
    },
    created(){
    
    },
    mounted(){

    },
    methods:{
        // 지역을 기준으로 검색한 데이터를 가져옵니다.
        // ex) parameter : 충청남도 => 충청남도 예방접종 위탁의료기관 데이터를 가져옵니다. 
        search(){
            console.log("location_title ==> " + this.location_title);
            axios.get('http://localhost:8082/myapp/getConsignedmedicalinstitutionApi',{
        params:{
            location_title:this.location_title
        }
        
    })
        
    .then((res)=>{
        //get Data List 
        console.log(res.data.data);
        this.boardData = res.data.data;
        // data 가 존재하지 않는경우 
        if(this.boardData.length ==  0 ){
            alert("데이터가 존재하지않습니다.")
            return false;
        }
    }) 
        },  //이전페이지 보여주기 
    prev(){
      var pageNum = document.getElementById('current_page').value
      var currentPageNum = parseInt(pageNum) -1;
       document.getElementById('current_page').value = currentPageNum;
      //alert(currentPageNum);
      console.log(currentPageNum)
      this.defaultPageNum = currentPageNum;
      console.log("현재 페이지 ==> " + this.defaultPageNum);
      if(this.defaultPageNum <= 0 ){
          console.log("이전 데이터가 없습니다.")
          // - 값이 된 페이지를 초기 값으로 복원합니다.
          this.defaultPageNum = 1;
          return false;
      }
       axios.get('http://localhost:8082/myapp/getConsignedmedicalinstitutionApi',{
        params: {
        defaultPageNum : this.defaultPageNum,
        location_title:this.location_title
        }
    }) 
    .then((res)=>{
        //get Data List 
        console.log(res.data.data);
        this.boardData = res.data.data;
    })
      
      
    },
    //다음페이지 보여주기 
    next(){
      var pageNum = document.getElementById('current_page').value
      var currentPageNum = parseInt(pageNum) +1;
      document.getElementById('current_page').value = currentPageNum;
      //alert(currentPageNum);
      console.log(currentPageNum)
      this.defaultPageNum = currentPageNum;
      console.log("현재 페이지 ==> " + this.defaultPageNum);
      axios.get('http://localhost:8082/myapp/getConsignedmedicalinstitutionApi',{
        params: {
        defaultPageNum : this.defaultPageNum,
        location_title:this.location_title
        }
    }) 
    .then((res)=>{
        //get Data List 
        console.log(res.data.data);
        this.boardData = res.data.data;
    })
    }
    }
}
</script>

<style>
.message{
    width: 700px;
    margin: 0 auto;
}
.Search_bar{
    width:700px;
    padding-top:40px;

    margin: 0 auto;
}
.page-item{
    width:50px;
    border:1px solid black;
    font-weight:bold;
    cursor: pointer;
}
@import 'https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css'
</style>