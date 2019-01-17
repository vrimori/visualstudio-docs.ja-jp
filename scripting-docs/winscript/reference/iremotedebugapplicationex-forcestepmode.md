---
title: IRemoteDebugApplicationEx:ForceStepMode |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 771c17fdb8f2bea77959bc53b8d98fd10399a142
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094758"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode
シングル ステップ モードにデバッガーを強制します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStepThread`  
 [in]ステップ イン プロセスのデバッグ モニターのスレッド。 Null の場合、PDM は、ステップ実行のスレッドをクリアします。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplicationEx インターフェイス](http://msdn.microsoft.com/en-us/2f65fa67-06b7-4053-8945-22383ab66343)