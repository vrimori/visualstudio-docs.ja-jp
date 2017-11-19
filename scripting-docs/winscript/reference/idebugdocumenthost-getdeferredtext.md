---
title: "IDebugDocumentHost::GetDeferredText |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
使用して追加された文字の範囲を返します、`IDebugDocumentHelper::AddDeferredText`元のホスト ドキュメント内のメソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwTextStartCookie`  
 [in]テキストの開始位置を表すホスト定義クッキー。  
  
 `pcharText`  
 [入力、出力].文字のテキスト バッファー。 このパラメーターがある場合に、このメソッドで文字が返されません`NULL`です。  
  
 `pstaTextAttr`  
 [入力、出力].文字属性バッファーです。 このパラメーターがある場合に、このメソッドで属性が返されません`NULL`です。  
  
 `pcNumChars`  
 [入力、出力].返される文字/属性の実際の数を示します。 このパラメーターは、このメソッドを呼び出す前に 0 に設定する必要があります。  
  
 `cMaxChars`  
 [in]返される文字の最大数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|メソッドは実装されていません。|  
  
## <a name="remarks"></a>コメント  
 このメソッドが返す可能性があります`E_NOTIMPL`ホストが要求されていない場合、`IDebugDocumentHelper::AddDeferredText`です。  
  
> [!NOTE]
>  このメソッドは、元のドキュメントからテキストを返します。 ホストはありませんの追跡の編集またはドキュメントには、他の変更。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)