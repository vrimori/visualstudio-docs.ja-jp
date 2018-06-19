---
title: '方法: ASP.NET プロセスの名前を見つける |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 899860baf5461eb798341cebf775ccde488915b7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473820"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>方法 : ASP.NET プロセスの名前を見つける
実行中の [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションにアタッチする場合、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] プロセスの名前を把握している必要があります。  

-   IIS または iis Express で ASP.NET Core を実行している場合は、dotnet.exe は、プロセス名です。

-   IIS 6.0 で ASP.NET を後で実行している場合、名前は w3wp.exe です。  
  
-   以前のバージョンの IIS で ASP.NET を実行している場合、名前は aspnet_wp.exe です。

-   Iis Express で ASP.NET を実行している場合は、iisexpress.exe は名前です。
  
Visual Studio、Visual Studio 2012 より前のバージョンを使用してビルドされたアプリケーション、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]コードをファイル システム上におよび、テスト サーバー WebDev.WebServer.exe または WebDev.WebServer40.exe の下で実行できます。 その場合は、WebDev.WebServer.exe またはの代わりに WebDev.WebServer40.exe にアタッチする必要があります、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]プロセスです。 ただし、これは、ローカル デバッグだけに当てはまります。
  
古いバージョンの ASP アプリケーションは、インプロセスで実行する場合、IIS プロセス inetinfo.exe 内で実行します。  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>アプリケーションが実行されている IIS のバージョンを判断するには  

1.  アプリケーションが実行されているかどうかを確認し、その後、Visual Studio から、次のように使用します。、[プロセスにアタッチする](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)コマンド。

2.  W3wp.exe プロセスをすばやく検索するように、プロセス名の最初の文字を入力、**選択可能なプロセス** ボックスの一覧です。

    このトピックの一覧から選択可能なプロセスは、IIS のバージョンが利用可能なおよびアプリケーションを実行しているどのプロセスで示されます。

    > [!NOTE]
    > Visual Studio 2017 以降、検索ボックスを使用して、プロセス名を検索します。
  
## <a name="see-also"></a>関連項目  
 [実行中のプロセスにアタッチする](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [リモートの Web アプリケーションのデバッグの前提](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [システム要件](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET アプリケーションをデバッグします。](../debugger/how-to-enable-debugging-for-aspnet-applications.md)