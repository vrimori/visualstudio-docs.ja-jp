---
title: "IDebugDocumentText::GetText |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
文字または文字位置の範囲に関連付けられた文字属性を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cCharacterPosition`  
 [in]位置の文字範囲の位置を開始します。  
  
 `pcharText`  
 [入力、出力].文字のテキスト バッファー。 バッファーを保持するのに十分な大きさにする必要があります`cMaxChars`文字です。 このパラメーターが NULL の場合、メソッドは、文字を返しません。  
  
 `pstaTextAttr`  
 [入力、出力].文字属性バッファーです。 バッファーを保持するのに十分な大きさにする必要があります`cMaxChars`文字です。 このパラメーターが NULL の場合、メソッドは、属性を返しません。  
  
 `pcNumChars`  
 [入力、出力].文字/属性の数が返されます。 このパラメーターは、このメソッドを呼び出す前に 0 に設定する必要があります。  
  
 `cMaxChars`  
 [in]位置の文字範囲の文字数。 返される文字の最大数を指定します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、文字または文字位置の範囲に関連付けられた文字属性を取得します。 位置の文字範囲は、文字位置と文字数で指定されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)