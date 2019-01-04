---
title: IDebugProgram2::Terminate |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4ef57e3cbc11eb6e1b8e266d1a0799ef46ba406
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872097"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
プログラムを終了します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 可能であれば、プログラムは終了し、プロセスからアンロードそれ以外の場合、デバッグ エンジン (DE) は、必要なクリーンアップを実行します。  
  
 このメソッドまたは[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)メソッドはすべてのデバッグを停止するユーザーへの応答では通常、IDE によって呼び出されます。 このメソッドの実装では、プロセス内でプログラムを終了する必要があります、理想的には、します。 それができない場合、DE する必要がありますプログラムがこのプロセスではこれ以上実行されないように (および必要なクリーンアップを行います)。 場合、`IDebugProcess2::Terminate`メソッドは、IDE によって呼び出された、プロセス全体は終了されてからしばらく、`IDebugProgram2::Terminate`メソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)