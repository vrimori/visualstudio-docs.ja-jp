---
title: "VBArray オブジェクト (JavaScript) | Microsoft Docs"
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
  - "VBArray"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "VBArray オブジェクト定数"
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# VBArray オブジェクト (JavaScript)
Visual Basic のセーフ配列にアクセスする手段を提供します。  
  
> [!WARNING]
>  このオブジェクトは Internet Explorer でのみサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされません。  
  
## 構文  
  
```  
  
varName = new VBArray(safeArray)  
```  
  
## パラメーター  
 `varName`  
 必須です。 VBArray を割り当てる変数名。  
  
 *safeArray*  
 必須です。 VBArray 値です。  
  
## 解説  
 VBArrays は読み取り専用で、直接作成することはできません。*safeArray* 引数は、VBArray コンストラクターに渡される前に VBArray 値を取得する必要があります。 この操作は、既存の ActiveX またはその他のオブジェクトから値を取得することによってのみ行うことができます。  
  
 VBArray には複数の次元を指定できます。 各次元のインデックスを個別に指定できます。 配列の次元数は、**dimensions** メソッドにより取得できます。各次元で使用されるインデックスの範囲は、`lbound` メソッドおよび `ubound` メソッドにより取得できます。  
  
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
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
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
  
## プロパティ  
 `VBArray` オブジェクトには、プロパティはありません。  
  
## メソッド  
 [dimensions メソッド](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [getItem メソッド](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [lbound メソッド](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [toArray メソッド](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [ubound メソッド](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
## 参照  
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)