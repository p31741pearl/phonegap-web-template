
<!DOCTYPE html>
<html>

<head>
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <script src="https://aframe.io/releases/0.9.1/aframe.min.js"></script>
    <script type="text/javascript" src="cordova.js"></script>

    <script src="https://unpkg.com/aframe-look-at-component@0.8.x/dist/aframe-look-at-component.min.js"></script>

    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>

    <style>
        /*手機尺寸的螢幕*/
        @media only screen and (max-width:480px) {
            * {
                margin: 0px;
                padding: 0px;
                box-sizing: border-box;
            }

            .topp {
                height: 380pt;
                width: 100%;

                z-index: -1;
                position: absolute;
            }


            #inputimg {
                margin: auto;
                display: block;
                margin-bottom: 30px;
            }

            .blockk input,
            #newInput {
                margin-top: 30px;
                margin-bottom: 30px;
                margin: auto;
                display: block;
                text-align: center;
                width: 80%;
                ;
                height: 60pt;
            }



            .blockk i {
                margin-left: 7pt;
                margin-bottom: 10pt;
                text-align: left;
                font-size: 10pt;
                color: white;
            }

            #btn {
                border-radius: 10pt;

                border: 0;

                background-color: #7f8eff;
            }


            #addpoint {
                position: absolute;
                display: block;
                text-align: center;
                width: 360pt;
                height: 20pt;
                margin-top: 380pt;
                border: none;
            }

            #checkk {
                display: none;
                float: right;
                margin-top: 300pt;

            }

            #deletee {
                display: none;
                float: right;
                margin-top: 305pt;
            }

            .mybtn {
                background-color: blue;
                color: #fff;
                float: right;
                margin-top: 300pt;
                display: none;
            }

            #wordd {
                height: 300pt;
                width: 90%;
                background-color: #ffffff;
                border-radius: 5pt;
                display: none;
                z-index: -2;
                float: right;
                margin: auto;
                margin-top: 20pt;
                margin-right:15pt; 

            }

        }
    </style>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">


    <script>
        var stt = 0;
        AFRAME.registerComponent('cursor-listener', {

            init: function fi() {
                var adddd = document.getElementById('addpoint'); /*底下加號按鈕*/
                var q = 0; /*圓標設id*/
                var entityE2 = document.querySelector('a-scene');


                 var nuu =0;
                var s = adddd.addEventListener('click', function() {

                    d = document.createElement('a-entity');

                    d.id = q;
                    entityE2.appendChild(d);
                    console.log(q);

                    /*取滑鼠座標*/
                    var i = document.getElementById('clickPosition').object3D.getWorldPosition();
                    var addddddd = entityE2.addEventListener('click', function add() {
                        console.log("加");
                        /*加圓點*/
                        d.setAttribute('position', {
                            x: i.x,
                            y: i.y,
                            z: i.z
                        });
                        d.setAttribute('geometry', {
                            primitive: 'sphere',
                            radius: 3,
                            segmentsWidth: 20,
                            segmentsHeight: 20,

                        });
                        d.setAttribute('cursor-listener', '');
                       
                        d.addEventListener('click', function() {
                           var worddd = document.getElementById('wordd');
                            worddd.style.display = 'block';
                           var wri = document.getElementById("ie"+nuu);
                            console.log("哀低多少啦啦啦"+wri.id);
                            var sentence=document.createElement('p');
                            sentence.innerHTML=wri.value;
                            worddd.appendChild(sentence);
                            nuu=nuu+1;
                            /*  var rr =document.getElementById("inputword");
                              
                              console.log("跳出來哦"+rr.value);*/
                        });




                        /*加號鍵消失*/
                        document.getElementById('addpoint').style.display = 'none';
                        /*勾勾跟刪除鍵出現*/
                        document.getElementById('checkk').style.display = 'block';
                        document.getElementById('deletee').style.display = 'block';
                        console.log(d.id);
                        q = q + 1;
                        console.log(i.x);
                        console.log(i.y);
                        console.log(i.z);
                        entityE2.removeEventListener('click', add);

                    });

                });

                /*刪除鍵功能*/
                document.getElementById('deletee');
                deletee.addEventListener('click', function() {
                    d.removeAttribute('geometry');
                    document.getElementById('addpoint').style.display = 'block';

                    document.getElementById('checkk').style.display = 'none';
                    document.getElementById('deletee').style.display = 'none';
                    console.log("刪了沒阿");


                    stt = 1;

                });

                /*
                      if(stt=1){
                            AFRAME.registerComponent('handle-events', {
                                  init: function() {
                                      var el = this.el; 
                                       const formElement = document.getElementById("newInput");
                                  const name = formElement.value;
                             console.log(name);
                               
                           
                                      el.addEventListener('click', function() {
                                          el.setAttribute('color', '#ff2424');
                                      });
                                    
                                      el.addEventListener('click', function() {
                                          el.setAttribute('scale', {
                                              x: 2,
                                              y: 1,
                                              z: 2
                                          });
                                      });
                                     
                                  }
                              })
                      }*/
                /*點擊顯示輸入的文字*/

                /* d.addEventListener('click', function() {
                   
                      const formElement = document.getElementById("newInput");
                 const name =  formElement.value;
                     console.log("做事");
                     alert("你的姓名是 " + name);

                 });*/
                /*deletee.addEventListener('click', function() {
                             document.getElementById('q');
                     
                             q.entityE2.removeChild(q);
                                document.getElementById('addpoint').style.display = 'block';

                                document.getElementById('checkk').style.display = 'none';
                                document.getElementById('deletee').style.display = 'none';
                    console.log("刪了沒阿");

                            });*/
            },

        });
    </script>




</head>

<body>

    <div style="position:relative;">
        <div class="topp">
            <a-scene id="hey" embedded>
                <a-sound src="src: url(Sequence 02.mp3)" autoplay="true" position="0 2 5"></a-sound>
                <a-entity camera look-controls>
                    <a-entity cursor="fuse: true; fuseTimeout: 500" position="0 0 -1" geometry="primitive: ring; radiusInner: 0.02; radiusOuter: 0.03" material="color: black; shader: flat">
                    </a-entity>
                    <a-entity id="clickPosition" position="0 0 -100"></a-entity>
                    <a-entity id="pic" cursor-listener></a-entity>
                </a-entity>
                <a-sky id="you" src="360_0096_Stitch_XHC.JPG"></a-sky>

            </a-scene>
        </div>
        <div id="wordd"><img id="fine" src="check.png" ></div>
        <div class=container id="boxx">
            <div class="btn mybtn" id="checkk" data-toggle="modal" data-target="#my_modal">
                <img src="check.png" onclick="checkk();">
            </div>

            <div class="modal" id="my_modal">
                <div class="modal-dialog modal-sm">
                    <div class="modal-content">

                        <!--header-->
                        <div class="modal-header">

                            <div class="hey">
                                <button id="btn" onclick="addElementInput()">type</button>
                                <button id="btn" onclick="addElementInput1()">image</button>
                            </div>

                            <h3>Add new things!</h3>
                        </div>
                        <!--body-->
                        <div class="modal-body">
                            <div id="parent"></div>
                        </div>
                        <!--footer-->
                        <div class="modal-footer">

                            <img src="check.png" data-action="submit">
                        </div>

                    </div>
                </div>
            </div>

        </div>

        <img id="deletee" src="delete.png" cursor-listener>
        <div class="bottombar">
            <button id="addpoint" cursor-listener>+</button>
        </div>

    </div>
</body>

<script language="javascript">
    var i = 0

    function addElementInput() {

        var parent = document.getElementById("parent");

        //添加 div

        var input = document.createElement("input");

        /* input.setAttribute("id", idd);*/
       
        input.setAttribute("placeholder", "這是怎樣的回憶呢");

    

        parent.appendChild(input);
        input.setAttribute("id","ie"+i);
      /*  var jjjjjj = document.getElementsByTagName("input");*/
        //设置 div 属性，如 id
        /*  for(var i=0;i<objs.length;i++)
{
objs[i].id= i;};*/

       /* jjjjjj[i].id = i;
        var wee =parent.document.getElementById(i).value;*/
        
        console.log("哀是" + i);
    /*    console.log("哀低" + jjjjjj[i]);
         console.log("內容"+wee);*/
        console.log(input.id);
       
        i = i + 1;
    }


    function addElementInput1() {

        var parent = document.getElementById("parent");
        var bigImg = document.createElement("img"); //创建一个img元素
        bigImg.setAttribute("id", "inputimg");
        bigImg.src = "person.jpg"; //给img元素的src属性赋值
        //bigImg.width="320";  //320个像素 不用加px

        parent.appendChild(bigImg); //为dom添加子元素img

    }

    /*按下勾勾後跳出文字輸入框然後自己跟刪除鍵消失*/
    function checkk() {
        qq = 1;

        document.getElementById('checkk').style.display = 'none';
        document.getElementById('deletee').style.display = 'none';

        console.log("這裡");


    };
    const submitBtn = document.querySelector('[data-action="submit"]');
    submitBtn.addEventListener("click", processFormData);
    var inputword = 0;

    function processFormData(e) {
        // 方法 1-1：getElementById - 從 input
        // const nameElement = document.getElementById("name");
        // const name = nameElement.value;
        // const emailElement = document.getElementById("email");
        // const email = emailElement.value;

        // 方法 1-2：getElementById - 從 form
        /*  const formElement = document.getElementById("newInput");
           const name = newInput.value;
           formElement.setAttribute("id", "inputword");
           // 方法 2：getElementsByTagName
           inputword=inputword+1;
           // const inputElement = document.getElementsByTagName('input');
           // const name = inputElement[0].value;
           // const email = inputElement[1].value;

           // 方法 3：getElementsByName
           // const nameElement = document.getElementsByName('name');
           // const name = nameElement[0].value;
           // const emailElement = document.getElementsByName('email');
           // const email = emailElement[0].value;

           alert(name);*/
        var i=0;
        $('#my_modal').hide();
        //切換視窗顯示、不顯示
        $("#my_modal").modal('toggle');
        document.getElementById('addpoint').style.display = 'block';
        /* var okk =$("addElementInput");*/
        /*var iii =$('input')[i].value;*/
        var wee =parent.document.getElementById("ie"+i).id;
         var weee =parent.document.getElementById(wee);
        var weeee=weee.value;
        console.log("wee"+weeee);
            i=i+1;

    }
</script></html>
