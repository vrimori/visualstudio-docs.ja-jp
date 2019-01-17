---
title: IDebugApplicationNode::GetParent |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.GetParent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::GetParent
ms.assetid: 88ba3a53-0cd7-4e1f-8558-79c20ac76cc9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46b13c583f4e40b68610e50b37520f3d3882f364
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089649"
---
# <a name="idebugapplicationnodegetparent"></a>IDebugApplicationNode::GetParent
このアプリケーションのノードの親ノードを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetParent(  
   IDebugApplicationNode**  pprddp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pprddp`  
 [out]このアプリケーションのノードの親アプリケーション ノード。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、このアプリケーションのノードの親ノードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)