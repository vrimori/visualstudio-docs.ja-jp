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
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844147"
---
# <a name="vbarray-expected"></a>VBArray が必要です。
必要ですが、Visual Basic の safeArray、されていないオブジェクトを指定しています。  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays は読み取り専用で、直接作成することはできません。 SafeArray の引数は、VBArray 値でありに渡される前に VBArray 値を取得する必要がありますが、`VBArray`コンス トラクター。 この操作は、既存の ActiveX またはその他のオブジェクトから値を取得することによってのみ行うことができます。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   のみを渡すこと**VBArray**オブジェクトを**VBArray**コンス トラクター。  
  
## <a name="see-also"></a>関連項目  
 [VBArray オブジェクト](../../javascript/reference/vbarray-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)