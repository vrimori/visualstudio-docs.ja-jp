---
title: IActiveScriptProfilerControl2::PrepareProfilerStop |Microsoft Docs
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
ms.openlocfilehash: 086ec8b4a126c65162638afde4d8081269757e1c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089519"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
該当するすべてのスクリプト エンジンのプロファイリングを停止することをプロファイラーに通知します。 このメソッドを使用する場合、完全な呼び出し履歴を取得できます[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]が実行されているは、プロファイリングを停止するとします。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
|`S_FALSE`|スクリプトが実行されていない場合、プロファイリングが停止しました。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|プロファイルが有効になっていません。|  
  
## <a name="remarks"></a>Remarks  
 呼び出す`IActiveScriptProfilerControl2::PrepareProfilerStop`により、呼び出し履歴内の関数のイベントが送信されます。 このメソッドは、現在のタブ上にある任意のスクリプティング エンジンのプロファイリングを停止する前に呼び出す必要があります。メソッドは、任意のスクリプティング エンジンに対して呼び出すことができます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 インターフェイス](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)