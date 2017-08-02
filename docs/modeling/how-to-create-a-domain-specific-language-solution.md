---
title: "方法: ドメイン固有言語ソリューションを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-domain-specific-language-solution"></a>方法: ドメイン固有言語ソリューションを作成する
ドメイン固有言語 (DSL) を使用して作成する特殊な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションです。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 この手順を開始する前に、これらのコンポーネントを最初にインストールする必要があります。  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成します。  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成するには  
  
1.  DSL のウィザードを起動します。  
  
    1.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
    2.  **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
    3.  [**プロジェクトの種類**、展開、**その他のプロジェクトの種類**] ノードをクリック**拡張**します。  
  
    4.  クリックして**ドメイン固有言語デザイナー**します。  
  
    5.  **名前**ボックスに、ソリューションの名前を入力します。 **[OK]** をクリックします。  
  
         **ドメイン固有言語デザイナー ウィザード**が表示されます。  
  
        > [!NOTE]
        >  可能であれば、入力した名前は、コードが生成される可能性がありますので、有効な Visual c# の識別子をする必要があります。  
  
     ![DSL ダイアログの作成](~/modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  DSL テンプレートを選択します。  
  
     **ドメイン固有言語のオプションを選択して**などのソリューション テンプレートの選択 ページで、**最小言語**です。 DSL を作成する次のようなテンプレートを選択します。  
  
     ソリューション テンプレートの詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートを選択する](../modeling/choosing-a-domain-specific-language-solution-template.md)です。  
  
3.  ファイル名拡張子を入力して、**ファイル拡張子**ページです。 自分のコンピューターで一意である必要がありする任意のコンピューターでは、DSL をインストールします。 メッセージが表示**アプリケーションまたは Visual Studio エディターにこの拡張機能使用しない**します。  
  
    -   完全にインストールされていない以前の実験的な Dsl のファイル名拡張子を使用した、消去する方法もそれらアウトを使用して、**実験用インスタンスをリセット**は記載されているツール、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK メニュー。  
  
    -   他[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ファイルの拡張子を使用する拡張機能は完全にコンピューターにインストールされた、アンインストールすることを検討してください。 **ツール** メニューのをクリックして**拡張機能マネージャー**します。  
  
4.  検査、および必要に応じて調整、ウィザードの残りのページ内のフィールドです。 設定に満足したら、クリックして**完了**します。 設定の詳細については、次を参照してください。 [DSL デザイナーのウィザード ページ](#settings)します。  
  
     ウィザードと呼ばれる&2; つのプロジェクトが含まれるソリューションを作成する**Dsl**と**DslPackage**します。  
  
    > [!NOTE]
    >  信頼されていないソースからのテキスト テンプレートを実行するには、をクリックしないを通知するメッセージが表示される場合**OK**します。 このメッセージを再び表示されないように設定できます。  
  
##  <a name="a-namesettingsa-the-dsl-designer-wizard-pages"></a><a name="settings"></a>DSL デザイナーのウィザード ページ  
 既定値から変更されていないフィールドのいくつかのままにすることができます。 ただし、ファイル拡張子 フィールドを設定することを確認します。  
  
### <a name="solution-settings-page"></a>ソリューションの設定 ページ  
 **どのテンプレートを基に、ドメイン固有言語か?**  
 DSL を作成する次のようなテンプレートを選択します。 別のテンプレートは、便利な開始点を提供します。 ソリューション テンプレートを選択すると、ウィザードには、説明が表示されます。 ソリューション テンプレートの詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートを選択する](../modeling/choosing-a-domain-specific-language-solution-template.md)です。  
  
 **ドメイン固有言語の名前には、目的をください。**  
 既定値は、ソリューション名です。 コードは、この値から生成されます。 C# クラス名として有効な場合があります。  
  
### <a name="file-extension-page"></a>ファイル拡張子 ページ  
 **どのような拡張機能をモデル化ファイルで使用してでしょうか。**  
 新しいファイル拡張子を入力します。  
  
 このファイルの拡張子は既に登録されていないこと、このコンピューターで使用する次のように確認します。  
  
 下を見て**この拡張機能を処理する他のツールやアプリケーションが登録されて**します。 メッセージを表示する場合**アプリケーションまたは Visual Studio エディターにこの拡張機能使用しない**、このファイルの拡張子を使用することができます。  
  
 ツールまたはパッケージの一覧を表示する場合は、次のいずれかを行う必要があります。  
  
-   別のファイル拡張子を入力します。  
  
     \- または  
  
-   リセット、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]実験用インスタンス。 これで構築したことが、Dsl のすべてが登録を解除します。 **開始** メニューのをクリックして**すべてのプログラム**、 **Microsoft Visual Studio 2010 SDK**、**ツール**、し**Microsoft Visual Studio 2010 実験用インスタンスをリセット**します。 もう一度使用する他の Dsl を再構築することができます。  
  
     \- または  
  
-   場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ファイルの拡張子を使用する拡張機能は完全にコンピューターにインストールされた、アンインストールします。 **ツール** メニューのをクリックして**拡張機能マネージャー**します。  
  
### <a name="product-settings-page"></a>製品の設定 ページ  
 **新しいドメイン固有言語が含まれている製品の名前とは何ですか。**  
 既定値は、DSL の名前です。  
  
 この値は、このファイル拡張子を持つファイルを定義する Windows エクスプ ローラー (またはファイル エクスプ ローラー) で使用されます。  
  
 **属している製品の会社の名前とは何ですか。**  
 会社名。  
  
 この値は、DSL パッケージの AssemblyInfo プロパティに組み込まれます。  
  
 **このソリューション内のプロジェクトのルート名前空間とは何ですか。**  
 既定値は、会社から構成される名前と製品の名前。  
  
### <a name="signing-page"></a>[署名] ページ  
 **厳密な名前キー ファイルを作成します。**  
 既定のオプションでは、DSL アセンブリの署名に新しいキーを作成します。  
  
 **既存の厳密な名前キーを使用します。**  
 別のアセンブリと、DSL を統合する場合は、このオプションを使用します。  
  
 厳密な名前付けの詳細については、次を参照してください。[の作成と using strong-named Assemblies](http://go.microsoft.com/fwlink/?LinkId=186073)します。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)   
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

