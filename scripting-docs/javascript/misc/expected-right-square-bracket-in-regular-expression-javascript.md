---
title: "必要です (& m); #39]&#39;です。正規表現 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>必要です (& m); #39]&#39;です。正規表現 (JavaScript)
正規表現の一致の文字クラスを作成しようとしていますが、右角かっこが含まれていません。 角かっこ内に配置して、文字クラスに個々 のリテラル文字の組み合わせをアセンブルすることができます。 クラスは、文字が含まれている任意の 1 文字に一致します。 たとえば、/[abc]/"a"、"b"、文字のいずれかと一致するまたは"c"です。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   正規表現に右角かっこを追加します。  
  
    > [!NOTE]
    >  単一の角かっこに一致する場合は、円記号のエスケープ\\[で特殊文字として解釈されないので[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]です。  
  
## <a name="see-also"></a>関連項目  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [正規表現の構文 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)