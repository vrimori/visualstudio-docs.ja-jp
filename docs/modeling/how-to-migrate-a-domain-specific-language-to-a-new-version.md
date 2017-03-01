---
title: "方法: ドメイン固有言語の新しいバージョンへの移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>方法: ドメイン固有言語を新バージョンに移行する
定義するドメイン固有言語を使用するプロジェクトを移行する[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]のバージョンから[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]使用して配布されている[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]します。  
  
 一部として移行ツールが提供される[!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]します。 このツールに変換[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクトおよびソリューションを使用するか DSL Tools を定義します。  
  
 移行ツールを明示的に実行する必要があります: が起動していない自動的にソリューションを開くと[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 ツールと詳細なガイダンスのドキュメントは、このパスにあることができます。  
  
 **% プログラム Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>DSL プロジェクトを移行する前に  
 移行ツールは、変更[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト ファイル (**.csproj**) とソリューション ファイル (**.sln**)。  
  
#### <a name="to-prepare-projects-for-migration"></a>移行するには、プロジェクトを準備します。  
  
-   確認、 **.csproj**と**.sln**ファイルを書き込むことができます。 ソース管理下にある場合は、チェック アウトすることを確認します。  
  
-   移行する予定のフォルダーのコピーを作成します。  
  
## <a name="migrating-a-collection-of-projects"></a>プロジェクトのコレクションを移行します。  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL プロジェクトおよびソリューションを Visual Studio 2010 に移行するには  
  
1.  DSL の移行ツールを起動します。  
  
    -   コマンド プロンプトからツールを起動または Windows エクスプ ローラー (またはファイル エクスプ ローラー) では、ツールをダブルクリックすることができます。 このツールは、この場所には。  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  ソリューションおよび変換するプロジェクトを含むフォルダーを選択します。  
  
    -   ツールの上部にあるボックスにパスを入力またはクリックして**参照**します。  
  
     移行ツールには、定義または Dsl を使用するプロジェクトのツリーが表示されます。 ツリーには使用するすべてのプロジェクトが含まれています、 **Microsoft.VisualStudio.Modeling.Sdk**または**TextTemplating**アセンブリ。  
  
3.  プロジェクトのツリーを確認し、変換したくないプロジェクトをオフにします。  
  
    -   プロジェクトまたはツールが加える変更の一覧を表示するソリューションを選択します。  
  
        > [!NOTE]
        >  フォルダー名の横に表示されるチェック ボックスは、影響を与えるありません。 プロジェクトおよびソリューションを検査するフォルダーを展開する必要があります。  
  
4.  プロジェクトに変換します。  
  
    1.  クリックして**変換**します。  
  
         各プロジェクト ファイルが変換される前のコピー*プロジェクト***.csproj**として保存*プロジェクト***vs2008.csproj。**  
  
         それぞれのコピー*ソリューション***.sln**として保存*ソリューション***vs2008.sln。**  
  
    2.  報告されるすべての障害が発生した変換を調査します。  
  
         テキスト ウィンドウにエラーが報告されます。 さらに、ツリー ビューでは、変換に失敗した各ノードに赤いフラグが表示されます。 そのエラーに関する詳細を取得するノードをクリックすることができます。  
  
5.  **すべてのテンプレートの変換**ソリューションを正常に格納しているプロジェクトに変換します。  
  
    1.  ソリューションを開きます。  
  
    2.  クリックして、**すべてのテンプレートの変換**ソリューション エクスプ ローラーのヘッダーにボタンをクリックします。  
  
        > [!NOTE]
        >  この手順を不要な作成できます。 詳細については、次を参照してください。[すべてのテンプレートの変換を自動化する方法](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)します。  
  
6.  変換後のプロジェクトでカスタム コードを更新します。  
  
    -   プロジェクトをビルドし、すべてのエラーを調査しようとします。  
  
    -   デザイナーをテストします。  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>関連項目  
 [関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)


