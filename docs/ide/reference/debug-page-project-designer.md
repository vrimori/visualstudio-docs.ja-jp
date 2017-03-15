---
title: "[デバッグ] ページ (プロジェクト デザイナー) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesDebug"
helpviewer_keywords: 
  - "プロジェクト デザイナー、[デバッグ] ページ"
  - "[デバッグ] ページ、プロジェクト デザイナー"
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# [デバッグ] ページ (プロジェクト デザイナー)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!WARNING]
>  このトピックでは、Windows ストア apps には適用されません。  Windows Dev の中央の [デバッグ セッションの開始 \(VB、C\#、C\+\+、および XAML\)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) を参照してください。  
  
 Visual Basic または C\# プロジェクトのデバッグ動作のプロパティを設定するに **\[プロジェクト デザイナー\]** の **\[デバッグ\]** のページを使用します。  
  
 **\[デバッグ\]** のページにアクセスするには、**\[ソリューション エクスプローラー\]**のプロジェクト ノードを選択します。  **\[プロジェクト\]** で、メニューの *\[プロジェクト名\]***\[プロパティ\]**を選択します。  **\[プロジェクト デザイナー\]** が表示されたら、**\[デバッグ\]** のタブをクリックします。  
  
## 構成およびプラットフォーム  
 次のオプションを使用すると、表示または変更する構成およびプラットフォームを選択できます。  
  
 **構成**  
 表示または変更する構成設定を指定します。  **\[デバッグ\]** 設定は、\(既定\)、**\[リリース\]**、または **\[すべての構成\]**のいずれかになります。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
 **プラットフォーム**  
 表示または変更するプラットフォーム設定を指定します。  オプションは **\[Any CPU\]** \(既定\)、**x64**と **x86**を含めることができます。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
## \[開始動作\]  
 **\[開始動作\]** は、アプリケーションをデバッグするときに開始するアイテムを指定します。プロジェクト、カスタム プログラム、URL のいずれかを指定できます。省略することもできます。  既定では、このオプションは **\[スタート プロジェクト\]**に設定されます。  **\[デバッグ\]** のページで設定 **\[開始動作\]** は `StartAction` のプロパティの値が決まります。  
  
 **\[プロジェクトの開始\]**  
 アプリケーションのデバッグ時に、実行可能ファイル \(Windows アプリケーションとコンソール アプリケーション プロジェクトの場合\) を起動することを指定するには、このオプションを選択します。  このオプションの既定値はオンです。  
  
 **\[外部プログラムの開始\]**  
 アプリケーションのデバッグ時に特定のプログラムが起動されるように指定するには、このオプションを選択します。  
  
 **\[ブラウザーを開始時に使用する URL\]**  
 アプリケーションのデバッグ時に特定の URL にアクセスすることを指定するには、このオプションを選択します。  
  
## \[開始オプション\]  
 **\[コマンド ライン引数\]**  
 このテキスト ボックスには、デバッグ用のコマンド ライン引数を入力します。  
  
 **\[作業ディレクトリ\]**  
 このテキスト ボックスには、プロジェクトを起動するディレクトリを入力します。  またはディレクトリを選択するには参照ボタン \(**\[...\]**\) をクリックします。  
  
 **\[リモート コンピューターの使用\]**  
 リモート コンピューターからアプリケーションをデバッグするには、このチェック ボックスをオンにし、リモート コンピューターにテキスト ボックスにパスを入力します。  
  
## \[デバッガーを有効にする\]  
 **\[アンマネージ コード デバッグを有効にする\]**  
 ネイティブ コードのデバッグをサポートするかどうかを指定します。  COM オブジェクトを呼び出すか、プロジェクトを呼び出すネイティブ コードで記述されたカスタム プログラムを起動している場合は、このチェック ボックスをオンにすると、ネイティブ コードをデバッグする必要があります。  アンマネージ コードのデバッグを無効にする場合はオフにします。  既定では、このチェック ボックスはオフです。  
  
 **\[SQL Server デバッグを有効にする\]**  
 このチェック ボックスをオンまたは、Visual Basic アプリケーションから SQL プロシージャのデバッグを有効または無効にする場合はオフにします。  既定では、このチェック ボックスはオフです。  
  
 **\[Visual Studio ホスティング プロセスを有効にする\]**  
 Visual Studio ホスト プロセスを有効にするには、このチェック ボックスをオンにします。  既定では、このチェック ボックスはオンです。  詳細については、「[ホスト プロセス \(vshost.exe\)](../../ide/hosting-process-vshost-exe.md)」を参照してください。  
  
 セキュリティ ゾーンでのデバッグ、[\[セキュリティの詳細設定\] ダイアログ ボックス](../Topic/Advanced%20Security%20Settings%20Dialog%20Box.md)このオプションと **\[選択されたアクセス許可セットでこのアプリケーションをデバッグする\]** を有効にする必要があります。  
  
## 参照  
 [Visual Studio でのデバッグ](../../debugger/debugging-in-visual-studio.md)   
 [C\# デバッグ構成のプロジェクト設定](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Managing Debugging Properties](http://msdn.microsoft.com/ja-jp/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [方法 : アクセス許可が制限された ClickOnce アプリケーションをデバッグする](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [方法 : 構成を作成および編集する](../../ide/how-to-create-and-edit-configurations.md)