---
title: "IDebugDocumentHelper::AddDeferredText |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
指定されたテキストが、利用できない文字は行われません、ヘルパーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cChars`  
 [in]追加する (Unicode) 文字の数。  
  
 `dwTextStartCookie`  
 [in]テキストの開始位置を表すホスト定義クッキー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|メソッドが失敗しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、必要になるまで、状態の正確な通知とサイズの情報を生成するヘルパーを追加する文字を提供することを遅延させるホストを許可します。 `dwTextStartCookie`パラメーターは、cookie、テキストの開始位置を表すホストによって定義されます。 後続の呼び出し`IDebugDocumentText::GetText`この cookie を提供する必要があります。 たとえば、DBCS でテキストを表すホスト、cookie ことのバイト オフセット。  
  
 仮定に 1 回の呼び出し`IDebugDocumentText::GetText`が複数の呼び出しから文字を取得することができます`AddDeferredText`です。 遅延の文字の同じ範囲のヘルパー クラスは複数回要求可能性があります。  
  
> [!NOTE]
>  呼び出す`AddDeferredText`の呼び出しを混在させないでください`AddUnicodeText`または`AddDBCSText`です。 この場合、`E_FAIL`が返されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)