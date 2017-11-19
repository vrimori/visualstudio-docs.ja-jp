---
title: "SCRIPTTHREADID 定数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID 定数
スレッドの種類を指定するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>定数  
  
|定数|値|説明|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|現在実行中のスレッド。|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|基本スレッドです。つまりをスクリプト エンジンのスレッドがインスタンス化されます。|  
|SCRIPTTHREADID_ALL|0 xffffffff|すべてのスレッド。|  
  
## <a name="remarks"></a>コメント  
 `SCRIPTTHREADID`によって型が使用される`IActiveScript::GetCurrentScriptThreadID`、 `IActiveScript::GetScriptThreadID`、 `IActiveScript::GetScriptThreadState`、および`IActiveScript::InterruptScriptThread`、定数でのみ使用できますが、`IActiveScript::GetScriptThreadState`と`IActiveScript::InterruptScriptThread`です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)