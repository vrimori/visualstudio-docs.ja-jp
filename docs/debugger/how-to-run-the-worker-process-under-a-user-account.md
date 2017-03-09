---
title: "方法 : ユーザー アカウントでワーカー プロセスを実行する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ユーザー アカウント、aspnet_wp.exe"
  - "ASP.NET、Web アプリケーションのデバッグ"
  - "ツール、aspnet_wp.exe"
  - "ASP.NET ツール"
  - "aspnet_wp.exe"
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : ユーザー アカウントでワーカー プロセスを実行する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ユーザー アカウントを使用して [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセス (aspnet_wp.exe または w3wp.exe) を実行できるようにコンピューターを設定するには、次の手順を実行します。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>ユーザー アカウントで aspnet_wp.exe を実行するには  
  
1.  コンピューターでランタイムをインストールしたパスの CONFIG フォルダーにある machine.config ファイルを開きます。  
  
2.  検索、 &lt;processModel&gt; セクションし、ユーザー名とパスワードの属性を名前と aspnet_wp.exe を実行するユーザー アカウントのパスワードに変更します。  
  
3.  machine.config ファイルを保存します。  
  
4.  [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)] では、既定で、IIS 6.0 がインストールされます。 対応するワーカー プロセスは w3wp.exe です。aspnet_wp.exe をワーカー プロセスとして IIS 6.0 モードで実行するには、次の手順を実行します。  
  
    1.  をクリックして **開始**, 、] をクリックして **管理ツール** にして **インターネット インフォメーション サービス**します。  
  
    2.   **インターネット インフォメーション サービス** ] ダイアログ ボックスを右クリックし、 **Web サイト** フォルダーを選択して **プロパティ**です。  
  
    3.   **Web サイトのプロパティ** ] ダイアログ ボックスで、選択 **サービス**します。  
  
    4.  選択 **iis 6.0 では分離モードで実行 WWW サービスを**します。  
  
    5.  閉じる、 **プロパティ** ] ダイアログ ボックスと **インターネット サービス マネージャー**します。  
  
5.  Windows のコマンド プロンプトを開き、次を実行してサーバーをリセットします。  
  
    ```  
    iisreset  
    ```  
    — または —  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  [Temporary [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files] フォルダーを探します。このフォルダーは、[CONFIG] フォルダーと同じパスにあります。 一時領域を右クリックし [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files] フォルダーと選択 **プロパティ** 、ショートカット メニュー。  
  
7.   **Temporary ASP.NET Files のプロパティ** ダイアログ ボックスで、をクリックして、 **セキュリティ** ] タブをクリックします。  
  
8.  [ **詳細設定**] をクリックします。  
  
9.  **Temporary ASP.Net Files のセキュリティの詳細設定** ] ダイアログ ボックスをクリックして **追加**します。  
  
     **] ダイアログ ボックスの [ユーザー、コンピューター、またはグループ** が表示されます。  
  
10. ユーザー名を入力、 **を選択するオブジェクト名を入力** ボックスをクリックして **OK**します。 ユーザー名は、「ドメイン名\ユーザー名」の形式で入力する必要があります。  
  
11.  **Temporary ASP.NET Files のアクセス許可エントリ** ] ダイアログ ボックスで、ユーザーに、 **フル コントロール**, 、] をクリックし、 **[ok]** を閉じる、 **ASP.NET 一時ファイルのエントリ** ] ダイアログ ボックス。  
  
12. A **セキュリティ** ] ダイアログ ボックスが表示され、システム フォルダーのアクセス許可を変更するかどうかは確認します。 **[はい]**をクリックします。  
  
13. をクリックして **OK** を閉じる、 **Temporary ASP.NET Files のプロパティ** ] ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
[ASP.NET のデバッグ: システム要件](../debugger/aspnet-debugging-system-requirements.md)  
  
