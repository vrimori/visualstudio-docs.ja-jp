---
title: "ユーザー アクセス許可と Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: dc32236dad42ec169fc1c7a243b7c67fd5a8dbf3
ms.lasthandoff: 03/07/2017

---
# <a name="user-permissions-and-visual-studio"></a>ユーザー アクセス許可と Visual Studio
セキュリティ上の理由により、Visual Studio はできる限り通常のユーザーとして実行してください。  

> [!WARNING]
>  また、信頼できる人または信頼できる場所以外から入手した Visual Studio ソリューションをコンパイル、起動、またはデバッグしないでください。  

 通常のユーザーでも Visual Studio IDE のほぼすべてのタスクを実行できますが、次のタスクを実行するには管理者のアクセス許可が必要です。  

|領域|タスク|詳細情報|  
|----------|----------|--------------------------|  
|インストール|Visual Studio をインストールする。|[Visual Studio のインストール](../install/install-visual-studio.md)|  
||ローカル ヘルプ コンテンツをインストール、更新、または削除する。|[ローカル コンテンツのインストールと管理](../ide/install-and-manage-local-content.md)|  
|アプリケーションの種類|SharePoint のソリューションを開発する。|[SharePoint ソリューションの開発要件](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|  
||[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] の開発者ライセンスを取得する。|[開発者用ライセンスの取得](http://go.microsoft.com/fwlink/?LinkID=241313)|  
|ツールボックス|**ツールボックス**にクラシック COM コントロールを追加する。|[ツールボックスの使用](../ide/using-the-toolbox.md)|  
|アドイン|IDE でクラシック COM を使用して記述されたアドインをインストールおよび使用する。|[アドインおよびウィザードの作成](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|  
|ビルド|コンポーネントを登録するビルド後のイベントを使用する。|[カスタム ビルド ステップとビルド イベントについて](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
||C++ プロジェクトのビルド時に登録手順を含める。|[カスタム ビルド ステップとビルド イベントについて](/visual-cpp/ide/understanding-custom-build-steps-and-build-events)|  
|デバッグ|昇格されたアクセス許可で実行されたアプリケーションをデバッグする。|[デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)|  
||ASP.NET Web サイトなど、別のユーザー アカウントで実行されたアプリケーションをデバッグする。|[ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)|  
||XAML ブラウザー アプリケーション (XBAP) をゾーンでデバッグする。|[WPF ホスト (PresentationHost.exe)](http://msdn.microsoft.com/Library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|  
||エミュレーターを使用して、Microsoft Azure クラウド サービス プロジェクトをデバッグする。|[Visual Studio でのクラウド サービスのデバッグ](http://go.microsoft.com/fwlink/?LinkId=266725)|  
||リモート デバッグのファイアウォールを構成する。|[Remote Debugging](../debugger/remote-debugging.md)|  
|パフォーマンス ツール|アプリケーションをプロファイルする。|[パフォーマンス プロファイリングのビギナーズ ガイド](../profiling/beginners-guide-to-performance-profiling.md)|  
|配置|ローカル コンピューターでインターネット インフォメーション サービス (IIS) に Web アプリケーションを配置する。|[Visual Studio または Visual Web Developer を使用しているホスティング プロバイダーへの ASP.NET Web アプリケーションの配置: テスト環境としての IIS への配置](http://go.microsoft.com/fwlink/?LinkId=266478)|

## <a name="running-visual-studio-as-an-administrator"></a>管理者としての Visual Studio の実行  
 IDE を起動するたびに管理アクセス許可を使用して Visual Studio を起動するか、管理アクセス許可で常に実行するようにアプリケーション ショートカットを変更できます。 詳細については、Windows のヘルプを参照してください。  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8debuggerincludeswin8mdmd-includewin81debuggerincludeswin81mdmd-includewinserver8debuggerincludeswinserver8mdmd-or-includewinblueserver2ideincludeswinblueserver2mdmd"></a>[!INCLUDE[win8](../debugger/includes/win8_md.md)]、[!INCLUDE[win81](../debugger/includes/win81_md.md)]、[!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)]、または [!INCLUDE[winblue_server_2](../ide/includes/winblue_server_2_md.md)] で管理アクセス許可を使用して Visual Studio を実行するには  

1.  **[スタート]** 画面で、「**Visual Studio**」と入力します。 インストールされている Visual Studio のバージョンが表示されます。  

2.  起動する Visual Studio のバージョンを選択し、ショートカット メニューを表示します (画面の下部に表示されます)。 **[管理者として実行]**を選択します。  

     Visual Studio の起動時には、**[(管理者)]** がタイトル バーの製品名の後に表示されます。  

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7debuggerincludeswin7mdmd-or-includewinsvr08r2debuggerincludeswinsvr08r2mdmd"></a>または [!INCLUDE[win7](../debugger/includes/win7_md.md)] で管理アクセス許可を使用して Visual Studio を実行するには[!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]  

1.  **[スタート]** メニューをクリックし、**[すべてのプログラム]** をクリックします。  

2.  **[Microsoft Visual Studio** *Version]* フォルダーで、**[Visual Studio** *Version]* をクリックし、ショートカット メニューを開き、**[管理者として実行]** をクリックします。  

     Visual Studio の起動時には、**[(管理者)]** がタイトル バーの製品名の後に表示されます。  

## <a name="see-also"></a>関連項目  
 [Visual Studio プロジェクトの移植、移行、およびアップグレード](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [Visual Studio のインストール](../install/install-visual-studio.md)

