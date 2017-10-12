###   标题1

``` python
    //提交按钮事件
        function subEvt(){
            btn.onclick = function(){
                createModal();
            };
        }
        function createModal(){
            /*<div class="modal">
             <div class="pop_main">
             <div class="pop_con">
             <h3 class="pop_tit">√</h3>
             <p class="desc">恭喜你，提交成功！</p>
             <p class="about">已扣除10微币</p>
             <a href="javascript:void(0);" class="confirm">确定</a>
             </div>
             <a href="javascript:void(0)" class="close">X</a>
             </div>
             </div>*/
            var h1 = document.createElement('h3');
            h1.className = 'pop_tit';
            h1.innerHTML = '√';

            var p1 = document.createElement('p');
            p1.className = 'desc';
            p1.innerHTML = '恭喜你，提交成功！';

            var p2 = document.createElement('p');
            p2.className = 'about';
            p2.innerHTML = '已扣除10微币';

            var a1 = document.createElement('a');
            a1.href = "javascript:void(0);";
            a1.className = 'confirm';
            a1.innerHTML = '确定';

            var div1 = document.createElement('div');
            div1.className = 'pop_con';
            div1.appendChild(h1);
            div1.appendChild(p1);
            div1.appendChild(p2);
            div1.appendChild(a1);

            var a2 = document.createElement('a');
            a2.href = "javascript:void(0);";
            a2.className = 'close';
            a2.innerHTML = 'X';

            var div2 = document.createElement('div');
            div2.className = 'pop_main';
            div2.appendChild(div1);
            div2.appendChild(a2);

            var div3 = document.createElement('div');
            div3.className = 'modal';
            div3.appendChild(div2);

            wrap.appendChild(div3);

            centerBlock(div2);
            resize(div2);

            close(a2,div3);
            close(a1,div3);
        }
```

###  标题2

``` python
    //提交按钮事件
        function subEvt(){
            btn.onclick = function(){
                createModal();
            };
        }
        function createModal(){
            /*<div class="modal">
             <div class="pop_main">
             <div class="pop_con">
             <h3 class="pop_tit">√</h3>
             <p class="desc">恭喜你，提交成功！</p>
             <p class="about">已扣除10微币</p>
             <a href="javascript:void(0);" class="confirm">确定</a>
             </div>
             <a href="javascript:void(0)" class="close">X</a>
             </div>
             </div>*/
            var h1 = document.createElement('h3');
            h1.className = 'pop_tit';
            h1.innerHTML = '√';

            var p1 = document.createElement('p');
            p1.className = 'desc';
            p1.innerHTML = '恭喜你，提交成功！';

            var p2 = document.createElement('p');
            p2.className = 'about';
            p2.innerHTML = '已扣除10微币';

            var a1 = document.createElement('a');
            a1.href = "javascript:void(0);";
            a1.className = 'confirm';
            a1.innerHTML = '确定';

            var div1 = document.createElement('div');
            div1.className = 'pop_con';
            div1.appendChild(h1);
            div1.appendChild(p1);
            div1.appendChild(p2);
            div1.appendChild(a1);

            var a2 = document.createElement('a');
            a2.href = "javascript:void(0);";
            a2.className = 'close';
            a2.innerHTML = 'X';

            var div2 = document.createElement('div');
            div2.className = 'pop_main';
            div2.appendChild(div1);
            div2.appendChild(a2);

            var div3 = document.createElement('div');
            div3.className = 'modal';
            div3.appendChild(div2);

            wrap.appendChild(div3);

            centerBlock(div2);
            resize(div2);

            close(a2,div3);
            close(a1,div3);
        }
```