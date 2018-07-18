---
title: IDebugDocumentText::GetContextOfPosition |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1be8bb6d350a2ca68912622396af52f1625985a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727182"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
指定された文字位置の範囲に対応するドキュメントのコンテキスト オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cCharacterPosition`  
 [in]位置の文字範囲の位置を開始します。  
  
 `cNumChars`  
 [in]範囲の文字の数。  
  
 `ppsc`  
 [out]指定した文字位置の範囲に対応するドキュメントのコンテキスト オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、指定された文字位置の範囲に対応するドキュメントのコンテキスト オブジェクトを作成します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentText インターフェイス](../../winscript/reference/idebugdocumenttext-interface.md)