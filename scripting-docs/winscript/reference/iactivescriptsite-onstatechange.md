---
title: IActiveScriptSite::OnStateChange |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee4fd06b00c674c9c50ce253186aeee3165bac66
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345696"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
スクリプト エンジンの状態が変更されたことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ssScriptState`  
 [in]新しいスクリプトの状態を示す値。 参照してください、 [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)メソッド、状態の説明についてはします。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)