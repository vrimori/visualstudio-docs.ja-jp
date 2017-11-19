---
title: "SCRIPTTHREADSTATE 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE 列挙型
スクリプト エンジンのスレッドの状態を指定します。 この列挙体を使って、 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>列挙値  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|指定したスレッドはされていないサービス、スクリプト化されたイベントをすぐに実行される処理のスクリプトのテキスト、または、スクリプトのマクロを実行します。|  
|SCRIPTTHREADSTATE_RUNNING|指定したスレッドは積極的にサービス、スクリプト化されたイベントをすぐに実行される処理のスクリプトのテキスト、または、スクリプトのマクロを実行します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)