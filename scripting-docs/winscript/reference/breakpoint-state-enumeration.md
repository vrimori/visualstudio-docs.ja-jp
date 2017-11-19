---
title: "BREAKPOINT_STATE 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: BREAKPOINT_STATE
apilocation: scrobj.dll
helpviewer_keywords: BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 881598b39625b02651a4d57456904db60ace80c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="breakpointstate-enumeration"></a>BREAKPOINT_STATE 列挙型
ブレークポイントの状態を示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|BREAKPOINT_DELETED|ブレークポイントが存在しませんへの参照がまだあります。|  
|BREAKPOINT_DISABLED|ブレークポイントが存在しますは無効になります。|  
|BREAKPOINT_ENABLED|ブレークポイントが存在しが有効になっています。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)