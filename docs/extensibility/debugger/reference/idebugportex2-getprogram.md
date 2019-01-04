---
title: IDebugPortEx2::GetProgram |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::GetProgram
helpviewer_keywords:
- IDebugPortEx2::GetProgram
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 96303d8b98a573da1aa2f022d0fb66eda488ef00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951788"
---
# <a name="idebugportex2getprogram"></a>IDebugPortEx2::GetProgram
プログラム ノードに関連付けられているプログラムを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProgram(   
   IDebugProgramNode2* pProgramNode,  
   IDebugProgram2**    ppProgram  
);  
```  
  
```csharp  
int GetProgram(   
   IDebugProgramNode2 pProgramNode,  
   out IDebugProgram2 ppProgram  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProgramNode`  
 [in][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)プログラム ノードを表すオブジェクト。  
  
 `ppProgram`  
 [out]返します、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)プログラム ノードに関連付けられているプログラムを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)