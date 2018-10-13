---
title: 定義のカスタム モデリング ツールボックス アイテム |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 994bb8dfd047320ac0ea4a0d63260f19a2c3d45c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252370"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>カスタム モデリング ツールボックス アイテムを定義する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

頻繁に使用するパターンを使って簡単に要素または要素グループを作成するために、Visual Studio のモデリング図のツールボックスに新しいツールを追加することができます。 これらのツールボックス アイテムは、Visual Studio の他のユーザーに配布することができます。  
  
 この機能をサポートする Visual Studio のバージョンを確認するには、「 [アーキテクチャ ツールとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
 カスタム ツールは、図の中に 1 つまたは複数の新しい要素を作成します。 例えば、次のような要素を作成するカスタム ツールを作成できます。  
  
-   .NET プロファイルにリンクされたパッケージと、.NET のステレオタイプを持つクラス。  
  
-   オブザーバー パターンを表す関連付けによってリンクされたクラスのペア。  
  
> [!NOTE]
>  このメソッドを使用して、要素ツールを作成することができます。 つまり、ツールボックスから図にドラッグするツールを作成できます。 コネクタ ツールは作成できません。  
  
##  <a name="DefineTool"></a> カスタム モデリング ツールを定義します。  
  
#### <a name="to-define-a-custom-modeling-tool"></a>カスタム モデリング ツールを定義するには  
  
1.  要素または要素グループを含んだ UML 図を作成します。  
  
    -   これらの要素の間にはリレーションシップを設定できます。また、要素は、ポート、属性、操作またはピンなどの付属の要素を持つこともできます。  
  
2.  新しいツールにつける名前で図を保存します。 **ファイル**] メニューの [使用**を保存しています.として**します。  
  
3.  Windows エクスプローラーを使用して、2 つの図ファイルを次のフォルダーまたはその下の任意のサブフォルダーにコピーします。  
  
     *YourDocuments* **\Visual Studio\Architecture Tools\Custom ツールボックス アイテムの選択**  
  
    -   このフォルダがまだ存在しない場合は作成します。 両方を作成する必要があります**アーキテクチャ ツール**と**カスタム ツールボックス アイテム**します。  
  
    -   両方のダイアグラム ファイルが... に終了する名前を持つ 1 つのコピーします。**ダイアグラム**"と名前の末尾に、その他の"しています.**diagram.layout**"  
  
    -   カスタム ツールは必要に応じていくつでも作成できます。 各ツールに 1 つの図を使用します。  
  
4.  (省略可能)作成、 **.tbxinfo**ファイル」の説明に従って[カスタム ツールのプロパティを定義する方法](#tbxinfo)、同じディレクトリに追加します。 これによって、ツールボックス アイコンやヒントなどを定義することができます。  
  
    -   1 つ **.tbxinfo**ファイルを使用して、いくつかのツールを定義します。 これは、サブフォルダーにある複数の図ファイルを参照できます。  
  
5.  Visual Studio を再起動します。 ツールボックスにそれぞれの図の型に対応する追加のツールが表示されます。  
  
### <a name="what-the-custom-tool-will-replicate"></a>カスタム ツールのレプリケート対象  
 カスタム ツールは、元の図のほとんどの機能をレプリケートします。  
  
-   名前。 ツールボックスから項目が作成されると、同じ名前空間で名前が重複することを回避するために、必要に応じて名前の末尾に数値が追加されます。  
  
-   色、サイズ、および図形  
  
-   ステレオタイプおよびパッケージ プロファイル  
  
-   Is Abstract などのプロパティ値  
  
-   リンクされた作業項目  
  
-   リレーションシップの多重度と他のプロパティ  
  
-   図形の相対位置。  
  
 次の機能は、カスタム ツールでは保存されません。  
  
-   単純な図形。 これらはモデル要素に関連しない、一部の種類の図に描画できる図形のことです。  
  
-   コネクタのルーティング。 コネクタを手動でルーティングする場合、ツールを使用するとルーティングは保持されません。 ポートなどの入れ子になった一部の図形の位置は、その所有者に関連して保持されることはありません。  
  
##  <a name="tbxinfo"></a> カスタム ツールのプロパティを定義する方法  
 ツールボックスの情報 (**.tbxinfo**) ファイルでは、ツールボックスの名前、アイコン、ヒント、タブを指定し、ヘルプ キーワードを 1 つまたは複数のカスタム ツールのことができます。 任意の名前など付けます**MyTools.tbxinfo**します。  
  
 一般的なファイル形式は、次のとおりです。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">  
  <customToolboxItem fileName="MyObserverTool.classdiagram">  
    <displayName>  
       <value>Observer Pattern</value>  
    </displayName>  
    <tabName>  
       <value>UML Class Diagram</value>  
    </tabName>  
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>  
    <f1Keyword>  
      <value>ObserverPatternHelp</value>  
    </f1Keyword>  
    <tooltip>  
       <value>Create a pair of classes</value>  
    </tooltip>  
  </customToolboxItem>  
</customToolboxItems>  
```  
  
 各アイテムの値は、次のいずれかになります。  
  
-   この例で示すように、ツールボックス アイコンでは `<bmp fileName="…"/>` で、その他のアイテムでは `<value>string</value>` です。  
  
 \- または -  
  
-   `<resource fileName="Resources.dll"`  
  
     `baseName="Observer.resources" id="Observer.tabname" />`  
  
     この場合は、文字列値がリソースとしてコンパイルされている、コンパイル済みのアセンブリを指定します。  
  
 定義するツールボックス アイテムごとに `<customToolboxItem>` ノードを追加します。  
  
 内のノード、 **.tbxinfo**ファイルは、次のとおりです。 各ノードには、既定値が設定されています。  
  
|ノード名|定義|  
|---------------|-------------|  
|displayName|ツールボックス アイテムの名前。|  
|tabName|アイテムが表示されるツールボックス タブ。 この種類の図の標準タブの名前か、別の名前を指定できます。|  
|イメージ|ビットマップの位置 (**.bmp**) ファイル、高さと 16 で、幅と色深度が 24 ビットである必要があります。|  
|f1Keyword|ヘルプ トピックを検索するキーワードです。|  
|ヒント|このツールのヒントです。|  
  
 Visual Studio でビットマップ ファイルを編集して、[プロパティ] ウィンドウで高さと幅を 16 に設定できます。  
  
> [!NOTE]
>  図ファイルを単独で使用して試した後に .tbxinfo ファイルを使用し始めた場合、ツールボックスには、ツールボックス アイテムの古いバージョンと新しいバージョンの両方が含まれる場合があります。 これは、.tbxinfo ファイルで図ファイルの名前が間違っている場合にも発生します。 この場合、選択して、ツールボックスのショートカット メニューの [**ツールボックスのリセット]** します。 カスタム ツールボックス アイテムが表示されなくなります。 Visual Studio を再起動すると、正しいカスタム アイテムが表示されます。  
  
##  <a name="Extension"></a> Visual Studio 拡張機能内のツールボックス項目を配布する方法  
 他のツールボックス項目を配布する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]を Visual Studio Extension (VSIX) パッケージ化してユーザー。 コマンド、プロファイルなどの拡張機能を同じ VSIX ファイルにパッケージ化できます。 詳細については、次を参照してください。 [Visual Studio 拡張機能の配置](http://go.microsoft.com/fwlink/?LinkId=160780)します。  
  
 Visual Studio 拡張機能をビルドするには、通常は VSIX プロジェクトのテンプレートを使用します。 これを行うには、[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] をインストールしておく必要があります。  
  
#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>ツールボックス アイテムを Visual Studio 拡張機能に追加するには  
  
1.  [作成し、1 つまたは複数のカスタム ツールをテスト](#DefineTool)します。  
  
2.  [.Tbxinfo ファイルを作成する](#tbxinfo)ツールを参照します。  
  
3.  既存の Visual Studio 拡張機能プロジェクトを開きます。  
  
     \- または -  
  
     新しい Visual Studio 拡張機能プロジェクトを定義します。  
  
    1.  **[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]** をクリックします。  
  
    2.  **新しいプロジェクト**ダイアログ ボックスで、**インストールされたテンプレート**、選択**Visual c#**、**拡張**、 **VSIXプロジェクト**します。  
  
4.  プロジェクトにツールボックスの定義を追加します。 含める、 **.tbxinfo**ファイル、図ファイル、ビットマップ ファイル、およびリソース ファイル、およびそれらが VSIX に含まれているかどうかを確認します。  
  
    -   ソリューション エクスプ ローラーで、VSIX プロジェクトのショートカット メニューの 選択**追加**、**既存項目の**します。 ダイアログ ボックスで、次のように設定します。**オブジェクトの型: すべてのファイル**します。 ファイルを検索し、すべてを選択し、**追加**します。  
  
        > [!NOTE]
        >  このプロジェクトでは、図ファイルをモデル エディターで開くことができません。  
  
5.  ここで追加したすべてのファイルについて次のプロパティを設定します。 ソリューション エクスプローラーでそれらすべてを選択すると、それらのプロパティを同時に設定できます。 プロジェクト内の他のファイルのプロパティを変更しないように注意してください。  
  
     **出力ディレクトリにコピー** = **常にコピーします。**  
  
     **ビルド アクション** = **コンテンツ**  
  
     **VSIX に含める** = **は true。**  
  
6.  **source.extension.vsixmanifest**を開きます。 このファイルは拡張機能マニフェスト エディターで開きます。  
  
7.  **メタデータ**、カスタム ツールの説明を追加します。  
  
     **資産**、選択**新規**し、次のように、ダイアログ ボックスで、フィールドを設定します。  
  
    -   **型** = **カスタム拡張機能の種類**  
  
    -   種類 = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`  
  
        > [!NOTE]
        >  これは、ドロップダウン リストのオプションの 1 つではありません。 キーボードを使用して入力する必要があります。  
  
    -   **ソース** = **ファイル システム上の**します。  
  
    -   **パス**=、 **.tbxinfo**ファイル、たとえば**MyTools.tbxinfo**  
  
8.  プロジェクトをビルドします。  
  
9. **拡張機能が動作を確認する**、F5 キーを押します。 Visual Studio の実験用インスタンスが開始します。  
  
     実験用のインスタンスで、関連する型の UML 図を作成するか開きます。 新しいツールがツールボックスに表示されることと、正しく要素が作成されることを確認します。  
  
10. **デプロイ用の VSIX ファイルを取得する:** Windows エクスプ ローラーでフォルダーを開きます **.\bin\Debug**または **.\bin\Release**を検索する、 **.vsix**ファイル。 これは [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 拡張ファイルです。 このファイルは、自分のコンピューターにインストールできるほか、他の Visual Studio ユーザーに送信することもできます。  
  
#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Visual Studio 拡張機能からカスタム ツールをインストールするには  
  
1.  Windows エクスプローラーまたは Visual Studio で `.vsix` ファイルを開きます。  
  
2.  選択**インストール**で表示されるダイアログ ボックス。  
  
3.  アンインストールまたは拡張機能を一時的に無効にする、開く**拡張機能と更新**から、**ツール**メニュー。  
  
## <a name="localization"></a>ローカリゼーション  
 拡張機能が別のコンピューターにインストールされると対象のコンピュータの言語でツールの名前やヒントが表示されるように設定できます。  
  
#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>複数の言語のバージョンのツールを提供するには  
  
1.  1 つ以上のカスタム ツールを含んだ Visual Studio 拡張機能プロジェクトを作成します。  
  
     **.Tbxinfo**ファイル、ツールの定義をリソース ファイルのメソッドを使用して`displayName`、ツールボックス`tabName`、およびツールヒント。 これらの文字列が定義されているリソース ファイルを作成してアセンブリにコンパイルし、tbxinfo ファイルからそれを参照します。  
  
2.  他の言語の文字列のリソース ファイルが含まれている追加のアセンブリを作成します。  
  
3.  言語のカルチャ コードを名前にしたフォルダーに、追加のアセンブリをそれぞれ配置します。 たとえば、フランス語バージョンのアセンブリをという名前のフォルダー内に配置**fr**します。  
  
4.  `fr-CA` のような特定カルチャではなく、通常 2 つの文字で構成されるニュートラル カルチャ コードを使用する必要があります。 カルチャ コードの詳細については、次を参照してください。 [CultureInfo.GetCultures メソッド](http://go.microsoft.com/fwlink/?LinkId=160782)、カルチャ コードの完全な一覧を提供します。  
  
5.  Visual Studio 拡張機能をビルドして配布します。  
  
6.  拡張機能が別のコンピューターにインストールされると、ユーザーのローカル カルチャのリソース ファイルのバージョンが自動的にロードされます。 ユーザーのカルチャのバージョンをまだ提供していない場合、デフォルトのリソースが使用されます。  
  
 この方式を使用して、プロトタイプ図のさまざまなバージョンをインストールすることはできません。 要素とコネクタの名前は、どのインストールでも同じになります。  
  
## <a name="other-toolbox-operations"></a>その他のツールボックスの操作  
 通常、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] では、ツールの名前を変更したり、別のツールボックスのタブに移動したり、それらを削除したりすることで、ツールボックスをカスタマイズすることができます。 ただし、このトピックで説明した手順で作成したカスタム モデリング ツールでは、このような変更が維持されません。 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] を再起動すると、定義済みの名前とツールボックスの場所でツールボックスが再表示されます。  
  
 実行する場合に、カスタム ツールがさらに、非表示、**ツールボックスのリセット**コマンド。 しかし、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] を再起動すると再び表示されます。  
  
## <a name="see-also"></a>関連項目  
 [UML モデルと図を拡張します。](../modeling/extend-uml-models-and-diagrams.md)   
 [プロファイルを定義すると、UML を拡張](../modeling/define-a-profile-to-extend-uml.md)   
 [モデリング図にメニュー コマンドを定義します。](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML モデルの検証制約を定義する](../modeling/define-validation-constraints-for-uml-models.md)



