---
title: BREAKRESUMEACTION 列挙型 |Microsoft ドキュメント
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
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641222"
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION 列挙型
ブレークポイントから継続する方法について説明します。  
  
## <a name="syntax"></a>構文  
  
```  
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