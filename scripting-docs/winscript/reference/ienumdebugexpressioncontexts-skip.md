---
title: IEnumDebugExpressionContexts::Skip |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExpressionContexts.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugExpressionContexts::Skip
ms.assetid: 3498cbb5-8581-4dcd-b016-e86b049c7831
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ffc4a6246961c581fa56ca16d0635a116436210
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096877"
---
# <a name="ienumdebugexpressioncontextsskip"></a>IEnumDebugExpressionContexts::Skip
指定された数の列挙体シーケンス内のセグメントをスキップします。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする列挙体シーケンス内のセグメントの数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、指定された数の列挙体シーケンス内のセグメントをスキップします。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugExpressionContexts インターフェイス](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)