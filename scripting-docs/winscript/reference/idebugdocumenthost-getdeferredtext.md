---
title: Idebugdocumenthost::getdeferredtext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f2a39122454ea170177aee9ce7b2bbeb7ea248e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092561"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
使用して追加された文字の範囲を返します、`IDebugDocumentHelper::AddDeferredText`元ホスト ドキュメント内のメソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 [in]テキストの開始位置を表すホスト定義のクッキー。  
  
 `pcharText`  
 [入力、出力]文字のテキスト バッファー。 このパラメーターがある場合に、このメソッドで文字が返されません`NULL`します。  
  
 `pstaTextAttr`  
 [入力、出力]文字の属性のバッファー。 このパラメーターがある場合に、このメソッドで属性が返されません`NULL`します。  
  
 `pcNumChars`  
 [入力、出力]返される文字/属性の実際の数を示します。 このパラメーターは、このメソッドを呼び出す前にゼロに設定する必要があります。  
  
 `cMaxChars`  
 [in]返される文字の最大数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|メソッドが実装されていません。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドが返す可能性があります`E_NOTIMPL`ホストが要求されていない場合、`IDebugDocumentHelper::AddDeferredText`します。  
  
> [!NOTE]
>  このメソッドは、元のドキュメントからテキストを返します。 ホストを追跡するありません編集内容やその他の変更をドキュメントにします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)   
 [:Adddeferredtext](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR 列挙型](../../winscript/reference/source-text-attr-enumeration.md)