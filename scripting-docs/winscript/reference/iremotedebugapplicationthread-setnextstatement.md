---
title: "IRemoteDebugApplicationThread::SetNextStatement |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb23fa643f9a2333e17239a74d0da2f75e1ea791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
強制的に実行の実行を指定したフレームのコンテキストで、指定したコードのコンテキストにできるだけ近い続行します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStackFrame`  
 [in]スタック フレーム オブジェクト。 この引数には、NULL の場合、現在のスタック フレームを使用する必要がありますを意味する可能性があります。  
  
 `pCodeContext`  
 [in]コードのコンテキスト。 この引数には、NULL の場合、現在、コードのコンテキストを使用する必要がありますを意味する可能性があります。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、実行を継続によって指定されたコードのコンテキストにできるだけ近い`pCodeContext`で指定されたフレームのコンテキストで`pStackFrame`です。 これらの引数のいずれかの可能性があります`NULL`、現在のフレームまたはコンテキストを表します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)