---
title: '方法: ASP.NET プロセスの名前を見つける |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 223e060083554169ab6ffdb95faf4979e9466d02
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825622"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>方法 : ASP.NET プロセスの名前を見つける
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

実行中の [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションにアタッチする場合、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] プロセスの名前を把握している必要があります。  
  
- IIS 6.0 または IIS 7.0 を実行している場合、プロセスの名前は w3wp.exe です。  
  
- 6.0 よりも前のバージョンの IIS を実行している場合、プロセスの名前は aspnet_wp.exe です。  
  
  使用して構築されたアプリケーションの[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]以降のバージョン、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]コードはファイル システム上に存在し、テスト サーバー WebDev.WebServer.exe の下で実行します。 この場合、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] プロセスの代わりに WebDev.WebServer.exe にアタッチする必要があります。 ただし、これは、ローカル デバッグだけに当てはまります。  
  
  古いバージョンの ASP アプリケーションは、インプロセスで実行する場合、IIS プロセス inetinfo.exe 内で実行します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>プロジェクト コードがファイル システムと IIS のどちらに存在するかを判断するには  
  
1.  Visual Studio で開く**ソリューション エクスプ ローラー**がまだ開いていない場合。  
  
2.  アプリケーション名を含む最上位のノードを選択します。  
  
3.  場合、**プロパティ**ウィンドウのタイトルは、ファイルのパスを含む、アプリケーション コード、ファイル システムに存在します。  
  
     それ以外の場合、**プロパティ**ウィンドウのタイトルは、Web サイトの名前が格納されます。  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>アプリケーションが実行されている IIS のバージョンを判断するには  
  
1.  検索**管理ツール**して実行します。 オペレーティング システムに応じて、アイコン内でこの可能性があります**コントロール パネルの **、またはクリックしたときに表示されるメニュー エントリ**開始**します。  
  
     Windows XP で**コントロール パネルの **カテゴリの表示またはクラシック表示にすることができます。 カテゴリ表示は、をクリックする必要がある**クラシック表示に切り替える**または**パフォーマンスとメンテナンス**を参照してください、**管理ツール**アイコン。  
  
2.  **管理ツール**、インターネット インフォメーション サービスを実行します。 MMC ダイアログ ボックスが表示されます。  
  
3.  左側のペインに複数のコンピューターが表示される場合、アプリケーション コードが存在するコンピューターを選択します。  
  
4.  IIS のバージョンは、**バージョン**右側のペインの列。  
  
## <a name="see-also"></a>関連項目  
 [リモート Web アプリケーションをデバッグするための前提条件](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [システム要件](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET のデバッグの準備](../debugger/preparing-to-debug-aspnet.md)   
 [Web アプリケーションとスクリプトのデバッグ](../debugger/debugging-web-applications-and-script.md)



