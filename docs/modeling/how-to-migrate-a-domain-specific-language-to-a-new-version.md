---
title: '方法: ドメイン固有言語を新バージョンに移行する'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2f4051f0771d4343ee09593a2e9674fa904a5f85
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953308"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>方法: ドメイン固有言語を新バージョンに移行する
定義し、ドメイン固有言語を使用するプロジェクトを移行する[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]のバージョンから[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]をと共に配布された[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]です。

 移行ツールがの一部として提供される[!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]です。 ツールは変換[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクトおよびソリューションを使用するか DSL ツールを定義します。

 移行ツールを明示的に実行する必要があります: がないが自動的に起動では、ソリューションを開くと[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 ツールとドキュメントの詳細なガイダンスは、このパスに見つかりませんことができます。

 **% プログラム Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>DSL プロジェクトを移行する前に
 移行ツールで変更する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト ファイル (**.csproj**) ファイルとソリューション ファイル (**.sln**)。

#### <a name="to-prepare-projects-for-migration"></a>プロジェクト移行の準備をします。

-   確認、 **.csproj**と **.sln**ファイルを書き込むことができます。 ソース管理下にある場合は、それらがチェック アウトされることを確認します。

-   移行するフォルダーのコピーを作成します。

## <a name="migrating-a-collection-of-projects"></a>プロジェクトのコレクションを移行します。

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL プロジェクトおよびソリューションを Visual Studio 2010 に移行するには

1.  DSL 移行ツールを起動します。

    -   Windows エクスプ ローラー (またはファイル エクスプ ローラー) では、ツールをダブルクリックしてまたはコマンド プロンプトからツールを起動できます。 このツールは、この場所には。

         **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2.  ソリューションおよびプロジェクトに変換することがあるフォルダーを選択します。

    -   このツールの上部にあるボックスにパスを入力するか、をクリックして**参照**です。

     移行ツールには、定義または Dsl を使用するプロジェクトのツリーが表示されます。 ツリーには使用するすべてのプロジェクトが含まれています、 **Microsoft.VisualStudio.Modeling.Sdk**または**TextTemplating**アセンブリ。

3.  プロジェクトのツリーを確認し、変換しないプロジェクトをオフにします。

    -   プロジェクトまたはツールによって、変更の一覧を表示するソリューションを選択します。

        > [!NOTE]
        >  フォルダー名の隣に表示されるチェック ボックスは、影響を与えるありません。 プロジェクトおよびソリューションを検査するフォルダーを展開する必要があります。

4.  プロジェクトを変換します。

    1.  をクリックして**変換**です。

         各プロジェクト ファイルが変換される前のコピー*プロジェクト * * * .csproj** として保存*プロジェクト * * *.vs2008.csproj**

         各コピー*ソリューション * * * .sln** として保存*ソリューション * * *.vs2008.sln**

    2.  報告されるすべての障害が発生した変換を調査します。

         テキスト ウィンドウにエラーが報告されます。 さらに、ツリー ビューでは、変換に失敗した各ノードに赤いフラグを示しています。 そのエラーに関する詳細を取得するノードをクリックすることができます。

5.  **すべてのテンプレートを変換**ソリューションで正常に含むプロジェクトを変換します。

    1.  ソリューションを開きます。

    2.  クリックして、**すべてのテンプレートの変換**ソリューション エクスプ ローラーのヘッダーにボタンをクリックします。

        > [!NOTE]
        >  この手順を不要な作成できます。 詳細については、次を参照してください。[すべてのテンプレートの変換を自動化する方法](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)です。

6.  変換後のプロジェクトでカスタム コードを更新します。

    -   プロジェクトをビルドし、すべてのエラーを調査しようとします。

    -   デザイナーをテストします。


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>関連項目

- [関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)