---
title: IDebugDocumentPosition2::GetDocument |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2::GetDocument
helpviewer_keywords:
- IDebugDocumentPosition2::GetDocument
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f19edfc978d0e0750aae9242cd0f61b276277ca0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806894"
---
# <a name="idebugdocumentposition2getdocument"></a>IDebugDocumentPosition2::GetDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

コンテナーのドキュメントを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDoc  
);  
```  
  
```csharp  
int GetDocument(   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppDoc`  
 [out]返します、 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)この位置を含むドキュメントを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

