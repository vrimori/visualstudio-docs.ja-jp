---
title: '方法: ユーザー アカウントでワーカー プロセスを実行 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc474bc2b8c191a753e9b27ebbb57e397145b2e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>方法 : ユーザー アカウントでワーカー プロセスを実行する
ユーザー アカウントを使用して [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセス (aspnet_wp.exe または w3wp.exe) を実行できるようにコンピューターを設定するには、次の手順を実行します。  

 > [!IMPORTANT]
 > Windows Server 2008 R2 以降では、ことをお勧めの使用、 [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities)各アプリケーション プールの id として。
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>ユーザー アカウントで aspnet_wp.exe を実行するには  
  
1.  コンピューターでランタイムをインストールしたパスの CONFIG フォルダーにある machine.config ファイルを開きます。  
  
2.  検索、 &lt;processModel&gt;セクション属性を変更したり、ユーザー名とパスワードを名前および aspnet_wp.exe を実行するユーザー アカウントのパスワード。  
  
3.  machine.config ファイルを保存します。  
  
4.  [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] では、既定で、IIS 6.0 がインストールされます。 対応するワーカー プロセスは w3wp.exe です。aspnet_wp.exe をワーカー プロセスとして IIS 6.0 モードで実行するには、次の手順を実行します。  
  
    1.  をクリックして**開始**をクリックして**管理ツール**を選択し**インターネット インフォメーション サービス**です。  
  
    2.  **インターネット インフォメーション サービス**ダイアログ ボックスを右クリックし、 **Websites**フォルダーを選択し、**プロパティ**です。  
  
    3.  **Web サイトのプロパティ** ダイアログ ボックスで、選択**サービス**です。  
  
    4.  選択**iis 6.0 プロセス分離モードで実行 WWW サービス**です。  
  
    5.  閉じる、**プロパティ** ダイアログ ボックスと**インターネット サービス マネージャー**です。  
  
5.  Windows のコマンド プロンプトを開き、次を実行してサーバーをリセットします。  
  
    ```  
    iisreset  
    ```  
    または  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  [Temporary [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files] フォルダーを探します。このフォルダーは、[CONFIG] フォルダーと同じパスにあります。 一時領域を右クリックして[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Files] フォルダーと選択**プロパティ**ショートカット メニューの [します。  
  
7.  **Temporary ASP.NET Files のプロパティ**ダイアログ ボックスで、をクリックして、**セキュリティ**タブです。  
  
8.  **[詳細設定]** をクリックします。  
  
9. **Temporary ASP.Net Files のセキュリティの詳細設定**ダイアログ ボックスで、をクリックして**追加**です。  
  
    **] ダイアログ ボックスの [ユーザー、コンピューター、またはグループ**が表示されます。  
  
10. ユーザー名を入力、**を選択するオブジェクト名を入力**ボックスし、をクリックして**OK**です。 ユーザー名は、「ドメイン名\ユーザー名」の形式で入力する必要があります。  
  
11. **Temporary ASP.NET Files のアクセス許可エントリ** ダイアログ ボックスで、ユーザーに付与**フル コントロール**、クリックして**ok**を閉じる、**一時的な ASP のエントリ.NET ファイル** ダイアログ ボックス。  
  
12. A**セキュリティ** ダイアログ ボックスが表示され、システム フォルダーのアクセス許可を変更するかどうかは確認します。 **[はい]**をクリックします。  
  
13. をクリックして**OK**を閉じる、 **Temporary ASP.NET Files のプロパティ** ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
[ASP.NET アプリケーションをデバッグします。](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
[ASP.NET のデバッグ : システム要件](../debugger/aspnet-debugging-system-requirements.md)  
  
