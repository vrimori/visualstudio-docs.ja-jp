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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0614509685436f46a2f48eb8b6a6299321f84901
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
特定のコードのコンテキストのコードの場所の識別子を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_CODE_CONTEXT_OUT_OF_SCOPE`コードのコンテキストが有効な場合は、スコープ外です。  
  
## <a name="remarks"></a>コメント  
 コードの場所 id では、逆アセンブルをサポートするデバッグ エンジン (DE) に固有です。 この場所 id では、デによってコード内の位置を追跡するために使用されは、通常、アドレスまたは何らかのオフセット。 唯一の要件は 1 つの場所のコードのコンテキストが、別の場所のコードのコンテキストよりも小さい場合は最初のコードのコンテキストの対応するコードの場所 id でもなければ、2 つ目のコードのコンテキストのコードの場所 id よりも小さい必要があります。  
  
 コードの場所の識別子のコードのコンテキストを取得する、 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
