---
title: 同じソース行の式で throw を後に |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7179a22d2713c9ddc894618bd6921f3f873f2ad8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345423"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw ステートメントに指定する式は、ソース コードの同一行に記述してください
使用した、`throw`キーワードが従っていなかった、式が同じソース行にします。 A`throw`ステートメントは、2 つの部分で構成されています。`throw`キーワードの後に、式がスローされます。 例:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 これら 2 つのコンポーネントを分割することはできません。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   必ず、`throw`キーワードとがスローされる式が同じ行に表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)   
 [Throw ステートメント](../../javascript/reference/throw-statement-javascript.md)   
 [try… catch… finally ステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)