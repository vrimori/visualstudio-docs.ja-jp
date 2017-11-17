---
title: "Debug.setNonUserCodeExceptions プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="debugsetnonusercodeexceptions-property"></a>Debug.setNonUserCodeExceptions プロパティ
このスコープ内の、try-catch ブロックが、ユーザーに処理されないと、デバッガーによって処理されるかどうかを判断します。 例外は、スローされた場合、ユーザーに処理されないに従って分類または処理されないことができます。  
  
 このプロパティ設定されている場合`true`、特定のスコープでデバッガーを決定できますに操作 (たとえば、中断) で開発者がユーザーに処理されない例外で中断する場合、そのスコープ内でスローされる例外。 このプロパティ設定されている場合`false`プロパティが設定されていない場合と同じです。  
  
 デバッグの詳細については、次を参照してください。[アクティブ スクリプト デバッグの概要](http://go.microsoft.com/fwlink/p/?LinkId=249469)です。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>例  
 次のコードに、このプロパティを設定する方法を示します。  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]