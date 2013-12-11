<style type="text/css">
#CICodeFormatterTable td select{font-size:10px;font-weight:normal}
#CICodeFormatterTable td{font-size:10px;font-weight:normal}
#CICodeFormatter.pre{padding:0px;margin:0px;font-weight:normal;overflow:auto}
</style>
<table id="CICodeFormatterTable" cellspacing="2" cellpadding="4" border="0" style="font-size:11px;font-family:verdana;width:99%;">
<tbody>
<tr>
<td style="background:#D3E1EF;color:black;font-family:verdana;font-weight:bolder;border-bottom:1px solid blue;">Paste Here Your Source Code</td>
</tr>
<tr>
<td style="background:#f0f0f0;">
<textarea id="txtSourceCode" style="width:100%;;height:120px;font-family:arial;font-size:10px;"></textarea>
</td>
</tr>
<tr>
<td style="background:#D3E1EF;color:black;font-family:verdana;font-weight:bolder;border-bottom:1px solid blue;">Source Code Formatting Options</td>
</tr>
<tr>
<td style="background:#f0f0f0;color:black;font-family:verdana;font-weight:bolder;border-bottom:0px solid blue;">
<table width="100%" cellspacing="1" cellpadding="2" style="font-size:11px;font-family:verdana;background:white">
<tbody>
<tr>
<td width="250" style="background:#f0f0f0"> 1) Convert Tab into Space : </td>
<td style="background:#f0f0f0">
<select id="cbTabSize">
<option value="1" />1 
<option value="2" />2 
<option value="3" />3 
<option value="4" />4 
<option value="5" selected />5 
<option value="6" />6 
<option value="7" />7 
<option value="8" />8 
<option value="9" />9 
<option value="10" />10
</select>
</td>
</tr>
<tr>
<td style="background:#f0f0f0"> 2) Need Line Code Numbering : </td>
<td style="background:#f0f0f0">
<select id="cbLineNumbering">
<option value="true" />Yes 
<option value="false" selected />No
</select>
</td>
</tr>
<tr>
<td style="background:#f0f0f0"> 3) Remove blank lines : </td>
<td style="background:#f0f0f0">
<select id="cbRemoveBlankLines">
<option value="true" selected />Yes 
<option value="false" />No
</select>
</td>
</tr>
<tr>
<td style="background:#f0f0f0"> 4) Embeded styles / Stylesheet : </td>
<td style="background:#f0f0f0">
<select id="cbEmbededStylesheet">
<option value="true" selected />Yes 
<option value="false" />No
</select>
</td>
</tr>
<tr>
<td width="250" style="background:#f0f0f0"> 5) Code Block Width : </td>
<td style="background:#f0f0f0">
<select id="cbCodeDivWidth" disabled="">
<option value="auto" />auto width 
<option value="99%" selected />100% 
<option value="100px" />100px 
<option value="150px" />150px 
<option value="200px" />200px 
<option value="250px" />250px 
<option value="300px" />300px 
<option value="350px" />350px 
<option value="400px" />400px 
<option value="450px" />450px 
<option value="500px" />500px 
<option value="550px" />550px 
<option value="600px" />600px 
<option value="650px" />650px 
<option value="700px" />700px 
<option value="750px" />750px 
<option value="800px" />800px 
<option value="850px" />850px 
<option value="900px" />900px 
<option value="950px" />950px 
<option value="1000px" />1000px 
</select>
</td>
</tr>
<tr>
<td width="250" style="background:#f0f0f0"> 6) Code Block Height : </td>
<td style="background:#f0f0f0">
<select id="cbCodeDivHeight">
<option value="auto" selected />auto height 
<option value="100%" />100% 
<option value="100px" />100px 
<option value="150px" />150px 
<option value="200px" />200px 
<option value="250px" />250px 
<option value="300px" />300px 
<option value="350px" />350px 
<option value="400px" />400px 
<option value="450px" />450px 
<option value="500px" />500px 
<option value="550px" />550px 
<option value="600px" />600px 
<option value="650px" />650px 
<option value="700px" />700px 
<option value="750px" />750px 
<option value="800px" />800px 
<option value="850px" />850px 
<option value="900px" />900px 
<option value="950px" />950px 
<option value="1000px" />1000px 
</select>
</td>
</tr>
<tr>
<td width="250" style="background:#f0f0f0"> 7) Alternative Background : </td>
<td style="background:#f0f0f0">
<select id="cbAlternativeBackground">
<option value="true" selected />Yes 
<option value="false" />No
</select>
</td>
</tr>
</tbody>
</table>
</td>
</tr>
<tr>
<td align="right">
<input type="button" onclick="showFormattedCode()" value="Format Source Code" />
</td>
</tr>
<tr>
<td style="background:#D3E1EF;color:black;font-family:verdana;font-weight:bolder;border-bottom:1px solid blue;">Copy Formatted Source Code</td>
</tr>
<tr>
<td style="background:#f0f0f0;">
<textarea id="txtSourceCodeFormat" style="width:100%;;height:120px;font-family:arial;font-size:10px;"></textarea>
</td>
</tr>
<tr>
<td align="right">   </td>
</tr>
<tr>
<td style="background:#D3E1EF;color:black;font-family:verdana;font-weight:bolder;border-bottom:1px solid blue;">Preview Of Formatted Code</td>
</tr>
</tbody>
</table>
<div id="divSourceCodeOutPut" style="padding:0px;width:99%;height:100%"> </div>
<script type="text/javascript" language="javascript">
/********************************************************************************************************
* Date : 31/5/2009
* Development : http://ithelpdeskgroup.blogspot.com
* Author : Ad
********************************************************************************************************/
var sourceCodeTextareaObj = "";
var sourceCodeFormattedTextareaObj = "";
var sourceCodeOutputDivObj = "";
var tabSize = "5";
var language="";
var lineNumbering = true;
var removeBlankLines = true;
var embededStylesheet = true;
var tag=true;
var blockWidth="100%";
var blockHeight="auto";
var alternativeBackground = true;
function CICodeFormatter(sourceCodeTextareaObj,sourceCodeFormattedTextareaObj,sourceCodeOutputDivObj){
this.sourceCodeTextareaObj = document.getElementById(sourceCodeTextareaObj);
this.sourceCodeFormattedTextareaObj = document.getElementById(sourceCodeFormattedTextareaObj);
this.sourceCodeOutputDivObj=document.getElementById(sourceCodeOutputDivObj);
}
CICodeFormatter.prototype.formatSourceCode=function(lang,tag,tabSize,lineNumbering,removeBlankLines,embededStylesheet,blockWidth,blockHeight,alternativeBackground){
this.language = lang;
this.tag = tag;
this.tabSize = tabSize;
this.lineNumbering = lineNumbering;
this.removeBlankLines = removeBlankLines;
this.embededStylesheet = embededStylesheet;
this.blockWidth = blockWidth;
this.blockHeight = blockHeight;
this.alternativeBackground = alternativeBackground;
switch(language){
case "PHP":
break;
default:
this.formatAnyCode();
break;
}
}
CICodeFormatter.prototype.getSourceCode = function(){
var sc = this.sourceCodeTextareaObj.value;
sc = this.escapeEntities(sc);
return sc;
}
CICodeFormatter.prototype.escapeEntities = function(str){
var sc = str;
var space = "";
for(var i=0;i<this.tabSize;i++){
if(this.tag=="true")
space+="&nbsp;";
else
space+=" ";
}
sc = sc.replace(/ /g," ");
sc = sc.replace(/&/g,"&amp;");
sc = sc.replace(/</g,"&lt;");
sc = sc.replace(/>/g,"&gt;");
sc = sc.replace(/\t/g,space);
return sc;
}
CICodeFormatter.prototype.trim=function(str){
return str.replace(/^\s+|\s+$/g,"");
}
CICodeFormatter.prototype.rightTrim=function(str){
return str.replace(/^\s+$/,"");
}
CICodeFormatter.prototype.formatAnyCode = function(){
var sourceCode = this.getSourceCode();
var fc="";
var counter=0;
var lines = sourceCode.split('\n');
var bg = "#f0f0f0";
var mxChars = "0";
var lineNumber = "";
var tmp="";
var lineStyle = "";
var codeStyle = "";
var parentStyle = "";
var styleSheet = "";
for(var i=0;i<lines.length;i++){
bg = (counter % 2 == 0 )?"#f0f0f0":"#ffffff";
tmp = (this.removeBlankLines=="true")?lines[i].replace(/&nbsp;/g,"").replace(/ /g,""):lines[i];
if(this.trim(tmp)!="" || this.removeBlankLines=="false"){
counter++;
if(this.embededStylesheet == "true"){
lineStyle = 'style="width:30px;color:gray;"';
//codeStyle = 'style="white-space : nowrap;width:auto;background:'+bg+';"';
}
if(this.lineNumbering == "true") lineNumber='<span '+lineStyle+'>'+(counter)+' :&nbsp;&nbsp;</span>';
if(this.tag=="true"){
fc+= '<div class="CICodeLine'+(counter % 2)+'" '+codeStyle+'>'+lineNumber+''+lines[i]+"</div>";
}else{
if(this.lineNumbering == "true"){
var space ="";
fc+=(counter)+': '+lines[i]+' \n';
}else{
fc+=" "+lines[i]+" \n";
}
}
}
}
//genratting formatted source code..
if(this.embededStylesheet == "true"){
//parentStyle='style="font-family:arial;font-size:12px;border:1px dashed #CCCCCC;width:'+this.blockWidth+';height:'+this.blockHeight+';overflow:auto;background:#f0f0f0;"';
parentStyle='style="font-family:arial;font-size:12px;border:1px dashed #CCCCCC;width:'+this.blockWidth+';height:'+this.blockHeight+';overflow:auto;background:#f0f0f0;'+((this.tag=="false" && this.alternativeBackground=="true")?";background-image:URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif);":"")+'padding:0px;color:#000000;text-align:left;line-height:20px;"';
}else{
styleSheet = this.getStyleSheet();
}
if(this.tag=="true"){
fc = '<b style="font-family:verdana;font-size:10px;">CODE:</b><br><div style="white-space : nowrap;"><div class="CICodeFormatter" '+parentStyle+'>'+fc+'</div></div>';
}else{
//fc = '<div style="font-family:verdana;font-size:10px;font-weight:bolder;text-align:left;width:100%;">CODE:</div><pre class="CICodeFormatter" '+parentStyle+'><code>'+fc+'</code></pre>';
fc = '<pre '+((this.embededStylesheet == "false")?"class=\"CICodeFormatter\"":"")+' '+parentStyle+'><code '+((this.embededStylesheet == "false")?"class=\"CICodeFormatter\"":"style=\"color:#000000;word-wrap:normal;\"")+'>'+fc+'</code></pre>';
//fc = '<pre '+((this.embededStylesheet == "false")?"class=\"CICodeFormatter\"":"")+' '+parentStyle+'>'+fc+'</pre>';
}
this.sourceCodeFormattedTextareaObj.value=styleSheet+fc;
this.sourceCodeOutputDivObj.innerHTML = styleSheet+fc;
}
CICodeFormatter.prototype.getStyleSheet = function(){
var style = "";
style = "<style type=\"text/css\">\n";
style +="pre.CICodeFormatter{\n\tfont-family:arial;\n\tfont-size:12px;\n\tborder:1px dashed #CCCCCC;\n\twidth:"+this.blockWidth+";\n\theight:"+this.blockHeight+";\n\toverflow:auto;\n\tbackground:#f0f0f0;\n\tline-height:20px;\n\t"+((this.tag=="false" && this.alternativeBackground=="true")?"background-image:URL(http://2.bp.blogspot.com/_z5ltvMQPaa8/SjJXr_U2YBI/AAAAAAAAAAM/46OqEP32CJ8/s320/codebg.gif);":"")+"\n\tpadding:0px;\n\tcolor:#000000;\n\ttext-align:left;\n}\n";
style +="pre.CICodeFormatter code{\n\tcolor:#000000;\n\tword-wrap:normal;\n}\n";
if(this.tag=="true"){
style +="div.CICodeFormatter span{\n\twidth:30px;\n\tcolor:gray;\n}\n";
style +="div.CICodeFormatter div.CICodeLine1,div.CICodeLine0{\n\twidth:150em;\n\theight:20px;\n\tbackground:#f0f0f0;\n\twhite-space : nowrap;\n}\n";
style +="div.CICodeFormatter div.CICodeLine0{\n\tbackground:#ffffff;\n}\n";
}
style +="</style>\n";
return style;
}
</script>
<script language="Javascript">
var cf = new CICodeFormatter("txtSourceCode","txtSourceCodeFormat","divSourceCodeOutPut");
/*function showFormattedCode(){
cf.formatSourceCode('',
document.getElementById('cbDiv').value,
document.getElementById('cbTabSize').value,
document.getElementById('cbLineNumbering').value,
document.getElementById('cbRemoveBlankLines').value,
document.getElementById('cbEmbededStylesheet').value,
document.getElementById('cbCodeDivWidth').value,
document.getElementById('cbCodeDivHeight').value);
}*/
function showFormattedCode(){
cf.formatSourceCode('',
"false",
document.getElementById('cbTabSize').value,
document.getElementById('cbLineNumbering').value,
document.getElementById('cbRemoveBlankLines').value,
document.getElementById('cbEmbededStylesheet').value,
document.getElementById('cbCodeDivWidth').value,
document.getElementById('cbCodeDivHeight').value,
document.getElementById('cbAlternativeBackground').value);
}
</script>
