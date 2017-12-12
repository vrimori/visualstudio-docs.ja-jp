---
title: "Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2e66af6d2d38685bdd905b7991c6e8f782e4f696
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2017
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン
このトピックの手順を使用して、ソリューション内のプロジェクトまたはプロジェクト項目のすべてまたは一部をビルド、リビルド、またはクリーンを行うことができます。 ステップ バイ ステップ チュートリアルについては、「[チュートリアル: アプリケーションをビルドする](../ide/walkthrough-building-an-application.md)」を参照してください。  
  
> [!NOTE]
> ご使用の Visual Studio エディションの UI は、アクティブな設定によって、このトピックで説明する内容とは異なる場合があります。 設定を、たとえば、**[全般]** や **[Visual C++]** に変更するには、**[ツール]**、**[設定のインポートとエクスポート]**、**[すべての設定をリセット]** の順に選択します。
  
### <a name="to-build-rebuild-or-clean-an-entire-solution"></a>ソリューション全体のビルド、リビルド、またはクリーン  
  
1.  **ソリューション エクスプローラー**で、ソリューションを選択するか開きます。  
  
2.  メニュー バーで、**[ビルド]** を選択し、次のコマンドのいずれかを選択します。  
  
    -   **[ビルド]** または **[ソリューションのビルド]** を選択すると、最新のビルド以降に変更されたプロジェクト ファイルとコンポーネントのみがコンパイルされます。  
  
        > [!NOTE]
        >  ソリューションに複数のプロジェクトが含まれている場合は、**[ビルド]** コマンドが **[ソリューションのビルド]** になります。  
  
    -   **[ソリューションのビルド]** を選択すると、ソリューションが "クリーン" されてから、すべてのプロジェクト ファイルとコンポーネントがビルドされます。  
  
    -   **[ソリューションのクリーン]** を選択すると、中間ファイルと出力ファイルがすべて削除されます。 その後、プロジェクト ファイルとコンポーネント ファイルのみを残して、中間ファイルと出力ファイルの新しいインスタンスをビルドできます。  
  
### <a name="to-build-or-rebuild-a-single-project"></a>1 つのプロジェクトをビルドまたはリビルドするには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトを選択するか開きます。  
  
2.  メニュー バーで、**[ビルド]** を選択してから、[*プロジェクト名*の**ビルド**] または [**プロジェクト名**の*リビルド*] を選択します。  
  
    -   [*プロジェクト名*の**ビルド**] を選択すると、最新のビルド以降に変更されたプロジェクト コンポーネントのみがビルドされます。  
  
    -   [*プロジェクト名*の**リビルド**] を選択すると、プロジェクトが "クリーン" されてから、プロジェクト ファイルとすべてのプロジェクト コンポーネントがビルドされます。  
  
### <a name="to-build-only-the-startup-project-and-its-dependencies"></a>スタートアップ プロジェクトとその依存関係のみをビルドするには  
  
1.  メニュー バーの **[ツール]**、 **[オプション]**の順にクリックします。  
  
2.  **[オプション]** ダイアログ ボックスで、**[プロジェクトおよびソリューション]** ノードを展開してから、**[ビルド/実行]** ページを選択します。  
  
     **[ビルド/実行] ([オプション] ダイアログ ボックス - [プロジェクトおよびソリューション]**) が開きます。  
  
3.  **[実行時に、スタートアップ プロジェクトおよび依存関係のみをビルドする]** チェック ボックスをオンにします。  
  
     このチェック ボックスをオンにすると、以下のいずれかの手順を実行したときに、現在のスタートアップ プロジェクトとその依存関係のみがビルドされます。  
  
    -   メニュー バーで、**[デバッグ]**、**[開始]** (F5 キー) の順に選択します。  
  
    -   メニュー バーで、**[ビルド]**、**[ソリューションのビルド]** (Ctrl + Shift + B キー) の順に選択します。  
  
    このチェック ボックスをオフにすると、上記のいずれかのコマンドを実行した場合に、すべてのプロジェクト、依存関係、およびソリューション ファイルがビルドされます。 既定では、このチェック ボックスはオフになっています。  
  
### <a name="to-build-only-the-selected-visual-c-project"></a>選択した Visual C++ プロジェクトのみをビルドするには  
  
1.  [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] プロジェクトを選択してから、メニュー バーで **[ビルド]**、**[プロジェクトのみ]** の順に選択し、以下のコマンドのいずれかを選択します。  
  
    -   *プロジェクト名***のみをビルド**  
  
    -   *プロジェクト名***のみをリビルド**  
  
    -   *プロジェクト名***のみ消去**  
  
    -   *プロジェクト名***へのみリンク**  
  
    これらのコマンドは、選択されている [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] プロジェクトにのみ適用されます。プロジェクトの依存関係やソリューション ファイルのビルド、リビルド、クリーン、リンクは行われません。 使用している [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンに応じて、**[プロジェクトのみ]** のサブメニューに他のコマンドが含まれる場合があります。  
  
### <a name="to-compile-multiple-c-project-items"></a>複数の C++ プロジェクト項目をコンパイルするには  
  
1.  **ソリューション エクスプローラー**で、有効なコンパイル アクションのある複数のファイルを選択し、それらのファイルのいずれかのショートカット メニューを開いてから **[コンパイル]** を選択します。  
  
    ファイルに依存関係がある場合、依存関係の順序でコンパイルされます。 コンパイル時に使用できないプリコンパイル済みヘッダーがファイルで必要な場合、コンパイル操作は失敗します。 コンパイル操作では、現在のアクティブなソリューション構成が使用されます。  
  
### <a name="to-stop-a-build"></a>ビルドを停止するには  
  
1.  次のいずれかの操作を実行します。  
  
    -   メニュー バーで、**[ビルド]**、**[キャンセル]** の順に選択します。  
  
    -   Ctrl + Break キーを選択します。  
  
## <a name="see-also"></a>関連項目
[方法: ビルド ログ ファイルを表示、保存、および構成する](../ide/how-to-view-save-and-configure-build-log-files.md)   
[ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)   
[コードのコンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)   
[ビルド構成について](../ide/understanding-build-configurations.md)   
[デバッグ プロジェクト構成およびリリース プロジェクト構成](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)   
[C/C++ ビルドのリファレンス](/cpp/build/reference/c-cpp-building-reference)   
[Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)   
[ソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)