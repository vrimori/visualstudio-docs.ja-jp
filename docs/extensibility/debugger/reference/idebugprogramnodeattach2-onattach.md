---
title: IDebugProgramNodeAttach2::OnAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9abab3122921619ba14400bb14039fac139a159f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933803"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
関連付けられているプログラムにアタッチするか、アタッチ プロセスの遅延、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidProgramId`  
 [in]`GUID`に関連付けられているプログラムを割り当てます。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドを呼び出すことはできません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを呼び出すアタッチ中に、前に、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドが呼び出されます。 `OnAttach`メソッド、attach プロセス自体を実行できます (この場合は、このメソッドを返します`S_FALSE`) にアタッチ プロセスを延期または、`IDebugEngine2::Attach`メソッド (、`OnAttach`メソッドを返します。 `S_OK`)。 いずれの場合、`OnAttach`メソッドを設定できます、`GUID`をデバッグ中のプログラムの指定された`GUID`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)