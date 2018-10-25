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
ms.openlocfilehash: 496b742bc63beec2ba7c50ab5cc8dff88b47bc65
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871213"
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

