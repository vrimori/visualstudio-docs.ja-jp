---
title: 実行中の ASP.NET プロセスの検索 |Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 120b5b6818900b8f177a7358d9ef0cee7bb88482
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992621"
---
# <a name="find-the-name-of-the-aspnet-process"></a>ASP.NET プロセスの名前を見つける

デバッグ、実行中に[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]アプリに Visual Studio デバッガーをアタッチする必要があります、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]名前で処理します。

**確認するには、プロセスは、ASP.NET アプリを実行しています。**

1. アプリが実行されている、Visual Studio で、次のように選択します。**デバッグ** > **プロセスにアタッチ**します。 
   
1. **プロセスにアタッチ**ダイアログ ボックスで、型プロセスの最初の文字が次の一覧から名前または検索ボックスに入力します。 ASP.NET アプリの実行を実行している 1 つです。 アプリをデバッグするには、そのプロセスにアタッチします。 
   
    - *w3wp.exe* 6.0 以降、IIS です。 
    - *aspnet_wp.exe*は IIS の以前のバージョン。
    - *iisexpress.exe* IISExpress です。
    - *dotnet.exe* ASP.NET Core です。
    - *inetinfo.exe*インプロセスで実行されている古い ASP アプリケーションです。 

>[!NOTE]
>Visual Studio 2012 以前[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]コードがファイル システム上にあるし、テスト サーバーで実行*WebDev.WebServer.exe*または*WebDev.WebServer40.exe*します。 この場合は、ローカル デバッグにアタッチ*WebDev.WebServer.exe*または*WebDev.WebServer40.exe*の代わりに、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]プロセス。 

**関連項目:**

 [実行中のプロセスにアタッチする](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Web アプリケーションのリモート デバッグの前提条件](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)   
 [システム要件](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET アプリケーションをデバッグする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)