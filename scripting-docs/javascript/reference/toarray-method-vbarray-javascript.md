---
title: "toArray メソッド (VBArray) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "toArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toArray メソッド"
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# toArray メソッド (VBArray) (JavaScript)
VBArray から変換された標準 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列を返します。  
  
## 構文  
  
```  
  
safeArray.toArray( )  
```  
  
## 解説  
 必要な *safeArray* 参照は VBArray オブジェクトです。  
  
 変換では、多次元 VBArray が 1 つの次元 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列に変換されます。 一連の次元は、それぞれ 1 つ前の次元の最後に追加されます。 たとえば、それぞれに 3 つの要素が含まれる 3 つの次元を持つ VBArray は、次のように [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列に変換されます。  
  
 VBArray に \(1, 2, 3\)、\(4, 5, 6\)、\(7, 8, 9\) が含まれるとします。 変換後の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列には、1、2、3、4、5、6、7、8、9 が含まれます。  
  
 現在、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列を VBArray に変換する方法はありません。  
  
## 使用例  
 次の例は 3 つの部分で構成されます。 最初の部分は、Visual Basic のセーフ配列を作成する VBScript コードです。 2 番目の部分は、Visual Basic セーフ配列を [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列に変換する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードです。 どちらの部分も HTML ページの \<HEAD\> セクションに記述します。 3 番目の部分は、他の 2 つの部分を実行するための [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードで、\<BODY\> セクションに記述します。  
  
```javascript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(j, i) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray)  
{  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [VBArray オブジェクト](../../javascript/reference/vbarray-object-javascript.md)  
  
## 参照  
 [dimensions メソッド \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem メソッド \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound メソッド \(VBArray\)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ubound メソッド \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)