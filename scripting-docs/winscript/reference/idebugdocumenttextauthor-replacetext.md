---
title: IDebugDocumentTextAuthor::ReplaceText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 579d0ef243de7cd9bfcb821e75aa5ca213712a88
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090598"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
ドキュメントのテキストに置き換えます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cCharacterPosition`  
 [in]置換する文字の範囲の位置を開始します。  
  
 `cNumToReplace`  
 [in]置換する文字の数。  
  
 `pcharText[]`  
 [in]古い文字を置換する新しい文字を格納するバッファー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ドキュメントのテキストを置き換えます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentTextAuthor インターフェイス](../../winscript/reference/idebugdocumenttextauthor-interface.md)