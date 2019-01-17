---
title: IScriptNode::Delete |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce802cc1a6d63001cfbed020592b30a9d8dab1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094797"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
このオブジェクトのツリーを削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>パラメーター  
 メソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 後に、`Delete`メソッドを呼び出すと、 [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)そのスクリプトのノードがアクティブでないメソッドを示す必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)