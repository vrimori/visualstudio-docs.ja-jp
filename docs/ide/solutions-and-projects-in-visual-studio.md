---
title: "Visual Studio のソリューションおよびプロジェクト | Microsoft ドキュメント"
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio のソリューションおよびプロジェクト
Visual Studio でアプリ、Web サイト、プラグインなどを作成するときは、"*プロジェクト*" から始めます。 論理的には、実行可能プログラムや Web サイトにコンパイルされるか、またはコンパイルを実行するために必要とされる、すべてのソース コード ファイル、アイコン、イメージ、データ ファイル、およびその他の要素がプロジェクトに含まれています。 プロジェクトには、プログラムが通信するさまざまなサービスまたはコンポーネントで必要になる可能性がある、すべてのコンパイラ設定とその他の構成ファイルも含まれています。  

> [!NOTE]
>  必要ない場合は、ソリューションまたはプロジェクトを使用する必要はありません。 Visual Studio にファイルを開くだけでし、コードの編集を開始できます。 詳しくは、「[プロジェクトまたはソリューションを使用せずに Visual Studio でコードを開発する](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)」をご覧ください。  

プロジェクト ファイル (.vbproj、.csproj、.vcxproj) は、仮想フォルダー階層と、プロジェクト内のすべての項目へのパスを定義する XML ファイルです。 これにはビルドの設定も含まれます。 プロジェクト ファイルの内容を表示するには、ソリューション エクスプローラーでプロジェクト名を選択し、コンテキスト メニュー (右クリックで表示) から **[プロジェクトのアンロード]** をクリックします。 次に、コンテキスト メニューをもう一度開き、**[編集\<プロジェクト名\>]** を選択します。  

Visual Studio では、プロジェクト ファイルはソリューション エクスプローラーでプロジェクトの内容と設定を表示するために使用されます。 プロジェクトをコンパイルすると、MSBuild エンジンがプロジェクト ファイルを使用して実行可能ファイルを作成します。 他の種類の出力を生成するように、プロジェクトをカスタマイズすることもできます。  

論理的にはファイル システム上、プロジェクトは *ソリューション*内に格納されています。ソリューションには、1 つ以上の関連するプロジェクトと共に、ビルド情報、Visual Studio ウィンドウの設定、および特定のプロジェクトに関連付けられていないその他のファイルが含まれる場合があります。 ソリューションは独自形式を持つテキスト ファイル (.sln) で記述され、普通は手動での編集を意図していません。  

ソリューションには、プロジェクトで作業している各ユーザーの設定、ユーザー設定、および構成情報を格納する *.suo* ファイルが関連付けられています。  

 次の図は、プロジェクトとソリューションの関係、およびそれらに論理的に含まれる項目を示しています。  

 ![Visual Studio のプロジェクトとソリューション](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>プロジェクトの新規作成  
 新しいプロジェクトを作成する最も簡単な方法は、プロジェクト テンプレートから始めることです。これらのテンプレートは、特定のプログラミング言語で特定の種類のアプリケーションや Web サイトを作成し始めるのに必要な、生成済みのコード ファイル、構成ファイル、資産、および設定の基本セットで構成されます。 これらのテンプレートは、**[ファイル]**、**[新規作成]**、**[プロジェクト]** または **[ファイル]**、**[新規作成]**、**[Web サイト]** を選択して **[新しいプロジェクト]** または **[新しい Web サイト]** ダイアログ ボックスに移動したときに表示されます。 詳細については、「[ソリューションとプロジェクトの作成](../ide/creating-solutions-and-projects.md)」を参照してください。  

カスタム プロジェクトや項目テンプレートを作成することもできます。 詳細については、「[Creating Project and Item Templates](../ide/creating-project-and-item-templates.md)」 (プロジェクトと項目テンプレートの作成) をご覧ください。  

## <a name="managing-projects-in-solution-explorer"></a>ソリューション エクスプローラーでのプロジェクトの管理  
 新しいプロジェクトを作成した後は、 **ソリューション エクスプローラー** を使用して、プロジェクト、ソリューション、およびそれらの関連項目を表示して管理します。 次の図に、2 つのプロジェクトを含む C# ソリューションが表示されたソリューション エクスプローラーを示します。  

 ![ソリューション エクスプ ローラー](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>このセクションの内容  

-   [ソリューションとプロジェクトの作成](../ide/creating-solutions-and-projects.md)  

-   [プロジェクト項目の追加と削除](../ide/adding-and-removing-project-items.md)  

-   [プロジェクトおよびソリューションのプロパティの管理](../ide/managing-project-and-solution-properties.md)  

-   [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)  

-   [アプリケーション プロパティ](../ide/application-properties.md)  

-   [アセンブリおよびマニフェストへの署名の管理](../ide/managing-assembly-and-manifest-signing.md)  

-   [方法 : アプリケーション アイコンを指定する (Visual Basic、C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [対象となる特定の .NET Framework バージョンの指定](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>関連項目  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
