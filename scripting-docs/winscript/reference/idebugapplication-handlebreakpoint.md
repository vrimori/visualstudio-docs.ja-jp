---
title: "IDebugApplication::HandleBreakPoint |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
現在のスレッドをブロックして、デバッガーの IDE に、ブレークポイントの通知を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `br`  
 [in]中断の理由です。  
  
 `pbra`  
 [out]デバッガーは、アプリケーションを再開したときに実行するアクション。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 言語エンジンは、ブレークポイントをヒットするスレッドのコンテキストでこのメソッドを呼び出します。 このメソッドは、現在のスレッドをブロックし、IDE デバッガーにブレークポイント通知を送信します。 デバッガーは、アプリケーションを再開するとき、`pbra`パラメーターが取るべき操作を指定します。  
  
> [!NOTE]
>  言語エンジンは、フレームまたは、ブレークポイント中の式を評価スタックの列挙などのタスクを実行するスレッドから呼び出すことができます。  
  
 このメソッドにより`IApplicationDebugger::onHandleBreakPoint`呼び出せるようにします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)