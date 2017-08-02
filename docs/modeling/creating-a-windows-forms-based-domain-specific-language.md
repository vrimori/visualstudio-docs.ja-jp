---
title: "Windows フォームに基づくドメイン固有言語の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 17
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c9caf1da3e6e9d065a94e6b12b7699cd5a381ea2
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Windows フォームに基づくドメイン固有言語の作成
Windows フォームを使用すると、DSL 図を使用する代わりに、ドメイン固有言語 (DSL) モデルの状態を表示します。 このトピックは、DSL への Windows フォームのバインドを使用して、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK。  
  
 ![DSL-Wpf-2](~/docs/modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Windows フォームの UI とモデル エクスプ ローラーを示す DSL インスタンス。  
  
## <a name="creating-a-windows-forms-dsl"></a>Windows フォーム DSL を作成します。  
 **最小 WinForm デザイナー** DSL テンプレートは、独自の要件に合わせて変更できる最小限の DSL を作成します。  
  
#### <a name="to-create-a-minimal-winforms-dsl"></a>最小限の WinForms DSL を作成するには  
  
1.  DSL を作成、**最小 WinForm デザイナー**テンプレートです。  
  
     このチュートリアルでは、次の名前が想定しています。  
  
    |||  
    |-|-|  
    |ソリューションと DSL の名前|FarmApp|  
    |Namespace|Company.FarmApp|  
  
2.  テンプレートでは最初の例をテストします。  
  
    1.  すべてのテンプレートを変換します。  
  
    2.  ビルドおよび実行するサンプル (**CTRL + F5**)。  
  
    3.  Visual Studio の実験用インスタンスの開く、`Sample`デバッグ プロジェクト内のファイルです。  
  
         Windows フォーム コントロールで表示されることに注意してください。  
  
         エクスプ ローラーで表示されているモデルの要素を確認することもできます。  
  
         フォームまたはエクスプ ローラーで、いくつかの要素を追加し、その他のディスプレイに表示されることに注意してください。  
  
 メイン インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、DSL ソリューションには、次の点に注意してください。  
  
-   `DslDefinition.dsl`図の要素は含まれません。 この DSL のインスタンス モデルを表示する DSL 図使用しないためにです。 代わりに、Windows フォームは、モデルにバインドして、フォーム上の要素、モデルが表示されます。  
  
-   加え、`Dsl`と`DslPackage`プロジェクトでは、ソリューションに含まれるという名前の&3; つ目のプロジェクト`UI.` **UI**プロジェクトには、Windows フォーム コントロールの定義が含まれています。 `DslPackage`異なります`UI`、および`UI`異なります`Dsl`します。  
  
-   `DslPackage`プロジェクト、`UI\DocView.cs`で定義されている Windows フォーム コントロールを表示するコードを含む、`UI`プロジェクトです。  
  
-   `UI`プロジェクトには、DSL にバインドされたフォーム コントロールの実際のサンプルが含まれています。 ただし、これは機能しません、DSL 定義を変更したとき。 `UI`プロジェクトが含まれています。  
  
    -   という名前の Windows フォーム クラス`ModelViewControl`します。  
  
    -   という名前のファイル`DataBinding.cs`の他の部分定義を含む`ModelViewControl`します。 そのコンテンツを表示する**ソリューション エクスプ ローラー**ファイルのショートカット メニューを開き、選択**コードの表示**します。  
  
### <a name="about-the-ui-project"></a>UI プロジェクトについて  
 内のコントロールを更新する必要が独自の DSL を定義する DSL 定義ファイルを更新すると、 `UI` DSL を表示するプロジェクト。 異なり、`Dsl`と`DslPackage`プロジェクトは、サンプル`UI`からプロジェクトが生成されない`DslDefinitionl.dsl`します。 コードを生成する場合は、このチュートリアルでは説明しませんが .tt ファイルを追加することができます。  
  
## <a name="updating-the-dsl-definition"></a>DSL 定義の更新  
 DSL 定義は、このチュートリアルでは使用します。  
  
 ![DSL-Wpf-1](~/docs/modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  
  
#### <a name="to-update-the-dsl-definition"></a>DSL 定義を更新するには  
  
1.  DSL デザイナーで DslDefinition.dsl を開きます。  
  
2.  削除**ExampleElement**  
  
3.  名前の変更、 **ExampleModel**ドメイン クラスを`Farm`します。  
  
     追加のドメイン プロパティの名前を付けます`Size`型の**Int32**、および`IsOrganic`型の**ブール**します。  
  
    > [!NOTE]
    >  ルート ドメイン クラスを削除して、新しいルートを作成した場合は、エディターのルート クラス プロパティをリセットする必要があります。 **DSL エクスプ ローラー****エディター**します。 [プロパティ] ウィンドウで次のように設定します。**ルート クラス**に`Farm`します。  
  
4.  使用して、**という名前のドメイン クラス**次のドメイン クラスを作成するツール。  
  
    -   `Field`– 以下のことをという名前の追加のドメイン プロパティ`Size`します。  
  
    -   `Animal`-[プロパティ] ウィンドウで、次のように設定します。**継承修飾子**に**抽象**します。  
  
5.  使用して、**ドメイン クラス**次のクラスを作成するツール。  
  
    -   `Sheep`  
  
    -   `Goat`  
  
6.  使用して、**継承**ツールを`Goat`と`Sheep`から継承`Animal`します。  
  
7.  使用して、**埋め込み**を埋め込むツール`Field`と`Animal``Farm`します。  
  
8.  ダイアグラムを整理することがあります。 重複する要素の数を軽減するために、**サブツリーをここに表示**リーフ要素のショートカット メニューのです。  
  
9. **すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバーにします。  
  
10. ビルド、 **Dsl**プロジェクトです。  
  
    > [!NOTE]
    >  この段階で、他のプロジェクトがエラーなくビルドできません。 ただし、そのアセンブリをデータ ソース ウィザードを使用できるように、Dsl プロジェクトをビルドしてみます。  
  
## <a name="updating-the-ui-project"></a>UI プロジェクトの更新  
 これで、DSL モデルに格納されている情報を表示する新しいユーザー コントロールを作成できます。 ユーザー コントロールをモデルに接続する最も簡単な方法では、データ バインドを使用します。 データ バインディングという名前のアダプター型**ModelingBindingSource** VMSDK 以外のインターフェイスに Dsl を接続するように設計されます。  
  
#### <a name="to-define-your-dsl-model-as-a-data-source"></a>データ ソースとして、DSL モデルを定義するには  
  
1.  **データ** メニューの 選択**データ ソースの**です。  
  
     **データソース**ウィンドウが開きます。  
  
     選択**新しいデータ ソースの追加**します。 **データ ソース構成ウィザード**が開きます。  
  
2.  選択**オブジェクト**、**次**します。  
  
     展開**Dsl**、 **Company.FarmApp**を選択して**ファーム**、これは、モデルのルート クラスです。 選択**完了**します。  
  
     ソリューション エクスプ ローラーで、 **UI**プロジェクトが含まれ**Properties\DataSources\Farm.datasource**  
  
     プロパティと、モデル クラスの関係は、データ ソース ウィンドウに表示されます。  
  
     ![DslWpf&3;](~/docs/modeling/media/dslwpf-3.png "DslWpf&3;")  
  
#### <a name="to-connect-your-model-to-a-form"></a>フォームに、モデルを接続するには  
  
1.  **UI**プロジェクトで、既存のすべての .cs ファイルを削除します。  
  
2.  新しい**ユーザー コントロール**という名前のファイル`FarmControl`に、 **UI**プロジェクトです。  
  
3.  **データ ソース**ウィンドウで、ドロップダウン メニューで **ファーム**、選択**詳細**します。  
  
     その他のプロパティの既定の設定のままにします。  
  
4.  デザイン ビューで FarmControl.cs を開きます。  
  
     ドラッグ**ファーム**FarmControl の [データ ソース] ウィンドウからです。  
  
     コントロールのセットが表示されたら、各プロパティのいずれかです。 リレーションシップのプロパティは、コントロールを生成しません。  
  
5.  削除**farmBindingNavigator**します。 これがも自動的に生成、`FarmControl`は、デザイナーにこのアプリケーションに適していません。  
  
6.  2 つのインスタンスを作成して、ツールボックスを使用して**DataGridView**、という名前を付けます`AnimalGridView`と`FieldGridView`です。  
  
    > [!NOTE]
    >  代替の手順では、コントロールにデータ ソース ウィンドウから動物とフィールドの項目をドラッグします。 この操作は、データ グリッドとグリッド ビューとデータ ソースの間のバインドに自動的に作成されます。 ただし、このバインディングが正しく機能しないの Dsl にします。 そのために、データ グリッドとバインドを作成する方が手動でします。  
  
7.  ツールボックスに含まれない場合、 **ModelingBindingSource**ツールで追加します。 ショートカット メニューを開き、**データ** タブで、選択**アイテムの選択**します。 **ツールボックス アイテムの選択**ダイアログで、 **ModelingBindingSource**から、 **.NET Framework タブ**します。  
  
8.  2 つのインスタンスを作成して、ツールボックスを使用して**ModelingBindingSource**、という名前を付けます`AnimalBinding`と`FieldBinding`です。  
  
9. 設定、**データソース**の各プロパティ**ModelingBindingSource**に**farmBindingSource**します。  
  
     設定、 **DataMember**プロパティを**動物**または**フィールド**します。  
  
10. 設定、**データソース**のプロパティ`AnimalGridView`に`AnimalBinding`、および`FieldGridView`に`FieldBinding`します。  
  
11. 任意で、ファームのコントロールのレイアウトを調整します。  
  
 **ModelingBindingSource** Dsl に固有のいくつかの機能を実行するアダプターします。  
  
-   VMSDK ストアのトランザクションで更新プログラムをラップします。  
  
     たとえば、ユーザーは、データ ビューのグリッドから行を削除、標準バインディングはトランザクション例外で表示されません。  
  
-   これにより、ユーザーは、行を選択するときに [プロパティ] ウィンドウが表示されるデータ グリッドの行ではなく、対応するモデル要素のプロパティ。  
  
 ![DslWpf4](~/docs/modeling/media/dslwpf4.png "DslWpf4")  
データ ソースおよびビュー間のリンクのスキーマです。  
  
#### <a name="to-complete-the-bindings-to-the-dsl"></a>DSL へのバインドを完了するには  
  
1.  別のコード ファイルに次のコードを追加、 **UI**プロジェクト。  
  
    ```c#  
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
  
2.  **DslPackage**プロジェクトで、編集**DslPackage\DocView.tt**を次の変数の定義を更新します。  
  
    ```c#  
    string viewControlTypeName = "FarmControl";  
    ```  
  
## <a name="testing-the-dsl"></a>DSL をテストします。  
 DSL ソリューションを構築し、改善を後で追加さらにすることができますが、実行今すぐできます。  
  
#### <a name="to-test-the-dsl"></a>DSL をテストするには  
  
1.  ソリューションをビルドして実行します。  
  
2.  Visual Studio の実験用インスタンスの開く、**サンプル**ファイルです。  
  
3.  **FarmApp エクスプ ローラー**のショートカット メニューを開き、**ファーム**ルート ノード、および選択**追加新しいヤギ**します。  
  
     `Goat1`表示されます、**動物**表示します。  
  
    > [!WARNING]
    >  ショートカット メニューを使用する必要があります、**ファーム**ノードでない、**動物**ノードです。  
  
4.  選択、**ファーム**ルート ノードとそのプロパティを表示します。  
  
     フォーム ビューでは、変更、**名**または**サイズ**ファームのです。  
  
     フォームで、[プロパティ] ウィンドウで対応するプロパティの変更には、各フィールドから移動するとします。  
  
## <a name="enhancing-the-dsl"></a>DSL の強化  
  
#### <a name="to-make-the-properties-update-immediately"></a>直ちに更新プロパティ  
  
1.  FarmControl.cs のデザイン ビューでは、名前、サイズまたは IsOrganic などの単純なフィールドを選択します。  
  
2.  プロパティ ウィンドウで  **DataBindings**開き**(詳細)**します。  
  
     **フォーマットと詳細バインド**ダイアログで、**データ ソースの更新モード**、選択**OnPropertyChanged**します。  
  
3.  ソリューションをビルドして実行します。  
  
     ファーム モデルの変更をすぐに対応するプロパティ、フィールドの内容を変更するときに、点を確認します。  
  
#### <a name="to-provide-add-buttons"></a>追加ボタンを提供するには  
  
1.  FarmControl.cs のデザイン ビューで、ツールボックスを使用して、フォームにボタンを作成します。  
  
     名前と、ボタンのテキストを次に例を編集`New Sheep`します。  
  
2.  (たとえばをダブルクリックして)、ボタンの背後にコードを開きます。  
  
     次のように編集します。  
  
    ```c#  
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
  
     また、次のディレクティブを挿入する必要になります。  
  
    ```c#  
  
    using Microsoft.VisualStudio.Modeling;  
  
    ```  
  
3.  フィールドとしたのと同様のボタンを追加します。  
  
4.  ソリューションをビルドして実行します。  
  
5.  新しいボタンが項目を追加することを確認します。 FarmApp エクスプ ローラーで、適切なデータ グリッド ビューでは、新しい項目が表示されます。  
  
     データ グリッド ビュー内の要素の名前を編集することができます。 そこからも削除できます。  
  
 ![DSL Wpf&2;](~/docs/modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
  
### <a name="about-the-code-to-add-an-element"></a>要素を追加するコードについて  
 新しい要素のボタン、次の代替のコードはやや簡単です。  
  
```c#  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  
  
```  
  
 ただし、このコードでは、新しい項目の既定の名前は設定されません。 定義したすべてのカスタマイズされたマージを実行することはない、**要素マージ ディレクティブ**DSL の定義されているカスタムのマージのコードは実行されません。  
  
 使用すること勧めしたがって<xref:Microsoft.VisualStudio.Modeling.ElementOperations>新しい要素を作成します</xref:Microsoft.VisualStudio.Modeling.ElementOperations>。 詳細については、次を参照してください。[をカスタマイズする要素の作成と移動](../modeling/customizing-element-creation-and-movement.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modeling SDK for Visual Studio - ドメイン固有言語](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
