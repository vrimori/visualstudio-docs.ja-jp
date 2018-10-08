---
title: '方法: ユーザー アカウントでワーカー プロセスの実行 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08ac00384110cc73175286365fef6ee4b67a0170
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535941"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>方法 : ユーザー アカウントでワーカー プロセスを実行する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 実行、ワーカー プロセス ユーザー アカウントで](https://docs.microsoft.com/visualstudio/debugger/how-to-run-the-worker-process-under-a-user-account)。  
  
ユーザー アカウントを使用して [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセス (aspnet_wp.exe または w3wp.exe) を実行できるようにコンピューターを設定するには、次の手順を実行します。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>ユーザー アカウントで aspnet_wp.exe を実行するには  
  
1.  コンピューターでランタイムをインストールしたパスの CONFIG フォルダーにある machine.config ファイルを開きます。  
  
2.  検索、 &lt;processModel&gt;セクションし、ユーザー名とパスワードの属性を aspnet_wp.exe を実行するユーザー アカウントのパスワードと名前に変更します。  
  
3.  machine.config ファイルを保存します。  
  
4.  [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)] では、既定で、IIS 6.0 がインストールされます。 対応するワーカー プロセスは w3wp.exe です。aspnet_wp.exe をワーカー プロセスとして IIS 6.0 モードで実行するには、次の手順を実行します。  
  
    1.  クリックして**開始**、] をクリックして**管理ツール**選び、**インターネット インフォメーション サービス**します。  
  
    2.  **インターネット インフォメーション サービス**ダイアログ ボックスを右クリックし、 **Websites**フォルダー選択**プロパティ**します。  
  
    3.  **Web サイトのプロパティ**] ダイアログ ボックスで、選択**サービス**します。  
  
    4.  選択**実行 WWW サービスを使用して IIS6.0 分離モードで**します。  
  
    5.  閉じる、**プロパティ**] ダイアログ ボックスと**インターネット サービス マネージャー**します。  
  
5.  Windows のコマンド プロンプトを開き、次を実行してサーバーをリセットします。  
  
    ```  
    iisreset  
    ```  
    または  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  [Temporary [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Files] フォルダーを探します。このフォルダーは、[CONFIG] フォルダーと同じパスにあります。 一時的なを右クリックして[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]ファイルのフォルダーと選択**プロパティ**ショートカット メニューの [します。  
  
7.  **Temporary ASP.NET Files のプロパティ**ダイアログ ボックスで、をクリックして、**セキュリティ**タブ。  
  
8.  [ **詳細設定**] をクリックします。  
  
9. **Temporary ASP.Net Files のセキュリティの詳細設定**ダイアログ ボックスで、をクリックして**追加**します。  
  
    **] ダイアログ ボックスの [ユーザー、コンピューター、またはグループ**が表示されます。  
  
10. ユーザー名を入力、**を選択するオブジェクト名を入力**ボックスし、順にクリックします**OK**。 ユーザー名は、「ドメイン名\ユーザー名」の形式で入力する必要があります。  
  
11. **Temporary ASP.NET Files のアクセス許可エントリ**] ダイアログ ボックスで、ユーザーに与えます**フル コントロール**、順にクリックします**OK**を閉じる、**一時的な ASP のエントリ.NET ファイル**] ダイアログ ボックス。  
  
12. A**セキュリティ**] ダイアログ ボックスが表示され、システム フォルダーのアクセス許可を変更するかどうかを確認します。 **[はい]** をクリックします。  
  
13. クリックして**OK**を閉じる、 **Temporary ASP.NET Files のプロパティ**] ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
[ASP.NET のデバッグ : システム要件](../debugger/aspnet-debugging-system-requirements.md)  
  




