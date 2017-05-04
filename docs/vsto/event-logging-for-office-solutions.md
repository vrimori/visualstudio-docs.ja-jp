---
title: "Office ソリューションのイベント ログ | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office アプリケーション [Visual Studio での Office 開発]、イベント ビューアー"
  - "ClickOnce 配置 [Visual Studio での Office 開発]、イベント ビューアー"
  - "配置 (アプリケーションを) [Visual Studio での Office 開発]、イベント ビューアー"
  - "Visual Studio での Office 開発、イベント ビューアー"
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Office ソリューションのイベント ログ
  Windows のイベント ビューアーを使用すると、Office ソリューションのインストール時またはアンインストール時に [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] でキャプチャされる例外メッセージを表示できます。 イベント ロガーからのこれらのメッセージを使用して、インストールと配置の問題を解決できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## イベント ログの読み取り  
 **イベント ビューアー**を開き、目的のイベントを表示するためにフィルター処理します。  
  
#### Windows Server 2003 と Windows XP でイベント ログを読み取るには  
  
1.  \[コントロール パネル\] の **\[管理ツール\]** を開きます。  
  
2.  **イベント ビューアー**を開始します。  
  
3.  イベント ログの一覧で **\[アプリケーション\]** を選択します。  
  
4.  **\[表示\]** メニューの **\[フィルター\]** をクリックします。  
  
5.  **\[イベント ソース\]** 一覧で **\[VSTO 4.0\]** を選択します。  
  
6.  インストール イベントの場合は、**\[イベント ID\]** ボックスに **4096** と入力します。  
  
7.  **\[OK\]** をクリックして、フィルター処理されたビューを表示します。  
  
#### Windows 7、Windows Vista、Windows Server 2008 でイベント ログを読み取るには  
  
1.  \[コントロール パネル\] の **\[管理ツール\]** を開きます。  
  
2.  **イベント ビューアー**を開始します。  
  
3.  **\[Windows ログ\]** を展開します。  
  
4.  イベント ログの一覧で **\[アプリケーション\]** を選択します。  
  
5.  **\[アクション\]** メニューの **\[現在のログをフィルター処理\]** をクリックします。  
  
6.  **\[イベント ソース\]** 一覧で **\[VSTO 4.0\]** を選択します。  
  
7.  インストール イベントの場合は、**\[イベント ID\]** ボックスに **4096** と入力します。  
  
8.  **\[OK\]** をクリックして、フィルター処理されたビューを表示します。  
  
 イベント ビューアーに次の情報が表示されます。  
  
-   ソリューションの配置マニフェストの場所。  
  
-   エラーまたは例外の原因を説明するメッセージ。  
  
 これらの例外メッセージから、信頼されていない証明書、信頼されていないドキュメントの場所、無効な配置マニフェストといったインストール上の問題の原因を特定できます。  
  
 Office ソリューションをアンインストールしても、例外メッセージはイベント ログに残ります。  
  
 Office ソリューションを実行しているときに例外メッセージを表示またはログに記録するには、「[Office Project のデバッグ](../vsto/debugging-office-projects.md)」および「[Office Project のデバッグ](../vsto/debugging-office-projects.md)」を参照してください。  
  
### ローカリゼーション  
 例外メッセージの言語は、Office ランタイム言語の Visual Studio Tools によって決まります。 たとえば、エンド ユーザーのコンピューターに日本語の言語パックがインストールされている場合、例外メッセージは日本語でイベント ログに書き込まれます。  
  
## イベント ロガーの無効化  
 Office ソリューションをインストールまたはアンインストールするときには、既定ではイベント ロガーが有効になります。 イベント ロガーを無効にするには、VSTO\_EVENTLOGDISABLED 環境変数を「1」に設定します。  
  
#### イベント ログを無効にするには  
  
1.  \[コントロール パネル\] の **\[システム\]** を開きます。  
  
2.  **\[詳細設定\]** タブの **\[環境変数\]** をクリックします。  
  
3.  **\[システム変数\]** ウィンドウの **\[新規\]** をクリックします。  
  
4.  **\[新しいシステム変数\]** ダイアログ ボックスで、**\[変数名\]** ボックスに **VSTO\_EVENTLOGDISABLED** と入力します。  
  
5.  **\[変数値\]** ボックスに **1** と入力します。  
  
6.  **\[OK\]** をクリックします。  
  
## 参照  
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office ソリューション配置のトラブルシューティング](../vsto/troubleshooting-office-solution-deployment.md)  
  
  