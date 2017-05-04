---
title: "lbound メソッド (VBArray) (JavaScript) | Microsoft Docs"
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
  - "lbound"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lbound メソッド"
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# lbound メソッド (VBArray) (JavaScript)
VBArray オブジェクトの配列で、指定した次元で使用されている最小のインデックス値を返します。  
  
## 構文  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## Parameters  
 *safeArray*  
 Required.  VBArray オブジェクトを指定します。  
  
 `dimension`  
 Optional.  VBArray の、最も小さいインデックスを取得する次元を指定します。  省略した場合、`lbound` は 1 を仮定します。  
  
## 解説  
 VBArray が空の場合、`lbound` メソッドは undefined を返します。  引数 `dimension` に VBArray の次元数より大きい値を指定したり、負の値を指定したりすると、"有効範囲外のインデックス" エラーが発生します。  
  
## 使用例  
 次のコードは、3 つの部分から構成されます。  最初の部分は、Visual Basic のセーフ配列を作成する VBScript のコードです。  2 番目の部分は、このセーフ配列の次元数と各次元の下限値を取得する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のコードです。  セーフ配列は、Visual Basic というよりもむしろ VBScript で作成されるため、下限値は常に 0 になります。  どちらのコードも、HTML ページの \<HEAD\> セクションに記述します。  3 番目の部分は、他の 2 つのコードを実行するために \<BODY\> セクションに記述する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のコードです。  
  
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
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、および Internet Explorer 10 標準の各ドキュメント モードでサポートされます。  [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **対象**: [VBArray オブジェクト](../../javascript/reference/vbarray-object-javascript.md)  
  
## 参照  
 [dimensions メソッド \(VBArray\)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem メソッド \(VBArray\)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [toArray メソッド \(VBArray\)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound メソッド \(VBArray\)](../../javascript/reference/ubound-method-vbarray-javascript.md)