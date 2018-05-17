---
title: User (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b96005f0935f0d1a50233196aa01bf157b6e0cd
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
**User** オプションは、プロファイリングされるプロセスを所有するアカウントのドメインとユーザー名を指定します。 このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合にのみ指定する必要があります。 プロセスの所有者は、Windows タスク マネージャーの [プロセス] タブの [ユーザー名] 列に表示されます。  
  
 **User** オプションは、**Start** オプションも含むコマンド ラインでのみ指定できます。  
  
## <a name="syntax"></a>構文  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Domain`  
 ユーザーのドメインの名前。  
  
 `UserName`  
 ユーザーの名前。  
  
## <a name="required-options"></a>必須オプション  
 **User** オプションは、**Start** オプションと共に指定する場合にのみ使用できます。  
  
 **Start:** `Method`  
 指定したプロファイル方法にプロファイラーを初期化します。  
  
## <a name="example"></a>例  
 **User** オプションの使用例を以下に示します。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)