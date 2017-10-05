---
title: "IDebugDocumentContext2::GetDocument |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::GetDocument
helpviewer_keywords:
- IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
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
ms.openlocfilehash: e2ff6daf8f7eb905553b3bfd9459357247485624
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
このドキュメントのコンテキストを含むドキュメントを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDocument(   
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppDocument`  
 [out]返します、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)をこのドキュメントのコンテキストを含むドキュメントを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、IDE に直接ドキュメントを提供するデバッグ エンジンです。 それ以外の場合、このメソッドが返す`E_NOTIMPL`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
