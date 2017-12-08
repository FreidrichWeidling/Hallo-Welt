# Hallo-Welt
<p>Dies ist mein erstes Repository auf GitHub. Ich hoffe, es kann mir helfen, meine Aufgabe fließend zu beenden.</p>
<!DOCTYPE html>
<html>
<body>

<p id="testtext"></p>
<p id="chiffretext"></p>
<p id="dezimaltext"></p>
<p id="akkumulieren1"></p>
<p id="akkumulieren2"></p>
<p id="zaun"></p>
<p id="hexadezimaltext"></p>
<p id="getrenntebits"></p>
<p id="zeichenfolge"></p>
<p id="zahlenfolgetext"></p>
<p id="klartext"></p>
<p id="derendgultigegeheimtext"></p>
<p id="derendgultigegeheimtext2"></p>
<p id="derendgultigegeheimtext3"></p>

<script>

//变量名称为大写字母，id为与变量名称相对应的小写字母
//TESTTEXT                  测试明文
//CHIFFRETEXT               初级密文
//DEZIMALTEXT               十进制文本
//AKKUMULIEREN1             前累加密文
//AKKUMULIEREN2             后累加密文
//ZAUN                      栅栏加密密文
//HEXADEZIMALTEXT           十六进制文本
//GETRENNTEBITS             分隔位
//ZEICHENFOLGE              字符串
//ZAHLENFOLGETEXT           数字串
//KLARTEXT                  片假名
//DERENDGULTIGEGEHEIMTEXT   最终密文
//DERENDGULTIGEGEHEIMTEXT2  最终密文2
//DERENDGULTIGEGEHEIMTEXT3  最终密文3

//密码表
var PASSWORTTABLLE="ボジオタギデバリミュサザョビエマ";

var TESTTEXT ="我爱你2333！？。I love you. 私はあなたを愛している!";
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
//document.getElementById("chiffretext").innerHTML=CHIFFRETEXT;

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
//document.getElementById("dezimaltext").innerHTML=DEZIMALTEXT;

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
//document.getElementById("akkumulieren1").innerHTML=AKKUMULIEREN1;

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
//document.getElementById("akkumulieren2").innerHTML=AKKUMULIEREN2;

//栅栏加密
function getZaun(str)
{
    var res=[];
    var k=0;
    for(var i=0;i<str.length;i+=2)
    {
        res[k]=str[i];
        k++;
    }
    for(var i=1;i<str.length;i+=2)
    {
        res[k]=str[i];
        k++;
    }
    return res;
}

var ZAUN=getZaun(AKKUMULIEREN2);
//document.getElementById("zaun").innerHTML=ZAUN;

//转为十六进制字符串
function getHexadezimal(str) 
{  
    var res = [];  
    for ( var i=0; i<str.length; i++ ) 
    {  
      res[i] =str[i].toString(16);  
    }  
    return res; 
}

var HEXADEZIMALTEXT=getHexadezimal(ZAUN);
//document.getElementById("hexadezimaltext").innerHTML=HEXADEZIMALTEXT;

//记录分隔位
 var number=0;
function ZeichnenSiedasTrennungsbitauf(str)
{
    var res=[];
    res=str.split("");
    number+=parseInt(res.length);
}
var NUMSTRING=[];
for(var i=0;i<CHIFFRETEXT.length;i++)
{
    ZeichnenSiedasTrennungsbitauf(HEXADEZIMALTEXT[i]);
    NUMSTRING[i]=number;
}
var GETRENNTEBITS=NUMSTRING;

//获取字符串
var res2 = [];
function getZeichenfolge(str) 
{  
    var res1 = [];
    for ( var i=0; i<str.length; i++ ) 
    {  
      res1=HEXADEZIMALTEXT[i].split("");
      res2+=res1;
    }  
    return res2; 
}

var ZEICHENFOLGE=getZeichenfolge(HEXADEZIMALTEXT);
//document.getElementById("zeichenfolge").innerHTML=ZEICHENFOLGE;

//最后一个数字串
function getZahlenfolgetext(str)
{
    ZEICHENFOLGE=str;
    var TT=[];
    var TT1=[];
    for ( var i=0; i<str.length; i++ ) 
        {  
          TT1=str[i].split("");
          if(i!=str.length-1)
          {
            TT+=TT1+",";
          }
          if(i==str.length-1)
            {
                TT+=TT1;
            }
        }
    return TT.replace(/,/g, "");
}

var ZAHLENFOLGETEXT=getZaun(getZahlenfolgetext(ZEICHENFOLGE));
//document.getElementById("zahlenfolgetext").innerHTML=ZAHLENFOLGETEXT;

//最终密文
var KLARTEXT=[];
function getDerendgultigegeheimtext(str)
{
    switch(str)
    {
        case "0":
        {
            KLARTEXT=PASSWORTTABLLE[0];
            break;
        }
        case "1":
        {
            KLARTEXT=PASSWORTTABLLE[1];
            break;
        }
        case "2":
        {
            KLARTEXT=PASSWORTTABLLE[2];
            break;
        }
        case "3":
        {
            KLARTEXT=PASSWORTTABLLE[3];
            break;
        }
        case "4":
        {
            KLARTEXT=PASSWORTTABLLE[4];
            break;
        }
        case "5":
        {
            KLARTEXT=PASSWORTTABLLE[5];
            break;
        }
        case "6":
        {
            KLARTEXT=PASSWORTTABLLE[6];
            break;
        }
        case "7":
        {
            KLARTEXT=PASSWORTTABLLE[7];
            break;
        }
        case "8":
        {
            KLARTEXT=PASSWORTTABLLE[8];
            break;
        }
        case '9':
        {
            KLARTEXT=PASSWORTTABLLE[9];
            break;
        }
        case "a":
        {
            KLARTEXT=PASSWORTTABLLE[10];
            break;
        }
        case "b":
        {
            KLARTEXT=PASSWORTTABLLE[11];
            break;
        }
        case "c":
        {
            KLARTEXT=PASSWORTTABLLE[12];
            break;
        }
        case "d":
        {
            KLARTEXT=PASSWORTTABLLE[13];
            break;
        }
        case "e":
        {
            KLARTEXT=PASSWORTTABLLE[14];
            break;
        }
        case "f":
        {
            KLARTEXT=PASSWORTTABLLE[15];
            break;
        }
    }
    return KLARTEXT;
}

var DERENDGULTIGEGEHEIMTEXT=[];
for(var i=0;i<ZAHLENFOLGETEXT.length;i++)
{
    DERENDGULTIGEGEHEIMTEXT+=getDerendgultigegeheimtext(ZAHLENFOLGETEXT[i]);
}

var DERENDGULTIGEGEHEIMTEXT2=getZaun(DERENDGULTIGEGEHEIMTEXT);
//document.getElementById("derendgultigegeheimtext2").innerHTML=DERENDGULTIGEGEHEIMTEXT2;

var DERENDGULTIGEGEHEIMTEXT3=[];
for(var i=0;i<DERENDGULTIGEGEHEIMTEXT2.length;i++)
{
    
        DERENDGULTIGEGEHEIMTEXT3+=DERENDGULTIGEGEHEIMTEXT2[i].replace(/,/g, "");
}
document.getElementById("derendgultigegeheimtext3").innerHTML="最终密文3："+DERENDGULTIGEGEHEIMTEXT3+GETRENNTEBITS;

</script>

</body>
</html>
