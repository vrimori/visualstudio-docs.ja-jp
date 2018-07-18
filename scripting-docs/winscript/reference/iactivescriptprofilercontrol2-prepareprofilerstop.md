---
title: IActiveScriptProfilerControl2::PrepareProfilerStop |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724522"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
適用可能なすべてのスクリプト エンジンでプロファイリングを停止しようとしていることをプロファイラーに通知します。 このメソッドを使用する場合、完全な呼び出し履歴を取得できます[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]が実行されているは、プロファイリングを停止するとします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>パラメーター  
 メソッドには、すべてのパラメーターは取りません。  
  
## <a name="return-value"></a>戻り値  
 HRESULT を返します。 次の値を指定できます。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|プロファイリングを開始できませんでした。|  
|`S_FALSE`|スクリプトが実行されていないときに、プロファイリングが停止されました。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|プロファイリングすることは無効です。|  
  
## <a name="remarks"></a>コメント  
 呼び出す`IActiveScriptProfilerControl2::PrepareProfilerStop`関数の呼び出し履歴内のイベントが送信されることを確認します。 このメソッドには、現在のタブ上にある任意のスクリプト エンジンでプロファイリングを停止する前に呼び出されます。スクリプト エンジンで任意のメソッドを呼び出すことができます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 インターフェイス](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)