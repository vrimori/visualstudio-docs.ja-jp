---
title: IRemoteDebugApplicationThread::EnumStackFrames |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.EnumStackFrames
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::EnumStackFrames
ms.assetid: 605ce83d-43d2-47ea-b066-ec8f0da50ca6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20abe2c10a0959f00e67d98ac405b74c35a0c032
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093275"
---
# <a name="iremotedebugapplicationthreadenumstackframes"></a>IRemoteDebugApplicationThread::EnumStackFrames
このスレッドに関連付けられているスタック フレームの列挙子を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppedsf`  
 [out]このスレッドに関連付けられているスタック フレームの列挙子。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、ブレークポイント内からを呼び出す必要があります。 スタック フレームの列挙子は、以降、最後にプッシュされたフレームでは、スタックの上部で開始フレームを返す必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationThread インターフェイス](../../winscript/reference/iremotedebugapplicationthread-interface.md)