---
title: Idebugdocumenthelper::definescriptblock |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0037df270bc95faaba4d2f04cce65902d08dc6e9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087998"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
ヘルパーに特定の範囲の文字は、指定されたスクリプト エンジンによって処理されるスクリプト ブロックであることを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 [in]スクリプト ブロックの先頭の位置。  
  
 `cChars`  
 [in]スクリプト ブロック内の文字の数。  
  
 `pas`  
 [in]このスクリプト ブロックのスクリプト エンジンです。  
  
 `fScriptlet`  
 [in]スクリプト ブロックがスクリプトレットを示すフラグです。  
  
 `pdwSourceContext`  
 [out]スクリプト ブロックのソース コンテキスト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 スマート ホストは、そのドキュメントには、埋め込みスクリプト ブロックが含まれている場合、このメソッドを使用できます。 言語エンジンは、そのコードには、他の言語の埋め込みスクリプトが含まれている場合、このメソッドを使用できます。  
  
 スクリプト エンジンはすべての構文の色分けやコード コンテキスト参照スクリプト ブロックにします。  
  
 `DefineScriptBlock`テキストを追加した後、メソッドを呼び出す必要があります (を使用するなど、`IDebugDocumentHelper::AddDBCSText`メソッド) スクリプトの前にブロックが解析されましたが、(を使用するなど、`IActiveScriptParse ::ParseScriptText`メソッド)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper::adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)