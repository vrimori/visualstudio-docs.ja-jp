---
title: IScriptNode::Alive |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0631690cbd961273175cf8dfbe35550980d4994d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728662"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
オブジェクトがアクティブであるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>パラメーター  
 メソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|スクリプトのノードはアクティブです。|  
  
## <a name="remarks"></a>コメント  
 オブジェクトがアクティブでない場合、コンポーネント オブジェクト モデル (COM) は、このメソッドの呼び出しをマーシャ リングのプロキシからエラーを返します。  
  
## <a name="see-also"></a>関連項目  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)