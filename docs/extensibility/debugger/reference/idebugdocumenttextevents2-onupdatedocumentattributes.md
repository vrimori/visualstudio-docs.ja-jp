---
title: IDebugDocumentTextEvents2::onUpdateDocumentAttributes |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 098698041ab90611e29132a9f9205b7b78238062
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109728"
---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ドキュメントの属性が更新されているイベントの受信側に通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT onUpdateDocumentAttributes(   
   TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
```csharp  
int onUpdateDocumentAttributes(   
   enum_TEXT_DOC_ATTR_2 textdocattr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `textdocattr`  
 [in]フラグの組み合わせ、 [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)ドキュメントの更新された属性を指定する列挙です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)