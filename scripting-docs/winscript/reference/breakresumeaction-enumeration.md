---
title: BREAKRESUMEACTION 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3186ac39353d11f327f7940ae5fc03ae2238ddd9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090469"
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION 列挙型
ブレークポイントから継続する方法について説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|アプリケーションを中止します。|  
|BREAKRESUMEACTION_CONTINUE|実行が継続します。|  
|BREAKRESUMEACTION_STEP_INTO|プロシージャにステップ インします。|  
|BREAKRESUMEACTION_STEP_OVER|プロシージャをステップ オーバーします。|  
|BREAKRESUMEACTION_STEP_OUT|現在のプロシージャからステップ アウトします。|  
|BREAKRESUMEACTION_IGNORE|現在の状態での実行を継続します。|  
|BREAKRESUMEACTION_STEP_DOCUMENT|次のドキュメントに移動します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)