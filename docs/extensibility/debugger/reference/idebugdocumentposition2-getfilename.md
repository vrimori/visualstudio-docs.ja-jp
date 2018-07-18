---
title: IDebugDocumentPosition2::GetFileName |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 81417fbb025fdea70a4b9fb51f0b49fb0257cd8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109104"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
ドキュメントの位置を含むソース ファイルのファイル名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFileName(   
   BSTR* pbstrFileName  
);  
```  
  
```csharp  
int GetFileName(   
   out string pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrFileName`  
 [out]ソース ファイルのファイル名を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ソース ファイルでは、(、ソース ファイルが存在しない、ディスク上など)、ファイル名は常にことはできません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)