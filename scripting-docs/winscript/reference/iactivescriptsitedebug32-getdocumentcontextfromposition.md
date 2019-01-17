---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9a52abcfa4defb49526f944469c95a2247f5d85c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094485"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
委任に、言語エンジンによって使用される`IDebugCodeContext::GetSourceContext`します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwSourceContext`  
 [in]ソース コンテンツに提供する`ParseScriptText`または`AddScriptlet`します。  
  
 `uCharacterOffset`  
 [in]文字に対してスクリプト ブロックまたはスクリプトレットの開始オフセットします。  
  
 `uNumChars`  
 [in]このコンテキスト内の文字の数。  
  
 `ppsc`  
 [out]この文字位置の範囲に対応するドキュメントのコンテキスト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 言語エンジンでは、このメソッドを使用して、委任`IDebugCodeContext::GetSourceContext`します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteDebug32 インターフェイス](../../winscript/reference/iactivescriptsitedebug32-interface.md)