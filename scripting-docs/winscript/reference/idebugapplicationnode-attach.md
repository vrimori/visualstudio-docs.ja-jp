---
title: IDebugApplicationNode::Attach |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49df95e2c5298fc9bb7025982e75a90548d9613f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094953"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
指定されたプロジェクト ツリーには、このアプリケーションのノードを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdanParent`  
 [in]このアプリケーションのノードが追加されるプロジェクト ツリー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドがプロジェクトにこのアプリケーションのノードを追加するツリーを使用して`pdanParent`親として。 場合`pdanParent`は`NULL`、このアプリケーションのノードが最上位のノードになります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)