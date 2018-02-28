---
title: "IDebugApplicationThread::SynchronousCallIntoThread |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
呼び出し元アプリケーションのスレッドでコードを実行するためのメカニズムを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstcb`  
 [in]呼び出すオブジェクト。  
  
 `dwParam1`  
 [in]最初のパラメーターに渡す、`IDebugThreadCall::ThreadCallHandler`メソッドです。  
  
 `dwParam2`  
 [in]2 番目のパラメーターに渡す、`IDebugThreadCall::ThreadCallHandler`メソッドです。  
  
 `dwParam3`  
 [in]3 番目のパラメーターに渡す、`IDebugThreadCall::ThreadCallHandler`メソッドです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、デバッガー スレッドでコードを実行する呼び出し元のメカニズムを提供します。 言語エンジンとホストは通常、1 つのスレッドの実装の上にフリー スレッド オブジェクトを実装するのにこのメソッドを使用します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplicationThread インターフェイス](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall インターフェイス](../../winscript/reference/idebugthreadcall-interface.md)