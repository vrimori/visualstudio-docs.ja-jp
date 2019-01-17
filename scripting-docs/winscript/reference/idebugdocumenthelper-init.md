---
title: :Init |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4bcb64b7bbb1c61e7f031d872f7d1440fd17833
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086633"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init`メソッドが名前と初期属性でのデバッグ ドキュメント ヘルパーを初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pda`  
 [in]このドキュメントに関連付けられているデバッグ アプリケーション。  
  
 `pszShortName`  
 [in]ドキュメントの短い名前を含む null で終わる文字列。  
  
 `pszLongName`  
 [in]ドキュメントの長い名前を含む null で終わる文字列。  
  
 `docAttr`  
 [in]テキスト ドキュメントの属性を指定します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、名前と初期属性でのデバッグ ドキュメント ヘルパーを初期化します。  
  
 このドキュメントは、ツリーまでにない`IDebugDocumentHelper::Attach`が呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR 定数](../../winscript/reference/text-doc-attr-constants.md)