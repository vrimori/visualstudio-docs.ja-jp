---
title: DEBUG_TEXT 定数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641062"
---
# <a name="debugtext-constants"></a>DEBUG_TEXT 定数
時に使用される[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>定数  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|テキストがステートメントではなく式であることを示します。 このフラグは、一部の言語によるテキストの解析方法に影響する場合があります。|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|戻り値が使用できる場合、その値は呼び出し元によって使用されます。|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|副作用を許可しません。 このフラグが設定されている場合は、ランタイム状態が式の評価によって変更されることはありません。|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|テキスト評価中のブレークポイントを許可します。 このフラグが設定されていない場合は、テキストの評価中、ブレークポイントが無視されます。|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|テキスト評価中のエラー レポートを許可します。 このフラグが設定されていない場合は、評価中、エラーがホストにレポートされません。|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|式がコード コンテキストに評価されることを示します。式自体は実行されません。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)