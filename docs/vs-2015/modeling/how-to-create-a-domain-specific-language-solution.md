---
title: '方法: ドメイン固有言語ソリューションの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2650afc2172cdcceca892d4ad19a05becac3e472
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908940"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>方法: ドメイン固有言語ソリューションを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ドメイン固有言語 (DSL) を使用して作成する特殊な[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ソリューション。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 この手順を開始する前に、これらのコンポーネントをまずインストールする必要があります。  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成します。  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成するには  
  
1. DSL のウィザードを起動します。  
  
   1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
   2. **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
   3. **プロジェクトの種類**、展開、**その他のプロジェクトの種類**ノードをクリックします**Extensibility**します。  
  
   4. クリックして**ドメイン固有言語デザイナー**します。  
  
   5. **名前**ボックスに、ソリューションの名前を入力します。 **[OK]** をクリックします。  
  
       **ドメイン固有言語デザイナー ウィザード**が表示されます。  
  
      > [!NOTE]
      >  可能であれば、コードを生成するために使用可能性がありますので、入力した名は有効な Visual c# の識別子にする必要があります。  
  
      ![DSL ダイアログの作成](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. DSL テンプレートを選択します。  
  
    **ドメイン固有言語のオプションの選択**などソリューション テンプレートのいずれかの選択 ページで、**最小言語**します。 DSL を作成する次のようなテンプレートを選択します。  
  
    ソリューション テンプレートの詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートの選択](../modeling/choosing-a-domain-specific-language-solution-template.md)します。  
  
3. ファイル名拡張子を入力、**ファイル拡張子**ページ。 自分のコンピューターで一意である必要がありする任意のコンピューターでは、DSL をインストールします。 メッセージが表示する必要があります**アプリケーションまたは Visual Studio エディターにこの拡張機能使用しない**します。  
  
   -   完全にインストールされていない以前の実験的な Dsl で、ファイル名拡張子を使用した場合ことができますをオフにすることを使用して、**実験用インスタンスをリセット**では、ツール、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK メニュー。  
  
   -   もう 1 つ場合[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]このファイルの拡張機能を使用する拡張機能は完全にコンピューターにインストールされたをアンインストールすることを検討してください。 **ツール** メニューのをクリックして**拡張機能マネージャー**します。  
  
4. 検査、および必要に応じて調整、ウィザードの残りのページのフィールド。 設定に満足したら、クリックして**完了**します。 設定の詳細については、次を参照してください。 [DSL デザイナーのウィザード ページ](#settings)します。  
  
    ウィザードの名前は 2 つのプロジェクトを含むソリューションを作成します**Dsl**と**DslPackage**します。  
  
   > [!NOTE]
   >  信頼されていないソースからのテキスト テンプレートを実行するには、をクリックしないを通知するメッセージが表示された場合**OK**します。 このメッセージが再び表示されるように設定できます。  
  
##  <a name="settings"></a> DSL デザイナーのウィザード ページ  
 既定値から変更されていないフィールドのいくつかのままにすることができます。 ただし、ファイル拡張子のフィールドを設定することを確認します。  
  
### <a name="solution-settings-page"></a>ソリューションの設定 ページ  
 **どのテンプレート、ドメイン固有言語を基になるか?**  
 DSL を作成する次のようなテンプレートを選択します。 別のテンプレートは、便利な開始ポイントを提供します。 ソリューション テンプレートを選択すると、ウィザードには、説明が表示されます。 ソリューション テンプレートの詳細については、次を参照してください。[ドメイン固有言語ソリューション テンプレートの選択](../modeling/choosing-a-domain-specific-language-solution-template.md)します。  
  
 **ドメイン固有言語の名前にしますか。**  
 既定値は、ソリューション名です。 コードは、この値から生成されます。 C# クラス名として有効な場合があります。  
  
### <a name="file-extension-page"></a>ファイル拡張子 ページ  
 **どのような拡張機能がモデル ファイルが使用しますか。**  
 新しいファイル拡張子を入力します。  
  
 このファイルの拡張機能が既に登録されていないこと、このコンピューターで使用する次のように確認します。  
  
 下を見て**他のツールやアプリケーションは、この拡張機能を処理するために登録されている**します。 メッセージが表示された場合**アプリケーションまたは Visual Studio エディターにこの拡張機能使用しない**、このファイルの拡張機能を使用することができます。  
  
 ツールまたはパッケージの一覧を表示する場合は、次のいずれかを実行する必要があります。  
  
-   別のファイル拡張子を入力します。  
  
     \- または -  
  
-   リセット、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]実験用インスタンス。 これは、すべてが以前にビルドされた Dsl の登録解除します。 **開始** メニューのをクリックして**すべてのプログラム**、 **Microsoft Visual Studio 2010 SDK**、**ツール**、し**リセット、Microsoft Visual Studio 2010 実験用インスタンス**します。 もう一度使用するその他の任意の Dsl を再構築することができます。  
  
     \- または -  
  
-   場合、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]このファイルの拡張機能を使用する拡張機能がコンピューターに完全にインストールされて、それをアンインストールします。 **ツール** メニューのをクリックして**拡張機能マネージャー**します。  
  
### <a name="product-settings-page"></a>製品の設定 ページ  
 **新しいドメイン固有言語が含まれている製品の名前は何ですか。**  
 既定値は、DSL の名前です。  
  
 この値は、このファイル拡張子を持つファイルを記述する、Windows エクスプ ローラー (またはファイル エクスプ ローラー) で使用されます。  
  
 **製品が属している会社の名前は何ですか。**  
 会社名。  
  
 この値は DSL パッケージの AssemblyInfo プロパティに組み込まれます。  
  
 **このソリューションでプロジェクトのルート名前空間とは何ですか。**  
 これは、会社から構成される名前と製品名を既定値です。  
  
### <a name="signing-page"></a>[署名] ページ  
 **厳密な名前キー ファイルを作成します。**  
 既定のオプションは、DSL のアセンブリの署名に新しいキーを作成します。  
  
 **既存の厳密な名前キーを使用します。**  
 別のアセンブリと DSL を統合する場合は、このオプションを使用します。  
  
 厳密な名前付けの詳細については、次を参照してください。[の作成と using strong-named Assemblies](http://go.microsoft.com/fwlink/?LinkId=186073)します。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)   
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



