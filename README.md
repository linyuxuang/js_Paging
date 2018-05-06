# js_Paging
纯js_分页

  自己写的  js  分页  
  
          <div id="div1"></div>
  
  

                 window.onload=function(){
                    paeg({
                        id:"div1",
                        nowNum:2,
                        allNum:10
                    })
                  };
                function paeg(obj){
                   if(!obj.id){
                       return false;
                   }
                   var divs=document.getElementById(obj.id);
                   var nowNums=obj.nowNum|| 1;
                   var allNums=obj.allNum||5;
                    if(nowNums>=4 && allNums>=6){
                       var shouye=document.createElement("a");
                        shouye.href="#1";
                        shouye.innerHTML="首页";
                        divs.append(shouye)
                     }
                    if(nowNums>=2){
                      var shangyiye=document.createElement("a");
                        shangyiye.href="#"+(nowNums-1);
                        shangyiye.innerHTML="上一页";
                        divs.append(shangyiye)
                    }
                   if(allNums<=5){
                      for(var i=1;i<allNums;i++){
                         var ca_a=document.createElement("a");
                          ca_a.href="#"+i;
                          if(nowNums==i){
                             ca_a.innerHTML=i;
                           }else{
                              ca_a.innerHTML='['+i+']';
                           }
                          divs.append(ca_a)
                       }
                   }else{
                      for(var i=1;i<=5;i++){
                        var oa=document.createElement("a");
                          if(nowNums==1||nowNums==2){
                             oa.href="#"+i;
                              if(nowNums==i){
                                  oa.innerHTML=i;
                              }else{
                                  oa.innerHTML='['+i+']'
                              }
                          }else if((allNums-nowNums==0)||(allNums-nowNums==1)){
                              oa.href="#"+(allNums-5+i);
                              if(allNums-nowNums==0 && i==5){
                                  oa.innerHTML=(allNums+i-5);
                              }else if(allNums-nowNums==1 && i==4){
                                  oa.innerHTML=(allNums+i-5);
                              }
                              else{
                                  oa.innerHTML='['+(allNums-5+i)+']'
                              }
                          }else{
                              oa.href="#"+(nowNums-3+i);
                              if(i==3){
                                  oa.innerHTML=(nowNums-3+i);
                              }else{
                                  oa.innerHTML='['+(nowNums-3+i)+']';
                              }
                            }
                          divs.append(oa)
                        }
                      }
                     if((allNums-nowNums)>=1){
                        var xiayiye=document.createElement("a");
                        xiayiye.href="#"+(nowNums+1);
                        xiayiye.innerHTML="下一页";
                        divs.append(xiayiye)
                    }
                    if((allNums-nowNums)>=3 && allNums>=6){
                        var weiye=document.createElement("a");
                         weiye.href="#"+(allNums);
                         weiye.innerHTML="尾页";
                         divs.append(weiye)
                     }
                    var a_obj=divs.getElementsByTagName("a");
                    for(var i=0;i<a_obj.length;i++){
                       a_obj[i].onclick=function(){
                        var hrf_a=parseInt(this.getAttribute("href").substring(1));
                          divs.innerHTML="";
                          paeg({
                              id:obj.id,
                              nowNum:hrf_a,
                              allNum:allNums
                          })
                       }
                     }
                  }
