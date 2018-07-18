---
title: IDebugApplicationNode::EnumChildren |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.EnumChildren
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::EnumChildren
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8ab13f3a284b1b36550367e68ca5fe600db3be6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725392"
---
# <a name="idebugapplicationnodeenumchildren"></a>IDebugApplicationNode::EnumChildren
このアプリケーション ノードの子ノードを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pperddp`  
 [out]このノードの子ノードの列挙です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、このアプリケーション ノードの子ノードを列挙します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)