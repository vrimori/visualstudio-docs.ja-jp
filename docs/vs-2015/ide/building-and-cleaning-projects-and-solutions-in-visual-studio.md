---
title: クリーンなプロジェクトのソリューションを構築します。
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05e8d13454ab9698ae855f1e937e85eb287a3a35
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057640"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの手順を使用して、ソリューション内のプロジェクトまたはプロジェクト項目のすべてまたは一部をビルド、リビルド、またはクリーンを行うことができます。 ステップ バイ ステップ チュートリアルについては、次を参照してください。[チュートリアル。アプリケーションをビルドする](../ide/walkthrough-building-an-application.md)します。

> [!NOTE]
>  ご使用の Visual Studio エディションの UI は、アクティブな設定によって、このトピックで説明する内容とは異なる場合があります。 設定を変更するには、**[ツール]** メニューを開き、**[設定のインポートとエクスポート]** を選択します。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。

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

2.  メニュー バーで、**[ビルド]** を選択してから、[_プロジェクト名_の**ビルド**] または [**プロジェクト名**の_リビルド_] を選択します。

    -   [_プロジェクト名_の**ビルド**] を選択すると、最新のビルド以降に変更されたプロジェクト コンポーネントのみがビルドされます。

    -   [_プロジェクト名_の**リビルド**] を選択すると、プロジェクトが "クリーン" されてから、プロジェクト ファイルとすべてのプロジェクト コンポーネントがビルドされます。

### <a name="to-build-only-the-startup-project-and-its-dependencies"></a>スタートアップ プロジェクトとその依存関係のみをビルドするには

1. メニュー バーの **[ツール]**、 **[オプション]** の順にクリックします。

2. **[オプション]** ダイアログ ボックスで、**[プロジェクトおよびソリューション]** ノードを展開してから、**[ビルド/実行]** ページを選択します。

    **[ビルド/実行] ([オプション] ダイアログ ボックス - [プロジェクトおよびソリューション]**) が開きます。

3. **[実行時に、スタートアップ プロジェクトおよび依存関係のみをビルドする]** チェック ボックスをオンにします。

    このチェック ボックスをオンにすると、以下のいずれかの手順を実行したときに、現在のスタートアップ プロジェクトとその依存関係のみがビルドされます。

   - メニュー バーで、**[デバッグ]**、**[開始]** (F5 キー) の順に選択します。

   - メニュー バーで、**[ビルド]**、**[ソリューションのビルド]** (Ctrl + Shift + B キー) の順に選択します。

     このチェック ボックスをオフにすると、上記のいずれかのコマンドを実行した場合に、すべてのプロジェクト、依存関係、およびソリューション ファイルがビルドされます。 既定では、このチェック ボックスはオフになっています。

### <a name="to-build-only-the-selected-visual-c-project"></a>選択した Visual C++ プロジェクトのみをビルドするには

1. [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] プロジェクトを選択してから、メニュー バーで **[ビルド]**、**[プロジェクトのみ]** の順に選択し、以下のコマンドのいずれかを選択します。

   - *プロジェクト名***のみをビルド**

   - *プロジェクト名***のみをリビルド**

   - *プロジェクト名***のみ消去**

   - *プロジェクト名***へのみリンク**

     これらのコマンドは、選択されている [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] プロジェクトにのみ適用されます。プロジェクトの依存関係やソリューション ファイルのビルド、リビルド、クリーン、リンクは行われません。 使用している [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] のバージョンに応じて、**[プロジェクトのみ]** のサブメニューに他のコマンドが含まれる場合があります。

### <a name="to-compile-multiple-c-project-items"></a>複数の C++ プロジェクト項目をコンパイルするには

1.  **ソリューション エクスプローラー**で、有効なコンパイル アクションのある複数のファイルを選択し、それらのファイルのいずれかのショートカット メニューを開いてから **[コンパイル]** を選択します。

     ファイルに依存関係がある場合、依存関係の順序でコンパイルされます。 コンパイル時に使用できないプリコンパイル済みヘッダーがファイルで必要な場合、コンパイル操作は失敗します。 コンパイル操作では、現在のアクティブなソリューション構成が使用されます。

### <a name="to-stop-a-build"></a>ビルドを停止するには

1.  次のいずれかの操作を実行します。

    -   メニュー バーで、**[ビルド]**、**[キャンセル]** の順に選択します。

    -   Ctrl + Break キーを選択します。

## <a name="see-also"></a>参照
 [方法: ビルド ログ ファイルの構成を表示、保存、および](../ide/how-to-view-save-and-configure-build-log-files.md)[ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)[のコンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)[ビルド構成について](../ide/understanding-build-configurations.md) [デバッグおよびリリース プロジェクト構成](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) [C/C++ ビルドのリファレンス](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)[ソリューションとプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)
