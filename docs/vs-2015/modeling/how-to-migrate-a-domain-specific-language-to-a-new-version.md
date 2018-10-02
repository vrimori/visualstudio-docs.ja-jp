---
title: '方法: ドメイン固有言語を新しいバージョンに移行する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1d97e0204122e6dfcae89da7b04a0a303a0bd9a4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592711"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>方法: ドメイン固有言語を新バージョンに移行する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ドメイン固有言語を新しいバージョンに移行](https://docs.microsoft.com/visualstudio/modeling/how-to-migrate-a-domain-specific-language-to-a-new-version)します。  
  
ドメイン固有言語を使って定義するプロジェクトを移行する[!INCLUDE[vs2010](../includes/vs2010-md.md)]のバージョンから[!INCLUDE[dsl](../includes/dsl-md.md)]を使用して配布されて[!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)]します。  
  
 一部として移行ツールが提供される[!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]します。 ツールに変換します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクトおよびソリューションを使用して、または DSL Tools を定義します。  
  
 移行ツールを明示的に実行する必要があります: ことがない自動的に起動でソリューションを開くときに[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 ツールおよび詳細なガイダンスのドキュメントは、このパスで見つかんだことができます。  
  
 **% プログラム Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>DSL プロジェクトを移行する前に  
 移行ツールを変更します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト ファイル (**.csproj**) とソリューション ファイル (**.sln**)。  
  
#### <a name="to-prepare-projects-for-migration"></a>移行するには、プロジェクトを準備します。  
  
-   必ず、 **.csproj**と **.sln**ファイルを書き込むことができます。 ソース管理下にある場合は、チェック アウトすることを確認します。  
  
-   移行するフォルダーのコピーを作成します。  
  
## <a name="migrating-a-collection-of-projects"></a>プロジェクトのコレクションを移行します。  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL プロジェクトおよびソリューションを Visual Studio 2010 に移行するには  
  
1.  DSL の移行ツールを起動します。  
  
    -   Windows エクスプ ローラー (またはファイル エクスプ ローラー) ツールをダブルクリックします。 または、コマンド プロンプトからツールを起動できます。 このツールは、この場所には。  
  
         **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  ソリューションおよび変換するプロジェクトを含むフォルダーを選択します。  
  
    -   ツールの上部にあるボックスにパスを入力またはクリックして**参照**します。  
  
     移行ツールには、定義または Dsl を使用するプロジェクトのツリーが表示されます。 ツリーには使用するすべてのプロジェクトが含まれています、 **Microsoft.VisualStudio.Modeling.Sdk**または**TextTemplating**アセンブリ。  
  
3.  プロジェクトのツリーを確認し、変換したくないプロジェクトをオフにします。  
  
    -   プロジェクトまたはツールによって、変更の一覧を表示するソリューションを選択します。  
  
        > [!NOTE]
        >  フォルダー名の横に表示されるチェック ボックスは、影響を与えるありません。 プロジェクトおよびソリューションを検査するフォルダーを展開する必要があります。  
  
4.  プロジェクトに変換します。  
  
    1.  クリックして**変換**します。  
  
         各プロジェクト ファイルが変換される前のコピーを_プロジェクト_**.csproj**として保存されます_プロジェクト_**vs2008.csproj。**  
  
         各コピー_ソリューション_**.sln**として保存されます_ソリューション_**vs2008.sln。**  
  
    2.  報告されるすべての失敗した変換を調査します。  
  
         テキスト ウィンドウにエラーが報告されます。 さらに、ツリー ビューでは、変換に失敗した各ノードに赤いフラグを示しています。 そのエラーの詳細を取得するノードをクリックすることができます。  
  
5.  **すべてのテンプレートの変換**ソリューションで正常に格納しているプロジェクトを変換します。  
  
    1.  ソリューションを開きます。  
  
    2.  をクリックして、**すべてのテンプレートの変換**ソリューション エクスプ ローラーのヘッダーにボタンをクリックします。  
  
        > [!NOTE]
        >  この手順を不要なことできます。 詳細については、次を参照してください。[すべてのテンプレートの変換を自動化する方法](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)します。  
  
6.  変換後のプロジェクトでのカスタム コードを更新します。  
  
    -   プロジェクトをビルドし、すべてのエラーを調査しようとします。  
  
    -   デザイナーをテストします。  
  
## <a name="see-also"></a>関連項目  
 [Visualization and Modeling SDK の新機能](../misc/what-s-new-in-visualization-and-modeling-sdk.md)



