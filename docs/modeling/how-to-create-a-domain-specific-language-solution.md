---
title: '方法: ドメイン固有言語ソリューションを作成する'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: c4851577a62db08e2c759f7140895e15b230ec60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>方法: ドメイン固有言語ソリューションを作成する
ドメイン固有言語 (DSL) を使用して作成する特殊な[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションです。

## <a name="prerequisites"></a>必須コンポーネント
 この手順を開始する前に、これらのコンポーネントをまずインストールする必要があります。

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|Visual Studio Visualization and Modeling SDK||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成します。

#### <a name="to-create-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成するには

1.  DSL ウィザードを起動します。

    1.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

    2.  **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

    3.  [**プロジェクトの種類**、展開、**その他のプロジェクトの種類**] ノードをクリック**Extensibility**です。

    4.  をクリックして**ドメイン固有言語デザイナー**です。

    5.  **名前**ボックスに、ソリューションの名前を入力します。 **[OK]** をクリックします。

         **ドメイン固有言語デザイナー ウィザード**が表示されます。

        > [!NOTE]
        >  可能であれば、コードが生成される可能性がありますので、入力した名前は、有効な Visual c# 識別子をする必要があります。

     ![DSL ダイアログの作成](../modeling/media/create_dsldialog.png "Create_DSLDialog")

2.  DSL テンプレートを選択します。

     **ドメイン固有言語のオプションの選択**などソリューション テンプレートのいずれかの選択 ページで、**最小限言語**します。 作成する DSL には、次のようなテンプレートを選択します。

     ソリューション テンプレートの詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートを選択する](../modeling/choosing-a-domain-specific-language-solution-template.md)です。

3.  ファイル名拡張子を入力、**ファイル拡張子**ページ。 自分のコンピューターで一意である必要があり、DSL をインストールするすべてのコンピューターにします。 メッセージが表示する必要があります**アプリケーションまたは Visual Studio のエディターを使用するこの拡張機能**します。

    -   完全にインストールされていない以前の実験用 Dsl で、ファイル名拡張子を使用している場合ことができますをオフにすることを使用して、**実験用インスタンスをリセット**は含まれているツール、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK メニュー。

    -   他[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]このファイル拡張子を使用する拡張機能は完全にコンピューターにインストールされた、アンインストールすることを検討してください。 **ツール** メニューのをクリックして**拡張機能マネージャー**です。

4.  検査、および、必要に応じて調整、ウィザードの残りのページのフィールドです。 設定に満足したらをクリックして**完了**です。 設定の詳細については、次を参照してください。 [DSL デザイナーのウィザード ページ](#settings)です。

     ウィザードの名前は 2 つのプロジェクトが含まれるソリューションを作成する**Dsl**と**DslPackage**です。

    > [!NOTE]
    >  信頼されていないソースからのテキスト テンプレートの実行をクリックしてできませんを通知するメッセージが表示する場合**OK**です。 このメッセージを再び表示されないように設定できます。

##  <a name="settings"></a> DSL デザイナーのウィザード ページ
 いくつかの既定値から変更されていないフィールドをおくことができます。 ただし、ファイル拡張子 フィールドを設定することを確認します。

### <a name="solution-settings-page"></a>ソリューションの設定 ページ
 **どのテンプレートを基に、ドメイン固有言語か?**
作成する DSL には、次のようなテンプレートを選択します。 別のテンプレートは、便利な開始点を提供します。 ソリューション テンプレートを選択すると、ウィザードには、説明が表示されます。 ソリューション テンプレートの詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートを選択する](../modeling/choosing-a-domain-specific-language-solution-template.md)です。

 **実行する、ドメイン固有言語の名前**
既定値は、ソリューション名です。 コードは、この値から生成されます。 C# クラス名として有効な場合があります。

### <a name="file-extension-page"></a>ファイル拡張子 ページ
 **どのような拡張機能をモデル ファイルを使用しますか。**
新しいファイル拡張子を入力します。

 このファイル拡張子が既に登録されていないこと、このコンピューターで使用するようを確認します。

 確認**この拡張機能を処理するその他のツールとアプリケーションが登録されて**です。 メッセージを表示する場合は**アプリケーションまたは Visual Studio のエディターを使用するこの拡張機能**、このファイル拡張子を使用できます。

 ツールまたはパッケージの一覧を表示する場合は、次のいずれかを行う必要があります。

-   別のファイル拡張子を入力します。

     \- または -

-   リセット、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]実験用インスタンス。 これは、すべて以前作成した Dsl の登録解除します。 **開始** メニューのをクリックして**すべてのプログラム**、 **Microsoft Visual Studio 2010 SDK**、**ツール**、し**リセット、Microsoft Visual Studio 2010 実験用インスタンス**です。 再利用する他の Dsl を再構築することができます。

     \- または -

-   場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コンピューターに、このファイル拡張子を使用する拡張機能を完全にインストールされたが、これをアンインストールします。 **ツール** メニューのをクリックして**拡張機能マネージャー**です。

### <a name="product-settings-page"></a>製品の設定 ページ
 **新しいドメイン固有言語が含まれている製品の名前は何ですか。**
既定値は、DSL の名前です。

 この値は、このファイル拡張子を持つファイルを記述する Windows エクスプ ローラー (またはファイル エクスプ ローラー) で使用されます。

 **製品が属している、会社の名前は何ですか。**
会社名。

 この値は、AssemblyInfo、DSL のパッケージのプロパティに組み込まれます。

 **このソリューションでプロジェクトのルート名前空間とは何ですか。**
既定値は、会社から構成される名前と製品名。

### <a name="signing-page"></a>[署名] ページ
 **厳密な名前キー ファイルを作成**DSL アセンブリに署名する新しいキーの作成には、既定のオプションです。

 **既存の厳密な名前キーを使用して**別のアセンブリと、DSL を統合する場合は、このオプションを使用します。

 厳密な名前付けの詳細については、次を参照してください。[作成と使用](http://go.microsoft.com/fwlink/?LinkId=186073)です。

## <a name="see-also"></a>関連項目

- [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)
- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
