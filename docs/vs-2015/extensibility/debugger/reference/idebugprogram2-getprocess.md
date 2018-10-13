---
title: IDebugProgram2::GetProcess |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a272e809edcdb564aedc386448338d6d2426e68f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222353"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このプログラムがで実行されているプロセスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppProcess`  
 [out]返します、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)プロセスを表すインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 デバッグ エンジン (DE) を実装しない限り、 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)インターフェイスでは、このメソッドの既定の実装を常に返します`E_NOTIMPL`とでが実行されているプロセスのことはできません、DE が判断できないためですこのメソッドの実装を満たします。  
  
 実装する、`IDebugEngineLaunch2`インターフェイスは、DE がプロセスを作成する方法を知る必要がありますを意味のため、DE の実装、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイスがで実行されているどのようなプロセスを把握できます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

