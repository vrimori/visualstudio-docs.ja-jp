---
title: SCRIPTTHREADSTATE 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c66d078effd510b3f64cf1f443926984ff2e282
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347672"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE 列挙型
スクリプト エンジンでは、スレッドの状態を指定します。 この列挙体を使って、 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>列挙値  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|指定されたスレッドはされていない処理がすぐに実行されるスクリプトのテキストをスクリプト化されたイベントを処理または、スクリプト マクロを実行します。|  
|SCRIPTTHREADSTATE_RUNNING|指定されたスレッドはアクティブに処理がすぐに実行されるスクリプトのテキストをスクリプト化されたイベントを処理か、スクリプトのマクロを実行します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)