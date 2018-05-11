---
title: WaitStart | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d84688198ff9d21a03923bf510676c7f620e4d12
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="waitstart"></a>WaitStart
WaitStart オプションを指定すると、プロファイラーの初期化が完了したか、または指定した秒数が経過したときにのみ、VSPerfCmd.exe Start サブコマンドは制御を返します。 既定では、Start コマンドはすぐに制御を返します。 Start サブコマンドがプロファイラーを初期化せずに制御を返した場合、エラーが返されます。 秒数が指定されていない場合、Start コマンドは無期限に待機します。  
  
 WaitStart オプションは、バッチ ファイルで、確実にプロファイラーが初期化されるようにする場合に役立ちます。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Seconds`  
 Start サブコマンドから制御が返されるまで待機する秒数。  
  
## <a name="required-options"></a>必須オプション  
 WaitStart オプションは、Start サブコマンドでのみ使用できます。  
  
 **Output:** `filename`  
 出力ファイル名を指定します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 このバッチ ファイルの例では、Start コマンドは、プロファイラーが初期化されるまで 5 秒間待機します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```