---
title: "getItem メソッド (VBArray) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>getItem メソッド (VBArray) (JavaScript)
指定した位置にある項目を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>パラメーター  
 *safeArray*  
 必須です。 VBArray オブジェクトです。  
  
 *dimension1, ..., dimensionN*  
 VBArray の目的の要素の正確な位置を指定します。 *n* は、VBArray の次元数です。  
  
## <a name="example"></a>例  
 次の例は 3 つの部分で構成されます。 最初の部分は、Visual Basic のセーフ配列を作成する VBScript コードです。 2 番目の部分は、Visual Basic のセーフ配列に対して反復処理を行い、各要素の内容を出力する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードです。 両方のパーツが入ります、\<ヘッド > HTML ページのセクションでします。 3 番目の部分、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]コードで、\<本文 > セクションに、その他の 2 つの部分を実行します。  
  
```JavaScript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(i, j) = k  
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
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>要件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「 [バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [dimensions メソッド (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [lbound メソッド (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray メソッド (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [ubound メソッド (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)