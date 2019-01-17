---
title: IRemoteDebugApplicationEvents::OnSetName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnSetName
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnSetName
ms.assetid: 524dcff3-fb48-4d8f-8989-73eb539454fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a46eda1d041175b9cfca9c7304696b4e6a868d6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086568"
---
# <a name="iremotedebugapplicationeventsonsetname"></a>IRemoteDebugApplicationEvents::OnSetName
設定の名前のイベントを処理します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OnSetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrName`  
 [in]新しい名前。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、設定の名前のイベントを処理します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationEvents インターフェイス](../../winscript/reference/iremotedebugapplicationevents-interface.md)