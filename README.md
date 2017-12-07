# Hallo-Welt
Dies ist mein erstes Repository auf GitHub. Ich hoffe, es kann mir helfen, meine Aufgabe fließend zu beenden.
<!DOCTYPE html>
<html>
<body>

<p id="testtext"></p>
<p id="chiffretext"></p>
<p id="klartext"></p>
<p id="dezimaltext"></p>
<p id="akkumulieren1"></p>
<p id="akkumulieren2"></p>

<script>

//变量名称为大写字母，id为与变量名称相对应的小写字母
//CHIFFRETEXT   密文
//KLARTEXT      片假名
//TESTTEXT      测试文本
//DEZIMALTEXT   十进制文本
//AKKUMULIEREN1  前累加密文
//AKKUMULIEREN2  后累加密文

var TESTTEXT = "我爱你2333！I love you. 私はあなたを愛している";
document.getElementById("testtext").innerHTML=TESTTEXT;

//转为unicode编码
function encodeUnicode(str) 
{  
    var res = [];  
    for ( var i=0; i<str.length; i++ ) 
    {  
      res[i] = ( "00" + str.charCodeAt(i).toString(16) ).slice(-4);  
    }  
    return res; 
}  

var CHIFFRETEXT=encodeUnicode(TESTTEXT);

//转为十进制数字
function getDezimaltext(str) 
{  
    var res = [];  
    for ( var i=0; i<str.length; i++ ) 
    {  
      res[i] =parseInt(CHIFFRETEXT[i],16);  
    }  
    return res; 
}  

var DEZIMALTEXT=getDezimaltext(CHIFFRETEXT);
document.getElementById("dezimaltext").innerHTML=DEZIMALTEXT;

//前累加加密
function getAkkumulieren1(str)
{
    var res=[];
    var i;
    for ( i=0; i<str.length-1; i++ ) 
        {
          res[i]=str[i]+str[i+1];
        } 
        res[i]=str[i];
        return res;
}

var AKKUMULIEREN1=getAkkumulieren1(DEZIMALTEXT);
document.getElementById("akkumulieren1").innerHTML=AKKUMULIEREN1;

//后累加加密
function getAkkumulieren2(str)
{
    var res=[];
    var i;
    for ( i=str.length-1; i>0; i-- ) 
        {
          res[i]=str[i]+str[i-1];
        } 
        res[i]=str[i];
        return res;
}

var AKKUMULIEREN2=getAkkumulieren2(AKKUMULIEREN1);
document.getElementById("akkumulieren2").innerHTML=AKKUMULIEREN2;

</script>

</body>
</html>
