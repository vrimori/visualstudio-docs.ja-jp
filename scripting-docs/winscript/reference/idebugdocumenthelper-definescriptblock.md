---
title: "IDebugDocumentHelper::DefineScriptBlock |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
ヘルパーに渡し、特定の範囲の文字が、指定されたスクリプト エンジンによって処理されるスクリプト ブロックを示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ulCharOffset`  
 [in]スクリプト ブロックの先頭の場所です。  
  
 `cChars`  
 [in]スクリプト ブロック内の文字の数。  
  
 `pas`  
 [in]このスクリプト ブロックのスクリプト エンジンです。  
  
 `fScriptlet`  
 [in]スクリプト ブロックがスクリプトレットであるかを示すフラグです。  
  
 `pdwSourceContext`  
 [out]スクリプト ブロックのソース コンテキスト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 スマート ホストは、そのドキュメントには、埋め込みのスクリプト ブロックが含まれている場合、このメソッドを使用できます。 言語エンジンは、そのコードには、他の言語の埋め込みのスクリプトが含まれている場合、このメソッドを使用できます。  
  
 スクリプト エンジンは、すべての構文の色分けやコード コンテキスト参照、スクリプト ブロックで行います。  
  
 `DefineScriptBlock`テキストを追加した後、メソッドを呼び出す必要があります (たとえばを使用して、`IDebugDocumentHelper::AddDBCSText`メソッド) スクリプトの前にブロックが解析されましたが、(などを使用して、`IActiveScriptParse ::ParseScriptText`メソッド)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)