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
ms.openlocfilehash: f8034ae225707ec6030daba39ed09bab3bd161c4
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859524"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Windows フォームに基づくドメイン固有言語の作成
DSL 図を使用する代わりに、ドメイン固有言語 (DSL) モデルの状態を表示するのに Windows フォームを使用することができます。 ここでは、Visual Studio Visualization and Modeling SDK を使用して、DSL への Windows フォームのバインドを示します。

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png)する DSL のインスタンス、Windows フォームの UI とモデル エクスプ ローラーを表示します。

## <a name="creating-a-windows-forms-dsl"></a>Windows フォームの DSL を作成します。
 **最小 WinForm デザイナー** DSL テンプレートは、独自の要件に合わせて変更できる最小限の DSL を作成します。

#### <a name="to-create-a-minimal-winforms-dsl"></a>最小限の WinForms DSL を作成するには

1.  DSL を作成、**最小 WinForm デザイナー**テンプレート。

     このチュートリアルでは、次の名前が想定しています。

    |||
    |-|-|
    |ソリューションと DSL 名|FarmApp|
    |名前空間|Company.FarmApp|

2.  テンプレートに用意された最初の例を試してみる。

    1.  すべてのテンプレートを変換します。

    2.  サンプルのビルドおよび実行 (**CTRL + F5**)。

    3.  Visual Studio の実験用インスタンスを開き、`Sample`デバッグ プロジェクト ファイル。

         Windows フォーム コントロールに表示されることに注意してください。

         エクスプ ローラーで表示されるモデルの要素を確認することもできます。

         フォームまたはエクスプ ローラーで、いくつかの要素を追加し、その他のディスプレイに表示されることに注意してください。

 Visual Studio のメイン インスタンスでは、DSL ソリューションについては、次の点に注意してください。

-   `DslDefinition.dsl` ダイアグラムの要素が含まれない。 この DSL のインスタンス モデルを表示する DSL ダイアグラム使用しないためにです。 代わりに、Windows フォーム、モデルにバインドして、フォームでの要素、モデルが表示されます。

-   加え、`Dsl`と`DslPackage`プロジェクト、ソリューションに含まれるという名前の 3 つ目のプロジェクト`UI.` **UI**プロジェクトには、Windows フォーム コントロールの定義が含まれています。 `DslPackage` 依存`UI`と`UI`異なります`Dsl`します。

-   `DslPackage`プロジェクト、`UI\DocView.cs`で定義されている Windows フォーム コントロールを表示するコードが含まれています、`UI`プロジェクト。

-   `UI`プロジェクトには、DSL にバインドされたフォーム コントロールの実際のサンプルが含まれています。 ただし、これは機能しません、DSL 定義を変更したとき。 `UI`プロジェクトが含まれています。

    -   という名前の Windows フォーム クラス`ModelViewControl`します。

    -   という名前のファイル`DataBinding.cs`の他の部分定義を格納している`ModelViewControl`します。 そのコンテンツを表示する**ソリューション エクスプ ローラー**ファイルのショートカット メニューを開き、選択**コードの表示**します。

### <a name="about-the-ui-project"></a>UI プロジェクトについて
 内のコントロールを更新する必要があります、独自の DSL を定義する DSL 定義ファイルを更新するときに、 `UI` DSL を表示するプロジェクト。 異なり、`Dsl`と`DslPackage`プロジェクトは、サンプル`UI`からプロジェクトが生成されない`DslDefinitionl.dsl`します。 このチュートリアルでは説明しませんが、する場合は、コードを生成する .tt ファイルを追加することができます。

## <a name="updating-the-dsl-definition"></a>DSL 定義の更新
 このチュートリアルでは、DSL 定義を使用してください。 以下。

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png)

#### <a name="to-update-the-dsl-definition"></a>DSL 定義を更新するには

1.  DSL デザイナーで DslDefinition.dsl を開きます。

2.  削除**ExampleElement**

3.  名前の変更、 **ExampleModel**ドメイン クラスを`Farm`します。

     追加のドメイン プロパティの名前を付けます`Size`型の**Int32**、および`IsOrganic`型の**ブール**します。

    > [!NOTE]
    >  ルート ドメイン クラスを削除して新しいルートを作成し、エディターのルート クラスのプロパティをリセットする必要があります。 **DSL エクスプ ローラー**、**エディター**します。 [プロパティ] ウィンドウで次のように設定します。**ルート クラス**に`Farm`します。

4.  使用して、**という名前のドメイン クラス**次のドメイン クラスを作成するツール。

    -   `Field` -付与このという追加のドメイン プロパティ`Size`します。

    -   `Animal` [プロパティ] ウィンドウで次のように設定します。**継承修飾子**に**抽象**します。

5.  使用して、**ドメイン クラス**次のクラスを作成するツール。

    -   `Sheep`

    -   `Goat`

6.  使用して、**継承**ツールを`Goat`と`Sheep`継承`Animal`します。

7.  使用して、**埋め込み**を埋め込むツール`Field`と`Animal``Farm`します。

8.  ダイアグラムを整理することがあります。 重複する要素の数を減らすためには、使用、**サブツリーをここに表示**リーフ要素のショートカット メニューの コマンド。

9. **すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。

10. ビルド、 **Dsl**プロジェクト。

    > [!NOTE]
    >  この段階で、エラーのない他のプロジェクトがビルドされません。 ただし、そのアセンブリをデータ ソース ウィザードを使用できるように、Dsl プロジェクトをビルドします。

## <a name="updating-the-ui-project"></a>UI プロジェクトの更新
 これで、DSL のモデルに格納されている情報を表示する新しいユーザー コントロールを作成できます。 ユーザー コントロールをモデルに接続する最も簡単な方法では、データ バインドを使用します。 データ バインディングという名前のアダプター型**ModelingBindingSource**非 VMSDK インターフェイスへの Dsl の接続には具体的には設計されています。

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>データ ソースとして、DSL モデルを定義するには

1.  **データ** メニューの 選択**データ ソースの**します。

     **データソース**ウィンドウが開きます。

     選択**新しいデータ ソースの追加**します。 **データ ソース構成ウィザード**が開きます。

2.  選択**オブジェクト**、**次**します。

     展開**Dsl**、 **Company.FarmApp**、選び**ファーム**、これは、モデルのルート クラスです。 **[完了]** を選択します。

     ソリューション エクスプ ローラーで、 **UI**プロジェクトが含まれています**Properties\DataSources\Farm.datasource**

     プロパティと、モデル クラスの関係は、データ ソース ウィンドウに表示されます。

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

#### <a name="to-connect-your-model-to-a-form"></a>フォームに、モデルを接続するには

1.  **UI**プロジェクトで、既存のすべての .cs ファイルを削除します。

2.  新しい追加**ユーザー コントロール**という名前のファイル`FarmControl`を**UI**プロジェクト。

3.  **データソース**ウィンドウで、ドロップダウン メニューで **ファーム**、選択**詳細**。

     その他のプロパティの既定の設定のままにします。

4.  FarmControl.cs をデザイン ビューで開きます。

     ドラッグ**ファーム**FarmControl 上にデータ ソース ウィンドウから。

     コントロールのセットが表示されたら、各プロパティのいずれか。 リレーションシップのプロパティでは、コントロールは生成されません。

5.  削除**farmBindingNavigator**します。 これはでも自動的に生成されます、`FarmControl`は、デザイナーにこのアプリケーションに適していません。

6.  2 つのインスタンスを作成して、ツールボックスを使用して**DataGridView**、という名前を付けます`AnimalGridView`と`FieldGridView`します。

    > [!NOTE]
    >  代替の手順は、コントロールにデータ ソース ウィンドウから動物とフィールドの項目をドラッグすることです。 このアクションは、データ グリッドとグリッド ビューとデータ ソース間のバインドに自動的に作成します。 ただし、このバインディングは、Dsl は正しく機能しません。 データ グリッドとバインドを作成することをお勧めそのため手動でします。

7.  ツールボックスが含まれていない場合、 **ModelingBindingSource**ツールで追加します。 ショートカット メニューで、**データ** タブで、選択**アイテムの選択**します。 **ツールボックス アイテムの選択**ダイアログ ボックスで、 **ModelingBindingSource**から、 **.NET Framework タブ**します。

8.  2 つのインスタンスを作成して、ツールボックスを使用して**ModelingBindingSource**、という名前を付けます`AnimalBinding`と`FieldBinding`します。

9. 設定、 **DataSource**の各プロパティ**ModelingBindingSource**に**farmBindingSource**します。

     設定、 **DataMember**プロパティを**動物**または**フィールド**します。

10. 設定、 **DataSource**プロパティの`AnimalGridView`に`AnimalBinding`との`FieldGridView`に`FieldBinding`します。

11. 任意で、ファームのコントロールのレイアウトを調整します。

 **ModelingBindingSource** Dsl に固有のいくつかの機能を実行するアダプターします。

-   VMSDK ストアのトランザクションで更新プログラムをラップします。

     たとえば、ユーザーは、データ ビューのグリッドから行を削除、ときに標準バインディングになりますトランザクション例外。

-   ユーザーは、行を選択するときにデータ グリッドの行ではなく、対応するモデル要素のプロパティが [プロパティ] ウィンドウに表示されますになります。

 ![DslWpf4](../modeling/media/dslwpf4.png)データ ソースとビュー間のリンクのスキーマ。

#### <a name="to-complete-the-bindings-to-the-dsl"></a>DSL へのバインドを完了するには

1.  内の別のコード ファイルで次のコードを追加、 **UI**プロジェクト。

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

2.  **DslPackage**プロジェクトで、編集**DslPackage\DocView.tt**次の変数の定義を更新します。

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>DSL をテストします。
 DSL ソリューションは、ビルドして、機能強化の後で追加したい場合がありますが、実行することができますようになりました。

#### <a name="to-test-the-dsl"></a>DSL をテストするには

1.  ソリューションをビルドして実行します。

2.  Visual Studio の実験用インスタンスを開き、**サンプル**ファイル。

3.  **FarmApp エクスプ ローラー**のショートカット メニューを開き、**ファーム**ルート ノード、および選択**追加新しい Goat**します。

     `Goat1` 表示されます、**動物**ビュー。

    > [!WARNING]
    >  ショートカット メニューを使用する必要があります、**ファーム**ノード、しない、**動物**ノード。

4.  選択、**ファーム**ルート ノードとそのプロパティを表示します。

     フォーム ビューで、**名前**または**サイズ**ファームの。

     [プロパティ] ウィンドウで、対応するプロパティの変更、フォーム内の各フィールドから移動する場合。

## <a name="enhancing-the-dsl"></a>DSL の強化

#### <a name="to-make-the-properties-update-immediately"></a>プロパティをすぐに更新するには

1.  FarmControl.cs のデザイン ビューでは、名前、サイズまたは IsOrganic などの単純なフィールドを選択します。

2.  プロパティ ウィンドウで  **DataBindings**開き **(詳細)**。

     **フォーマットと詳細バインド**ダイアログで、**データ ソース更新モード**、選択**OnPropertyChanged**します。

3.  ソリューションをビルドして実行します。

     ファーム モデルの変更をすぐに対応するプロパティ、フィールドの内容を変更すると、ことを確認します。

#### <a name="to-provide-add-buttons"></a>追加ボタンを提供するには

1.  FarmControl.cs のデザイン ビューで、ツールボックスを使用して、フォームにボタンを作成します。

     たとえば、名前と、ボタンのテキストを編集`New Sheep`します。

2.  (たとえばをダブルクリックして)、ボタンの背後にあるコードを開きます。

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

     また、次のディレクティブを挿入する必要があります。

    ```csharp

    using Microsoft.VisualStudio.Modeling;

    ```

3.  したとフィールドの場合と同様のボタンを追加します。

4.  ソリューションをビルドして実行します。

5.  新しいボタンが項目を追加することを確認します。 FarmApp エクスプ ローラーで、適切なデータ グリッド ビューでは、新しい項目が表示されます。

     データ グリッド ビューで要素の名前を編集する必要があります。 そこから削除することもできます。

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>要素を追加するコードについて
 新しい要素のボタンは、次の代替コードが少し簡単です。

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

 ただし、このコードは、新しい項目の既定の名前を設定できません。 定義した任意のカスタマイズされたマージは実行されません、**要素マージ ディレクティブ**DSL の定義されているコードのカスタムのマージは実行されません。

 使用すること勧めそのため<xref:Microsoft.VisualStudio.Modeling.ElementOperations>新しい要素を作成します。 詳細については、次を参照してください。[をカスタマイズする要素の作成と移動](../modeling/customizing-element-creation-and-movement.md)します。

## <a name="see-also"></a>関連項目

- [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)