---
title: IDebugCodeContext2::GetDocumentContext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d506c6c0810d27e7c8ed155724c1edc90f29fe06
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917348"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
このコードのコンテキストに対応するドキュメントのコンテキストを取得します。 ドキュメントのコンテキストでは、この命令を生成したソース コードに対応するソース ファイル内の位置を表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```csharp  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppSrcCxt`  
 [out]返します、 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)コードのコンテキストに対応するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 一般に、ドキュメント コンテキスト見なすことができますのソース ファイル内の位置として、コードのコンテキストはコード命令の実行、ストリーム内の位置。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)