---
title: Windows フォームに基づくドメイン固有言語の作成
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ce2fa2f067b72d051aa21eba0db2b8f0eda8b43f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Windows フォームに基づくドメイン固有言語の作成
Windows フォームを使用すると、DSL 図を使用する代わりに、ドメイン固有言語 (DSL) モデルの状態を表示します。 このトピックを紹介 DSL への Windows フォームのバインドを使用して、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK。

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2") A DSL のインスタンス、Windows フォーム UI とモデル エクスプ ローラーを表示します。

## <a name="creating-a-windows-forms-dsl"></a>Windows フォーム DSL を作成します。
 **最小限 WinForm デザイナー** DSL テンプレートには、独自の要件に合わせて変更できる最小限に抑える DSL が作成されます。

#### <a name="to-create-a-minimal-winforms-dsl"></a>最小 WinForms DSL を作成するには

1.  DSL を作成、**最小限 WinForm デザイナー**テンプレート。

     このチュートリアルでは、次の名前が想定しています。

    |||
    |-|-|
    |ソリューションと DSL の名前|FarmApp|
    |名前空間|Company.FarmApp|

2.  テンプレートでは最初の例で実験します。

    1.  すべてのテンプレートを変換します。

    2.  ビルドおよび実行するサンプル (**ctrl キーを押しながら f5 キーを押して**)。

    3.  Visual Studio の実験用インスタンスの開く、`Sample`デバッグ プロジェクト内のファイルです。

         Windows フォーム コントロール内に表示されることに注意してください。

         エクスプ ローラーで表示されているモデルの要素を表示することもできます。

         フォームまたはエクスプ ローラーで、いくつかの要素を追加し、その他のディスプレイに表示されることに注意してください。

 メイン インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、DSL ソリューションについて、次の点に注意してください。

-   `DslDefinition.dsl` 図の要素は含まれません。 DSL 図この DSL のインスタンス モデルを表示する使用しないためにです。 Windows フォームは、モデルにバインドして、モデルをフォーム上の要素が表示されます。

-   加え、`Dsl`と`DslPackage`プロジェクト、ソリューションに含まれるという名前の 3 つ目のプロジェクト`UI.` **UI**プロジェクトには、Windows フォーム コントロールの定義が含まれています。 `DslPackage` 異なります`UI`、および`UI`異なります`Dsl`です。

-   `DslPackage`プロジェクト、`UI\DocView.cs`で定義されている Windows フォーム コントロールを表示するコードが含まれています、`UI`プロジェクト。

-   `UI`プロジェクトには、DSL にバインドされたフォーム コントロールの実際のサンプルが含まれています。 ただし、何も起こりません DSL 定義を変更したときにします。 `UI`プロジェクトが含まれています。

    -   という名前の Windows フォーム クラス`ModelViewControl`です。

    -   という名前のファイル`DataBinding.cs`の他の部分定義を含む`ModelViewControl`です。 そのコンテンツを表示する**ソリューション エクスプ ローラー**ファイルのショートカット メニューを開き、選択**コードの表示**です。

### <a name="about-the-ui-project"></a>UI プロジェクトについて
 DSL 定義ファイルを独自の DSL の定義を更新するときにコントロールを更新する必要が、 `UI` DSL を表示するプロジェクトです。 異なり、`Dsl`と`DslPackage`プロジェクト、サンプル`UI`からプロジェクトは生成されません`DslDefinitionl.dsl`です。 コードを生成する場合は、するは、このチュートリアルでは説明しませんが、.tt ファイルを追加することができます。

## <a name="updating-the-dsl-definition"></a>DSL 定義の更新
 DSL 定義は、このチュートリアルで使用します。

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")

#### <a name="to-update-the-dsl-definition"></a>DSL 定義を更新するには

1.  DSL デザイナーで DslDefinition.dsl を開きます。

2.  削除**ExampleElement**

3.  名前を変更、 **ExampleModel**ドメイン クラス`Farm`です。

     追加のドメイン プロパティの名前を付けます`Size`型の**Int32**、および`IsOrganic`型の**ブール**です。

    > [!NOTE]
    >  ルート ドメイン クラスを削除して、新しいルートを作成した場合、エディターのルート クラスのプロパティをリセットする必要があります。 **DSL のエクスプ ローラー****エディター**です。 [プロパティ] ウィンドウで次のように設定します。**ルート クラス**に`Farm`です。

4.  使用して、**という名前のドメイン クラス**次のドメイン クラスを作成するツール。

    -   `Field` -付与このという追加のドメイン プロパティ`Size`です。

    -   `Animal` [プロパティ] ウィンドウで次のように設定します。**継承修飾子**に**抽象**です。

5.  使用して、**ドメイン クラス**次のクラスを作成するツール。

    -   `Sheep`

    -   `Goat`

6.  使用して、**継承**ツールを`Goat`と`Sheep`から継承`Animal`です。

7.  使用して、 **Embedding**を埋め込むツール`Field`と`Animal``Farm`です。

8.  ダイアグラムを整理することがあります。 重複する要素の数を減らすためを使用して、**サブツリーをここに表示**リーフ要素のショートカット メニューの コマンド。

9. **すべてのテンプレートを変換**ソリューション エクスプ ローラーのツールバーにします。

10. ビルド、 **Dsl**プロジェクト。

    > [!NOTE]
    >  エラーが発生しないが、この段階で、他のプロジェクトを構築できません。 ただし、そのアセンブリをデータ ソース ウィザードを使用できるように、Dsl プロジェクトをビルドします。

## <a name="updating-the-ui-project"></a>UI プロジェクトの更新
 ここで、DSL モデルに格納されている情報を表示する新しいユーザー コントロールを作成できます。 ユーザー コントロールをモデルに接続する最も簡単な方法はデータ バインドです。 データ バインディングという名前のアダプター型**ModelingBindingSource** Dsl を非 VMSDK インターフェイスに接続する専用です。

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>データ ソースとして、DSL モデルを定義するには

1.  **データ**] メニューの [選択**データ ソースの表示**です。

     **データソース**ウィンドウが開きます。

     選択**新しいデータ ソースの追加**です。 **データ ソース構成ウィザード**が開きます。

2.  選択**オブジェクト**、**次**です。

     展開**Dsl**、 **Company.FarmApp**を選択して**ファーム**、これは、モデルのルート クラスです。 **[完了]** を選択します。

     ソリューション エクスプ ローラーで、 **UI**プロジェクトが含まれています**Properties\DataSources\Farm.datasource**

     プロパティと、モデル クラスの関係は、データ ソース ウィンドウに表示されます。

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")

#### <a name="to-connect-your-model-to-a-form"></a>フォームに、モデルを接続するには

1.  **UI**プロジェクトで、既存のすべての .cs ファイルを削除します。

2.  新しい**ユーザー コントロール**という名前のファイル`FarmControl`を**UI**プロジェクト。

3.  **データソース**でドロップダウン メニューを開き、ウィンドウ**ファーム**、選択**詳細**です。

     その他のプロパティの既定の設定のままにします。

4.  デザイン ビューで FarmControl.cs を開きます。

     ドラッグ**ファーム**FarmControl、データ ソース ウィンドウからです。

     コントロールのセットが表示されたら、各プロパティのいずれか。 リレーションシップのプロパティでは、コントロールは生成されません。

5.  削除**farmBindingNavigator**です。 これがも自動的に生成、`FarmControl`デザイナーがこのアプリケーションに便利ではありません。

6.  2 つのインスタンスを作成、ツールボックスを使用して**DataGridView**、し名前を付ける`AnimalGridView`と`FieldGridView`です。

    > [!NOTE]
    >  代替の手順では、コントロールにデータ ソース ウィンドウから動物やフィールドの項目をドラッグします。 この操作は、データ グリッドとグリッド ビューとデータ ソース間のバインドに自動的に作成されます。 ただし、このバインディングは、Dsl は正しく機能しません。 したがって、データ グリッドとバインディングを作成する方は手動でします。

7.  ツールボックスが含まれていない場合、 **ModelingBindingSource**ツール、それを追加します。 ショートカット メニューを開き、**データ** タブで、選択**アイテムの選択**です。 **ツールボックス アイテムの選択**ダイアログで、 **ModelingBindingSource**から、 **.NET Framework タブ**です。

8.  2 つのインスタンスを作成、ツールボックスを使用して**ModelingBindingSource**、し名前を付ける`AnimalBinding`と`FieldBinding`です。

9. 設定、**データソース**の各プロパティ**ModelingBindingSource**に**farmBindingSource**です。

     設定、 **DataMember**プロパティを**動物**または**フィールド**です。

10. 設定、**データソース**のプロパティ`AnimalGridView`に`AnimalBinding`、および`FieldGridView`に`FieldBinding`です。

11. 任意で、ファームのコントロールのレイアウトを調整します。

 **ModelingBindingSource** Dsl に固有のいくつかの機能を実行するアダプターします。

-   VMSDK ストアのトランザクションで更新プログラムをラップします。

     たとえば、ユーザーは、データ ビューのグリッドから行を削除、ときに、標準バインディングになりますトランザクション例外。

-   これにより、ユーザーは、行を選択するときに、[プロパティ] ウィンドウが表示されるデータ グリッド行の代わりに、対応するモデル要素のプロパティ。

 ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")データ ソースとビューの間のリンクのスキーマです。

#### <a name="to-complete-the-bindings-to-the-dsl"></a>DSL へのバインドを完了するには

1.  別のコード ファイルに次のコードを追加、 **UI**プロジェクト。

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2.  **DslPackage**プロジェクト、編集**DslPackage\DocView.tt**を次の変数の定義を更新します。

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>DSL のテスト
 DSL ソリューションできますを作成および機能強化を後で追加することができますが、実行します。

#### <a name="to-test-the-dsl"></a>DSL をテストするには

1.  ソリューションをビルドして実行します。

2.  Visual Studio の実験用インスタンスの開く、**サンプル**ファイル。

3.  **FarmApp エクスプ ローラー**のショートカット メニューを開き、**ファーム**ルート ノード、および選択**追加新しい Goat**です。

     `Goat1` 表示されます、**動物**ビュー。

    > [!WARNING]
    >  ショートカット メニューを使用する必要があります、**ファーム**ノード、されません、**動物**ノード。

4.  選択、**ファーム**ルート ノードとそのプロパティを表示します。

     フォーム ビューで、変更、**名前**または**サイズ**ファームのです。

     フォームで、[プロパティ] ウィンドウの対応するプロパティの変更には、各フィールドから移動するとします。

## <a name="enhancing-the-dsl"></a>DSL の強化

#### <a name="to-make-the-properties-update-immediately"></a>プロパティをすぐに更新するには

1.  FarmControl.cs のデザイン ビューでは、名前、サイズまたは IsOrganic などの単純なフィールドを選択します。

2.  プロパティ ウィンドウで  **DataBindings**開き **(詳細)** です。

     **フォーマットと詳細バインド**ダイアログで、**データ ソース更新モード**、選択**OnPropertyChanged**です。

3.  ソリューションをビルドして実行します。

     ファーム モデルの変更をすぐに対応するプロパティ、フィールドの内容を変更すると、ことを確認します。

#### <a name="to-provide-add-buttons"></a>追加のボタンを提供するには

1.  FarmControl.cs のデザイン ビューで、ツールボックスを使用して、フォームにボタンを作成します。

     たとえば名前と、ボタンのテキストを編集`New Sheep`です。

2.  ボタンの分離コード (たとえばダブルクリックして開きます)。

     次のように編集します。

    ```csharp
    private void NewSheepButton_Click(object sender, EventArgs e)
    {
      using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
      {
        elementOperations.MergeElementGroup(farm,
          new ElementGroup(new Sheep(farm.Partition)));
        t.Commit();
      }
    }

    // The following code is shared with other add buttons:
    private ElementOperations operationsCache = null;
    private ElementOperations elementOperations
    {
      get
      {
        if (operationsCache == null)
        {
          operationsCache = new ElementOperations(farm.Store, farm.Partition);
        }
        return operationsCache;
      }
    }
    private Farm farm
    {
      get { return this.farmBindingSource.DataSource as Farm; }
    }

    ```

     次のディレクティブを挿入する必要がありますも。

    ```csharp

    using Microsoft.VisualStudio.Modeling;

    ```

3.  フィールドとしたのと同様のボタンを追加します。

4.  ソリューションをビルドして実行します。

5.  新しいボタンが項目を追加することを確認します。 FarmApp エクスプ ローラーで、適切なデータ グリッド ビューでは、新しい項目が表示されます。

     データ グリッド ビュー内の要素の名前を編集することができます。 そこから削除することもできます。

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")

### <a name="about-the-code-to-add-an-element"></a>要素を追加するコードについて
 新しい要素ボタンでは、次の代替コードは少し簡単なです。

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}

```

 ただし、このコードは、新しい項目の既定の名前を設定できません。 定義した任意のカスタマイズされたマージは実行されません、**要素マージ ディレクティブ**DSL の定義されているすべてのカスタムのマージ コードは実行されません。

 そのためことをお勧めを使用すること<xref:Microsoft.VisualStudio.Modeling.ElementOperations>新しい要素を作成します。 詳細については、次を参照してください。[をカスタマイズする要素の作成および移動](../modeling/customizing-element-creation-and-movement.md)です。

## <a name="see-also"></a>関連項目

- [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)