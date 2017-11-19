---
title: "Ijsdebugdatatarget::getthreadcontext メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e2f858c66eda2ad09b04d7beab776c793b6f195
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext メソッド
指定したスレッドのコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `threadId`  
 [入力] ターゲット プロセスで実行中のスレッド。  
  
 `contextFlags`  
 [入力] コンテキスト フラグを指定します。 これは CONTEXT の ContextFlags フィールドと同じです (詳細については「winnt.h」で「CONTEXT_ALL」を参照)。  
  
 `contextSize`  
 [入力] pContext で指定したバッファーのサイズ。  
  
 `pContext`  
 [出力] pContext で指定したバッファーでプラットフォーム固有の CONTEXT 構造体を受け取ります。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)