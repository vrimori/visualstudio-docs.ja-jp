---
title: "IActiveScriptDebug::GetScriptletTextAttributes |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909879030e5c6d26353d2003279d5c1ca7bacb74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
任意のスクリプトレットのテキスト属性を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrCode`  
 [in]スクリプトレット テキストです。 この文字列は、されません null 終端である必要があります。  
  
 `uNumCodeChars`  
 [in]スクリプトレット テキストの文字の数。  
  
 `pstrDelimiter`  
 [入力] スクリプトレット末尾の区切り記号のアドレス。 `pstrCode` がテキストのストリームから解析されるとき、ホストは通常、2 つの単一引用符 ('') などの区切り文字を使用してスクリプトレットの末尾を検出します。 このパラメーターには、ホストが使用する区切り文字を指定します。それにより、スクリプト エンジンで何らかの条件付きのプリミティブな前処理が可能になります (単一引用符 (') を区切り文字として使用するために 2 つの単一引用符に置き換えるなど)。 正確に (および場合)、スクリプト エンジン使用してこの情報は、スクリプト エンジンによって異なります。 ホストがスクリプトレットの末尾を示すため、区切り記号を使用しなかった場合は、このパラメーターを NULL に設定します。  
  
 `dwFlags`  
 [入力] スクリプトレットに関連付けられるフラグ。 次の値の組み合わせが可能です。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|識別子およびドット演算子必要がありますを特定できる SOURCETEXT_ATTR_IDENTIFIER と SOURCETEXT_ATTR_MEMBERLOOKUP フラグでそれぞれを示します。|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS フラグで、現在のオブジェクトの識別子を特定する必要があることを示します。|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT フラグで文字列のコンテンツとコメントのテキストを特定する必要があることを示します。|  
  
 `pattr`  
 [入力、出力].返される属性を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 実装するスマート ホスト`IDebugDocumentText`インターフェイスはこのメソッドを使用して、委任への呼び出し、`IDebugDocumentText::GetText`メソッドです。  
  
 スクリプトレットは、式を指定する傾向があり、スクリプト ブロックとは異なる構文がありますので、この呼び出しが提供されます。 このメソッドの実装の実装と同じになる同じ構文がある場合、`GetScriptTextAttributes`メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptDebug インターフェイス](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)