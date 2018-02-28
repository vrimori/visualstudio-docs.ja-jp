---
title: "ubound メソッド (VBArray) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ubound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ubound method
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfb87cf3fd552c329635a3ca3e974c84a1324bfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ubound-method-vbarray-javascript"></a>ubound メソッド (VBArray) (JavaScript)
VBArray の指定された次元で使用される最も高いインデックス値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
safeArray.ubound(dimension)   
```  
  
## <a name="parameters"></a>パラメーター  
 *safeArray*  
 必須です。 VBArray オブジェクトです。  
  
 `dimension`  
 省略可能です。 上限インデックスを必要とする VBArray の次元です。 省略すると、 `ubound` は 1 が渡された場合のように動作します。  
  
## <a name="remarks"></a>コメント  
 VBArray が空の場合、 `ubound` メソッドは undefined を返します。 `dim` が VBArray の次元数より大きいか、負の場合、このメソッドは "インデックスが有効範囲にありません" というエラーを生成します。  
  
## <a name="example"></a>例  
 次の例は 3 つの部分で構成されます。 最初の部分は、Visual Basic のセーフ配列を作成する VBScript コードです。 2 番目の部分は、セーフ配列の次元数と各次元の上限を決定する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードです。 両方のパーツが入ります、\<ヘッド > HTML ページのセクションでします。 3 番目の部分、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]コードで、\<本文 > セクションに、その他の 2 つの部分を実行します。  
  
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
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
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
  
## <a name="requirements"></a>要件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「 [バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [dimensions メソッド (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem メソッド (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound メソッド (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray メソッド (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)