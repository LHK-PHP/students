# students<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>购物车</title>
    <style type="text/css">
        table
        {
            border-collapse:collapse;
        }
    </style>
    <script src="../jquery/jquery-3.4.1.js"></script>
</head>
<body>
<h2>真划算</h2>
<table border="1">
    <tr style="background: #6a7074">
        <td>商品</td>
        <td>单价(元)</td>
        <td>颜色</td>
        <td>库存</td>
        <td>好评率</td>
        <td>操作</td></tr>
    <tr class="d1">
        <td class="names">罗技M185鼠标</td>
        <td class="price">80</td>
        <td >黑色</td>
        <td >893</td>
        <td > 98%</td>
        <td ><button class="goods">加入购物车</button></td></tr>
    <tr>
        <td class="names">微软X470键盘</td>
        <td class="price">150</td>
        <td>黑色</td>
        <td>9028</td>
        <td>96%</td>
        <td><button class="goods">加入购物车</button></td>
    </tr>
    <tr>
        <td class="names">浩克iPhone6手机壳</td>
        <td class="price">60</td>
        <td>透明</td>
        <td>672</td>
        <td>99%</td>
        <td><button class="goods">加入购物车</button></td></tr>
    <tr>
        <td class="names">蓝牙耳机</td>
        <td class="price">100</td>
        <td>蓝色</td>
        <td>8937</td>
        <td>95%</td>
        <td ><button  class="goods">加入购物车</button></td></tr>
    <tr>
        <td class="names">金士顿U盘</td>
        <td class="price"> 70</td>
        <td>红色</td>
        <td>482</td>
        <td>100%</td>
        <td><button class="goods" >加入购物车</button></td></tr>
</table>
<h1>购物车</h1>
<table border="1" >
    <tr style="background: #6a7074" class="car">
        <td>商品</td>
        <td>单价(元)</td>
        <td>数量</td>
        <td class="result_price">金额(元)</td>
        <td>删除</td>
        </tr>
    <tr>
        <td colspan="3">总计</td>
        <td class="result"></td>
        <td></td></tr>
</table>
</body>
<script>
       var num = 1;
       var price1;
       totals();
       $(document).on( 'click','.goods',function () {
           //获取以索引为具体得内容
           var uo = $('.goods').index(this);
           //获取商品的名称
           var index = $('.names').eq(uo).text();
           //获取商品的价格
            price = $('.price').eq(uo).text();
           //加入商品的信息到购物车里面
        if(''){}
           $('<tr class="com">'+'<td class="shopname">'+index+'</td>'+'<td class="zi">'+price+'</td>'+'<td><button class="jian">-</button>\n' + '<input type="text" value="1" size="6" class="textt"><button class="jia">+</button></td><td class="goods1">'+price+'</td><td><button class="rem">×</button></td>+'+'</tr>').insertAfter('.car')
           //触发结算函数事件
           totals()
           $('.shopname').
       })
       //点击加号数量加
    $(document).on('click','.jia',function () {
        var index = $('.jia').index(this);
        var type = $(this).text();
        numfunction(type,index)
    })
       //点击减号数量减
    $(document).on('click','.jian',function () {
        var index = $('.jian').index(this);
        var type = $(this).text();
        numfunction(type,index)
    })
       //删除商品
       $(document).on('click','.rem',function () {
           var index = $('.rem').index(this);
           $('.com').eq(index).remove();
           totals()
       })
       //封装函数为加减余额判断
    function numfunction(type,index) {
        //获取单价为80
        var index1 = $('.zi').eq(index).html();
        //获取下标为点击位置的内容
        var num = $('.textt').eq(index).val();
        if (type == '+'){
            num++;
        }else if(type == '-'){
            //当数量小于2时对减号按钮进行限制
            if (num < '2'){
                $('.jian').eq(index).attr('disabled','disabled')
                   }
            else {
                num--;
            }
            totals()
        }
        // console.log(index);
        // 将获得的值传入界面上的内容
        $('.textt').eq(index).val(num);
        $('.goods1').eq(index).html(index1*num)
        totals()
    }
    //结算所有的商品的价格
 function totals() {
           var arr = $('.goods1');
           for (var i =0;i<arr.length;i++){
               var total = $('.goods1').eq(i).text();
               // console.log(i);
               total +=Number(total[i]);
           }
           $('.result').text(total )
       }
</script>
</html>
