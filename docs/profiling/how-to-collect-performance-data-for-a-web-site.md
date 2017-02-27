---
title: "方法: Web サイトのパフォーマンス データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.url.url"
  - "vsperf.chooseurl"
  - "vs.performance.wizard.asppage"
  - "vsperf.url.ok"
  - "vsperf.url.cancel"
helpviewer_keywords: 
  - "プロファイリング ツール、プロファイリング (ASP.NET を)"
  - "Web サイト、パフォーマンス プロファイリング"
  - "ASP.NET、パフォーマンス プロファイリング"
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 33
---
# 方法: Web サイトのパフォーマンス データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**パフォーマンス ウィザード**を使用して、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションのパフォーマンス データを収集できます。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で開かれた Web アプリケーションをプロファイリングすることも、ローカル コンピューターに置かれ、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE で開かれていない [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web サイトをプロファイリングすることもできます。  
  
> [!NOTE]
>  **パフォーマンス ウィザード**を使用して、階層の相互作用\(TIP\) データ、JScript パフォーマンス データ、または両方を追加してプロファイル データを収集することができます。 TIP オプションは、サーバー側のプロセスからデータを収集します。 JScript プロファイリングは、ローカルまたはリモートの Web サイトで実行されているスクリプトからデータを収集します。 ほとんどの場合、1 つのオプションのみを選択する必要があります。  
  
 管理者が使用可能にしたユーザー アクセス許可の設定に応じて、個々のユーザーは、ASP.NET プロセスをホストしているコンピューター上でプロファイラー セッションを作成するためのセキュリティ アクセス許可を持っている場合もあれば持っていない場合もあります。 次の例では、考えられるユーザーごとの違いについて説明します。  
  
-   管理者がドライバーとサービスが起動するように設定しているときには、一部のユーザーが高度なプロファイリング機能にアクセスできることがあります。  
  
-   ドメイン ユーザーはサンプルのプロファイリングにのみアクセスできる場合があります。  
  
-   一部のユーザーが他のすべてのユーザーに対してプロファイリングへのアクセスを拒否することがあります。  
  
 詳細については、「[プロファイルと Windows Vista のセキュリティ](../profiling/profiling-and-windows-vista-security.md)」および [VSPerfCmd](../profiling/vsperfcmd.md) ADMIN オプションを参照してください。  
  
### Web サイト プロジェクトをプロファイリングする  
  
1.  [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] または [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] で [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web プロジェクト開きます。  
  
2.  **\[分析\]** メニューの **\[パフォーマンス ウィザードの起動\]** をクリックします。  
  
3.  ウィザードの最初のページで、プロファイル方法を選択し、**\[次へ\]** をクリックします。 プロファイル方法の詳細については、「[プロファイル方法について](../profiling/understanding-performance-collection-methods.md)」を参照してください。 同時実行ビジュアライザーのプロファイル方法は、Web アプリケーションでは使用できません。  
  
4.  **\[プロファイル対象のアプリケーションを選択してください\]** ドロップダウン リストで、現在のプロジェクトが選択されていることを確認し、**\[次へ\]** をクリックします。  
  
5.  ウィザードの 3 番目のページで、階層相互作用プロファイリング \(TIP\) データ、Web ページで実行されている JavaScript からのデータ、またはその両方の追加を選択できます。  
  
    -   階層の相互作用を収集するには、**\[階層の相互作用のプロファイルを有効にする\]** チェック ボックスをオンにします。  
  
    -   Web ページで実行されている JavaScript からデータを収集するには、**\[JavaScript のプロファイル\]** チェック ボックスをオンにします。  
  
6.  **\[次へ\]** をクリックします。  
  
7.  ウィザードの 4 番目のページで、**\[完了\]** をクリックします。  
  
8.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションのパフォーマンス セッションが作成され、ブラウザーで Web サイトが起動します。 プロファイリングする機能を実行してからブラウザーを閉じます。  
  
     プロファイラーで、データ ファイルが生成され、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] メイン ウィンドウにデータの概要ビューが表示されます。  
  
### Visual Studio でプロジェクトを開かずに Web サイトをプロファイリングする  
  
1.  [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] または [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] を開きます。  
  
2.  **\[分析\]** メニューの **\[パフォーマンス ウィザードの起動\]** をクリックします。  
  
3.  ウィザードの最初のページで、プロファイル方法を選択し、**\[次へ\]** をクリックします。 詳細については、「[プロファイル方法について](../profiling/understanding-performance-collection-methods.md)」を参照してください。  
  
4.  ウィザードの 2 番目のページで、**\[ASP.NET または JavaScript アプリケーションのプロファイル\]** オプションを選択し、**\[次へ\]** をクリックします。  
  
5.  ウィザードの 3 番目のページの **\[Web アプリケーションを実行する URL またはパス\]** ボックスで、アプリケーションのホーム ページの URL を入力し、**\[次へ\]** をクリックします。  
  
    -   サーバー \(IIS\) ベースのWeb サイトの場合は、**http:\/\/localhost\/MySite\/default.aspx** のような URL を入力します。 これにより、ローカル コンピューターの MySite のアプリケーション ルートで [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションがプロファイリングされ、そのサイトの default.aspx ページが Internet Explorer で起動されて、セッションが開始されます。  
  
    -   ファイル ベースの Web サイトの場合は、file\/\/\/**c:\\WebSites\\MySite\\default.aspx** のようなパスを入力します。 これにより、c:\\webSites\\MySite に置かれている [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションがプロファイリングされ、http:\/\/localhost:nnnn\/MySite\/default.aspx ページが Internet Explorer で起動されて、セッションが開始されます。  
  
    -   外部サイトで JavaScript データを収集する場合は、http:\/\/www.contoso.com のような URL を入力します。  
  
     詳細については、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ターゲット バイナリのプロパティ ページを参照してください。  
  
6.  ウィザードの 3 番目のページで、階層相互作用プロファイリング \(TIP\) データ、Web ページで実行されている JavaScript からのデータ、またはその両方の追加を選択できます。  
  
    -   階層の相互作用を収集するには、**\[階層の相互作用のプロファイルを有効にする\]** チェック ボックスをオンにします。  
  
    -   Web ページで実行されている JavaScript からデータを収集するには、**\[JavaScript のプロファイル\]** チェック ボックスをオンにします。  
  
7.  **\[次へ\]** をクリックします。  
  
8.  ウィザードの 4 番目のページで、**\[完了\]** をクリックします。  
  
9. ASP.NET アプリケーションのパフォーマンス セッションが作成され、ブラウザーで Web サイトが起動します。 プロファイリングする機能を実行してからブラウザーを閉じます。  
  
     プロファイラーで、データ ファイルが生成され、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] メイン ウィンドウにデータの概要ビューが表示されます。  
  
## 参照  
 [概要](../profiling/overviews-performance-tools.md)   
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [インストルメンテーション データ値について](../profiling/understanding-instrumentation-data-values.md)   
 [サンプリング データ値について](../profiling/understanding-sampling-data-values.md)