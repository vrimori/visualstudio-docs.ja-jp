---
title: "toArray メソッド (VBArray) (JavaScript) |Microsoft ドキュメント"
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
- toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="toarray-method-vbarray-javascript"></a>toArray メソッド (VBArray) (JavaScript)
VBArray から変換された標準 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>コメント  
 必要な *safeArray* 参照は VBArray オブジェクトです。  
  
 変換では、多次元 VBArray が 1 つの次元 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列に変換されます。 一連の次元は、それぞれ 1 つ前の次元の最後に追加されます。 たとえば、それぞれに 3 つの要素が含まれる 3 つの次元を持つ VBArray は、次のように [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列に変換されます。  
  
 VBArray に (1, 2, 3)、(4, 5, 6)、(7, 8, 9) が含まれるとします。 変換後の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列には、1、2、3、4、5、6、7、8、9 が含まれます。  
  
 現在、 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列を VBArray に変換する方法はありません。  
  
## <a name="example"></a>例  
 次の例は 3 つの部分で構成されます。 最初の部分は、Visual Basic のセーフ配列を作成する VBScript コードです。 2 番目の部分は、Visual Basic セーフ配列を [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 配列に変換する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] コードです。 両方のパーツが入ります、\<ヘッド > HTML ページのセクションでします。 3 番目の部分、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]コードで、\<本文 > セクションに、その他の 2 つの部分を実行します。  
  
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
  
## <a name="requirements"></a>要件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「 [バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [VBArray Object](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [dimensions メソッド (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem メソッド (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [lbound メソッド (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [ubound メソッド (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)