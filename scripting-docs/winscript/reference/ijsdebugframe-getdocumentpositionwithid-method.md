---
title: Ijsdebugframe::getdocumentpositionwithid メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c37f31ca6b75ca826dbdab93847a1e70ff054c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090013"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId メソッド
ユーザー レベルのドキュメント内でのこのスタック フレームの現在の位置を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pDocumentId`  
 [出力] ソース ドキュメントの一意の ID (IDebugDocumentText へのポインター)。  
  
 `pCharacterOffset`  
 [出力] スクリプトの先頭からの 0 から始まるオフセット。  
  
 `pStatementCharCount`  
 [出力] *pCharacterOffset から始まる現在のステートメントの長さ (文字数)。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)