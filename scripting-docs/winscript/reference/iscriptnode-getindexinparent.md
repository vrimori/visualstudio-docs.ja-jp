---
title: IScriptNode::GetIndexInParent |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3862a48ff4649f018eec79bf0411f23bc9f6d7bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733652"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
親の子の一覧で、オブジェクトのインデックスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pisn`  
 [out]親の子の一覧で、オブジェクトのインデックスを返します。  
  
 このメソッドが呼び出された場合、`IScriptNode`オブジェクトを Web ページを表す、このパラメーターは 0 を返します。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)