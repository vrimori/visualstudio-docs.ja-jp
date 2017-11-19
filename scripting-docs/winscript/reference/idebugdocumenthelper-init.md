---
title: "IDebugDocumentHelper::Init |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init`メソッドは、名前と初期属性を持つデバッグ ドキュメント ヘルパーを初期化します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]ドキュメントの短い名前を表す、null で終わる文字列。  
  
 `pszLongName`  
 [in]ドキュメントの長い名前を表す、null で終わる文字列。  
  
 `docAttr`  
 [in]テキスト ドキュメントの属性を指定します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、名前と最初の属性を持つデバッグ ドキュメント ヘルパーを初期化します。  
  
 このドキュメントはまでツリーにない`IDebugDocumentHelper::Attach`と呼びます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT_DOC_ATTR 定数](../../winscript/reference/text-doc-attr-constants.md)