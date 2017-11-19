---
title: "IEnumDebugExpressionContexts::Skip |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExpressionContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugExpressionContexts::Skip
ms.assetid: 3498cbb5-8581-4dcd-b016-e86b049c7831
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49a0fc242b7bbcd29a5b46d66be5ce4d16a1b2ec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugexpressioncontextsskip"></a>IEnumDebugExpressionContexts::Skip
指定した列挙のシーケンス内のセグメント数をスキップします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする列挙のシーケンス内のセグメントの数です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、指定した列挙のシーケンス内のセグメント数をスキップします。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugExpressionContexts インターフェイス](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)