---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25ce03a124f246443afd0f5a8540a93e7d474f9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
デリゲートを言語エンジンで使用される`IDebugCodeContext::GetSourceContext`です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwSourceContext`  
 [in]ソース コンテンツに提供される`ParseScriptText`または`AddScriptlet`です。  
  
 `uCharacterOffset`  
 [in]文字に対して、スクリプト ブロックまたはスクリプトレットの開始オフセットします。  
  
 `uNumChars`  
 [in]このコンテキストでの文字数。  
  
 `ppsc`  
 [out]この文字位置の範囲に対応するドキュメントのコンテキスト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 言語エンジンでは、このメソッドを使用して、委任`IDebugCodeContext::GetSourceContext`です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSiteDebug インターフェイス](../../winscript/reference/iactivescriptsitedebug-interface.md)