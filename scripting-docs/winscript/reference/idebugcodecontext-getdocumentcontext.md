---
title: IDebugCodeContext::GetDocumentContext |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::GetDocumentContext
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 098d57a5ff0ba14b1dd493ad772eee595a10ec9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725652"
---
# <a name="idebugcodecontextgetdocumentcontext"></a>IDebugCodeContext::GetDocumentContext
このコードのコンテキストに関連付けられているドキュメントのコンテキストを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppsc`  
 [out]このコードのコンテキストに関連付けられているドキュメントのコンテキスト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 テキスト ドキュメント、文字位置の範囲は、ステートメント全体のテキストを含める必要があります。 これにより、デバッガー IDE を現在のソース ステートメントを強調表示することができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCodeContext インターフェイス](../../winscript/reference/idebugcodecontext-interface.md)