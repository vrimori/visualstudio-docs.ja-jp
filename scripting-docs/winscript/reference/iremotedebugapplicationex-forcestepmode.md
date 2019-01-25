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
ms.openlocfilehash: 3cb5c94c55709f5ecdbd6bae63ee3366f3dfeb2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790855"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode

シングル ステップ モードにデバッガーを強制します。

## <a name="syntax"></a>構文

```cpp
HRESULT ForceStepMode(
   IRemoteDebugApplicationThread*  pStepThread
);
```

### <a name="parameters"></a>パラメーター

`pStepThread`

[in]ステップ イン プロセスのデバッグ モニターのスレッド。 Null の場合、PDM は、ステップ実行のスレッドをクリアします。

## <a name="return-value"></a>戻り値

このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。

|[値]|説明|
|-----------|-----------------|
|`S_OK`|メソッドが成功しました。|

## <a name="see-also"></a>関連項目

- [IRemoteDebugApplicationEx インターフェイス](iremotedebugapplicationex-interface.md)