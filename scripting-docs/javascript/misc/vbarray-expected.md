---
title: VBArray が必要です |Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4b5416c6e37e59a60206bd21606b5214f05a269
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347464"
---
# <a name="vbarray-expected"></a>VBArray が必要です。
必要ですが、Visual Basic の safeArray、されていないオブジェクトを指定しています。  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays は読み取り専用で、直接作成することはできません。 SafeArray の引数は、VBArray 値でありに渡される前に VBArray 値を取得する必要がありますが、`VBArray`コンス トラクター。 この操作は、既存の ActiveX またはその他のオブジェクトから値を取得することによってのみ行うことができます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを渡すこと**VBArray**オブジェクトを**VBArray**コンス トラクター。  
  
## <a name="see-also"></a>関連項目  
 [VBArray オブジェクト](../../javascript/reference/vbarray-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)