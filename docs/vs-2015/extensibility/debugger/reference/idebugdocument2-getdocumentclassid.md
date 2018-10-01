---
title: IDebugDocument2::GetDocumentClassID |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b744e9fa21bf7ead25df4099411c7f2bf4ccebaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537835"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugDocument2::GetDocumentClassID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocument2-getdocumentclassid)します。  
  
ドキュメントのクラス識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

