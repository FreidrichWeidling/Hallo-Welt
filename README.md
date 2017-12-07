# Hallo-Welt
Dies ist mein erstes Repository auf GitHub. Ich hoffe, es kann mir helfen, meine Aufgabe fließend zu beenden.
<!DOCTYPE html>
<html>
<body>

<p id="testtext"></p>
<p id="Chiffretext"></p>
<p id="Klartext"></p>

<script>

//变量名称为大写字母，id为与变量名称相对应的小写字母
//Chiffretext 密文
//Klartext    明文
//Testtext    测试文本

var TESTTEXT = "我爱你2333！？。I love you. 私はあなたを愛している!";
document.getElementById("testtext").innerHTML=TESTTEXT;

//转为unicode编码
function encodeUnicode(str) 
{  
    var res = [];  
    for ( var i=0; i<str.length; i++ ) 
    {  
      res[i] = ( "00" + str.charCodeAt(i).toString(16) ).slice(-4);  
    }  
    return "\\u" + res.join("\\u");  
}  

var CHIFFRETEXT=encodeUnicode(TESTTEXT);
document.getElementById("Chiffretext").innerHTML=CHIFFRETEXT;

//unicode解码
function decodeUnicode(str) 
{  
    str = str.replace(/\\/g, "%");  
    return unescape(str);  
}  

var KLARTEXT=decodeUnicode(CHIFFRETEXT);
document.getElementById("Klartext").innerHTML=KLARTEXT;

</script>

</body>
</html>
