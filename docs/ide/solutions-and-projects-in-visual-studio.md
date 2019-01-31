---
title: ソリューションとプロジェクト
ms.date: 10/05/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4f2d68920edad0b2c9e21c0897130b286180689
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55032974"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio のソリューションおよびプロジェクト

この記事では、Visual Studio の*プロジェクト*と*ソリューション*の概念について説明します。 また、新しいプロジェクトの作成方法と、**ソリューション エクスプローラー** ツール ウィンドウについても簡単に説明します。

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、[Visual Studio for Mac のプロジェクトおよびソリューション](/visualstudio/mac/projects-and-solutions)に関するページを参照してください。

## <a name="projects"></a>プロジェクト

Visual Studio でアプリ、Web サイト、プラグインなどを作成するときは、"*プロジェクト*" から始めます。 論理的には、実行可能ファイル、ライブラリ、または Web サイトにコンパイルされる、すべてのソース コード ファイル、アイコン、イメージ、データ ファイルなどがプロジェクトに含まれています。 また、プロジェクトには、プログラムが通信するさまざまなサービスまたはコンポーネントで必要になる可能性がある、コンパイラ設定とその他の構成ファイルも含まれています。

> [!NOTE]
> Visual Studio でソリューションまたはプロジェクトを使用して、コードの編集、ビルド、デバッグを行う必要はありません。 単に Visual Studio でソース ファイルを含むフォルダーを開いて編集を開始できます。 詳細については、「[プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)」を参照してください。

プロジェクトは、*.vbproj*、*.csproj*、*.vcxproj* などの拡張子を持つ XML ファイルで定義されます。 このファイルには、仮想フォルダー階層と、プロジェクト内のすべての項目へのパスが含まれます。 これにはビルドの設定も含まれます。

> [!TIP]
> Visual Studio でプロジェクト ファイルの内容を表示するには、まず、**ソリューション エクスプローラー**でプロジェクト名を選択し、コンテキストまたは右クリック メニューから **[プロジェクトのアンロード]** を選択して、プロジェクトをアンロードします。 次に、コンテキスト メニューをもう一度開き、**[編集\<プロジェクト名\>]** を選択します。

Visual Studio では、プロジェクト ファイルは**ソリューション エクスプローラー**でプロジェクトの内容と設定を表示するために使用されます。 プロジェクトをコンパイルすると、MSBuild エンジンがプロジェクト ファイルを使用して実行可能ファイルを作成します。 他の種類の出力を生成するように、プロジェクトをカスタマイズすることもできます。

## <a name="solutions"></a>ソリューション

プロジェクトは*ソリューション* 内に含まれます。 ソリューションは、その名前にもかかわらず、"答え" ではありません。 1 つ以上の関連するプロジェクト、およびビルド情報、Visual Studio ウィンドウの設定、特定のプロジェクトに関連付けられていないその他のファイルに対するコンテナーに過ぎません。 ソリューションは独自の形式を持つテキスト ファイル (拡張子 *.sln*) で記述され、手動での編集は想定されていません。

Visual Studio では、ソリューションの設定を格納するために、2 種類のファイル (*.sln* および *.suo*) を使用します。

|拡張子|name|説明|
|---------------|----------|-----------------|
|.sln|Visual Studio ソリューション|ソリューション内のプロジェクト、プロジェクト項目、およびソリューション項目を整理します。|
|.suo|ソリューション ユーザー オプション|ユーザー レベルの設定やブレークポイントなどのカスタマイズを格納します。|

## <a name="create-new-projects"></a>プロジェクトの新規作成

新しいプロジェクトを作成する最も簡単な方法は、特定の種類のアプリケーションまたは Web サイトのプロジェクト テンプレートから始めることです。 プロジェクト テンプレートは、生成済みのコード ファイル、構成ファイル、資産、設定の基本セットで構成されます。 これらのテンプレートは、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択して **[新しいプロジェクト]** ダイアログ ボックスに移動したときに表示されます。 詳細については、[ソリューションとプロジェクトの作成](../ide/creating-solutions-and-projects.md)に関するページを参照してください。

カスタム プロジェクトや項目テンプレートを作成することもできます。 詳細については、[プロジェクト テンプレートと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)に関するページをご覧ください。

## <a name="manage-projects-in-solution-explorer"></a>ソリューション エクスプローラーでプロジェクトを管理する

新しいプロジェクトを作成した後は、**ソリューション エクスプローラー**を使用して、プロジェクトとソリューション、およびそれらの関連項目を表示して管理できます。 次の図に、2 つのプロジェクトを含む C# ソリューションが表示された**ソリューション エクスプローラー**を示します。

![ソリューション エクスプローラー](../ide/media/vs2015_solution_explorer.png)

## <a name="see-also"></a>関連項目

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [プロジェクトとソリューション (Visual Studio for Mac)](/visualstudio/mac/projects-and-solutions)
- [プロジェクト アイテムの追加と削除 (Visual Studio for Mac)](/visualstudio/mac/add-and-remove-project-items)