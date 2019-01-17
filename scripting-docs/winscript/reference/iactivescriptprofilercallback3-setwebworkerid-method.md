---
title: Iactivescriptprofilercallback 3::setwebworkerid メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094434"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId メソッド
このプロファイル セッションに使用する worker ID をプロファイラーに通知します。 関数は、ページのコンテキストで実行されていない、このメソッドは呼び出されません。 値`webWorkerId`1 で始まるすべての worker の場合は 1 ずつインクリメントされます。 ID 値はのセッションの終了後に安定していますし、ワーカーが作成された順序にのみ対応のものではありません。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `webWorkerId`  
 Web worker の id。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。