---
title: "IDebugDisassemblyStream2::GetCodeLocationId |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b64ad6cc146c2e2457cf9c39d5ce2c5d8f78cf65
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
特定のコードのコンテキストのコードの場所の識別子を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```c#  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)識別子に変換するオブジェクト。  
  
 `puCodeLocationId`  
 [out]コードの場所の識別子を返します。 「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す`S_OK`。 そうしないと、エラー コードを返します。 返します。`E_CODE_CONTEXT_OUT_OF_SCOPE`コードのコンテキストが有効な場合は、範囲外です。  
  
## <a name="remarks"></a>コメント  
 コードの場所 id は、逆アセンブルをサポートするデバッグ エンジン (DE) に固有です。 この場所識別子は、DE、コード内の位置を追跡するために使用し、アドレスまたはある種のオフセットは、通常します。 唯一の要件を&1; つの場所のコードのコンテキストが別の場所のコードのコンテキストより小さい最初のコードのコンテキストの対応するコードの場所 id でもある&2; つ目のコードのコンテキストのコードの場所 id よりも小さい必要があります。  
  
 コードの場所の識別子のコードのコンテキストを取得する、 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
