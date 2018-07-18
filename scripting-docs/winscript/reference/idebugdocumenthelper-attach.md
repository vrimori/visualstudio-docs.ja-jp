---
title: IDebugDocumentHelper::Attach |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97ddb49f61e9df4044eb6e16b853e6cf8155162a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726972"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
このドキュメントをドキュメント ツリーに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pddhParent`  
 [in]ドキュメント ツリーは、このドキュメントを追加します。 NULL にすることがあります。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドでは、このドキュメントを追加、ドキュメントをツリーを使用して`pddhParent`親として。 場合、`pddhParent`は`NULL`、このドキュメントは、最上位のドキュメントになります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)