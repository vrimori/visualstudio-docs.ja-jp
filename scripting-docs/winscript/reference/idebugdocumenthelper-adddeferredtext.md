---
title: :Adddeferredtext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba6f945e6c7fa4df83a5e301d73b3fc0bb9da92b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096084"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
指定されたテキストは、使用可能な文字は提供されませんが、ヘルパーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cChars`  
 [in]追加する (Unicode) 文字の数。  
  
 `dwTextStartCookie`  
 [in]テキストの開始位置を表すホスト定義のクッキー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|メソッドが失敗しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、正確な通知およびサイズの情報を生成するヘルパーを許可するときに必要になるまでを追加する文字を提供することを遅延するホストを使用します。 `dwTextStartCookie`パラメーターは、cookie、テキストの開始位置を表すホストで定義されています。 後続の呼び出し`IDebugDocumentText::GetText`この cookie を提供する必要があります。 たとえば、DBCS でテキストを表すホストで cookie 可能性がありますのバイト オフセット。  
  
 前提とする単一の呼び出し`IDebugDocumentText::GetText`複数の呼び出しから文字を取得できます`AddDeferredText`。 遅延の文字の同じ範囲にはヘルパー クラスは複数回要求可能性があります。  
  
> [!NOTE]
>  呼び出す`AddDeferredText`への呼び出しを混在させないでください`AddUnicodeText`または`AddDBCSText`します。 この場合、`E_FAIL`が返されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [:Addunicodetext](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [Idebugdocumenthelper::adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)