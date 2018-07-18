---
title: IDebugDocumentContext::EnumCodeContexts |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.EnumCodeContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 300102d75fcfa797e8e073b9a1ce77cc5ee2827a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725872"
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
このドキュメントのコンテキストに関連付けられているコードのコンテキストを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppescc`  
 [out]このドキュメントのコンテキストに関連付けられているコード コンテキストです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 ドキュメントは、インクルード ファイルまたはテンプレートにドキュメントがない限り、通常 1 つだけのコードのコンテキストに関連付けられてます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentContext インターフェイス](../../winscript/reference/idebugdocumentcontext-interface.md)