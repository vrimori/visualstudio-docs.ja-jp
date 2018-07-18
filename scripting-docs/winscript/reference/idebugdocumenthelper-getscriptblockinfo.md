---
title: IDebugDocumentHelper::GetScriptBlockInfo |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e8dc63b8419424ed3fa01f67d3e77f0bc2b57f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726212"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
文字と、スクリプト ブロックに対応するスクリプト エンジンの範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwSourceContext`  
 [in]スクリプト ブロックのソース コンテキスト。  
  
 `ppasd`  
 [out]このスクリプト ブロックのスクリプト エンジンです。  
  
 `piCharPos`  
 [out]スクリプト ブロックの先頭の場所です。  
  
 `cChars`  
 [out]スクリプト ブロック内の文字の数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、文字と、スクリプト ブロックに対応するスクリプト エンジンの範囲を取得します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)