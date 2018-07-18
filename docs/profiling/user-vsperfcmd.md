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
ms.openlocfilehash: 128fe1f59cc652d0879e346689c9e84f1c1d9e82
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477055"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
**User** オプションは、プロファイリングされるプロセスを所有するアカウントのドメインとユーザー名を指定します。 このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合にのみ指定する必要があります。 プロセスの所有者は、Windows タスク マネージャーの **[プロセス]** タブの [ユーザー名] 列に表示されます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)