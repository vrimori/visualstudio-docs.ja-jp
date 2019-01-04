---
title: IDebugDocument2::GetDocumentClassID |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69c9b5d351f3989bf7a9855274634ededa52f08a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825725"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
ドキュメントのクラス識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```csharp  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pclsid`  
 [out]ドキュメントのクラス ID を示す GUID を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ドキュメントを表す個々 のクラスをインスタンス化するクラスの GUID を使用できます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)