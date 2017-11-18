---
title: "Iactivescriptprofilercallback 3::setwebworkerid メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId メソッド
このプロファイルのセッションに使用するワーカーの ID をプロファイラーに通知します。 関数は、ページのコンテキストで実行していない、このメソッドは呼び出されません。 値`webWorkerId`1 で始まるすべてのワーカーの場合は 1 ずつインクリメントされます。 ID の値は、セッションを超える安定しているし、ワーカーが作成された順序のみに対応するものではありません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `webWorkerId`  
 Web ワーカーの id。  
  
## <a name="return-value"></a>戻り値  
 このメソッドの戻り値は、スクリプト エンジンによって無視されます。