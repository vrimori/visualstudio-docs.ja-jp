---
title: IActiveScriptDebug::GetScriptTextAttributes |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01218ba46de39dd8351ad82068ca4b34b52b0d46
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097389"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
スクリプトのテキストの任意のブロックのテキスト属性を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrCode`  
 [in]スクリプト ブロックのテキスト。 この文字列は、いない null 終端である必要があります。  
  
 `uNumCodeChars`  
 [in]スクリプト ブロックのテキストの文字の数。  
  
 `pstrDelimiter`  
 [in]最後のスクリプト ブロックの区切り記号のアドレス。 ときに`pstrCode`解析は、テキストのストリームからホスト通常などの使用、区切り記号、2 つの単一引用符 (")、スクリプト ブロックの終わりを検出します。 このパラメーターには、ホストが使用する区切り文字を指定します。それにより、スクリプト エンジンで何らかの条件付きのプリミティブな前処理が可能になります (単一引用符 (') を区切り文字として使用するために 2 つの単一引用符に置き換えるなど)。 正確に把握 (および場合は) この情報は、スクリプト エンジンによって異なります、スクリプト エンジンが使用されます。 ホストは、スクリプト ブロックの終わりをマークする、区切り記号を使用しなかった場合は、このパラメーターを NULL に設定します。  
  
 `dwFlags`  
 [in]スクリプト ブロックに関連付けられているフラグです。 次の値の組み合わせが可能です。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|ある識別子およびドット演算子での識別 SOURCETEXT_ATTR_IDENTIFIER と SOURCETEXT_ATTR_MEMBERLOOKUP フラグでは、それぞれを示します。|  
|GETATTRFLAG_THIS|0x0100|現在のオブジェクトの識別子が SOURCETEXT_ATTR_THIS フラグで識別されることを示します。|  
|GETATTRFLAG_HUMANTEXT|0x8000|文字列のコンテンツおよびコメントのテキストが SOURCETEXT_ATTR_HUMANTEXT フラグで識別されることを示します。|  
  
 `pattr`  
 [入力、出力]返される属性を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 実装するスマート ホスト`IDebugDocumentText`インターフェイスはこのメソッドを使用して、デリゲートの呼び出しを`IDebugDocumentText::GetText`メソッド。  
  
 このメソッドのスクリプト ブロックです。`GetScriptletTextAttributes`メソッドがスクリプトレットです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptDebug インターフェイス](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)