---
title: IActiveScriptProfilerControl2::CompleteProfilerStart |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724502"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
すべての該当するスクリプト エンジンでプロファイリングを開始したことをプロファイラーに通知します。 このメソッドを使用する場合、完全な呼び出し履歴を取得できます[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]プロファイリングを開始するときに実行します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>パラメーター  
 メソッドには、すべてのパラメーターは取りません。  
  
## <a name="return-value"></a>戻り値  
 HRESULT を返します。 次の値を指定できます。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|プロファイリングを開始できません。|  
|`S_FALSE`|スクリプトが実行されていないときに、プロファイリングが開始されました。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|プロファイリングすることは無効です。 コールバックが設定されていません。|  
|`E_OUTOFMEMORY`|メモリ不足の状態のため、呼び出し履歴を取得できません。|  
  
## <a name="remarks"></a>コメント  
 呼び出す`IActiveScriptProfilerControl2::CompleteProfilerStart`関数の呼び出し履歴の中のイベントが送信されることを確認します。 このメソッドでは、プロファイリング、現在のタブ上にある任意のスクリプト エンジンで起動後に呼び出されます。スクリプト エンジンで任意のメソッドを呼び出すことができます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 インターフェイス](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)