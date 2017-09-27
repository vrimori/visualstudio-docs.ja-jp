---
title: "IDebugProgramNodeAttach2::OnAttach |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e0162d17fc81b1304213d0259863f35523a833f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
関連付けられているプログラムにアタッチするか、attach プロセスには、ゆだねます、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドです。  
  
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
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドを呼び出すことはできません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、attach プロセス中に前に、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドが呼び出されます。 `OnAttach`メソッド自体、attach プロセスを実行できます (このメソッドが戻る場合は、 `S_FALSE`) に、attach プロセスを延期または、`IDebugEngine2::Attach`メソッド (、`OnAttach`メソッドを返します。 `S_OK`)。 いずれの場合、`OnAttach`メソッドを設定できます、`GUID`をデバッグするプログラムの指定された`GUID`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)
