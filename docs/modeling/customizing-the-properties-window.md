---
title: "[プロパティ] ウィンドウをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, Properties window
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: "20"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 962b4a8eac0d548d2c7a337207644bdc717fe3cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-the-properties-window"></a>プロパティ ウィンドウのカスタマイズ
カスタマイズできますプロパティ ウィンドウの動作と外観、ドメイン固有言語 (DSL) で[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 DSL 定義では、各ドメイン クラスにドメインのプロパティを定義します。 既定では、図に、またはモデル エクスプ ローラーで、クラスのインスタンスを選択するすべてのドメイン プロパティは [プロパティ] ウィンドウで表示されます。 これにより確認し、ドメインのプロパティの値を編集する場合でも、ダイアグラムで図形のフィールドをマップしているされません。  
  
## <a name="names-descriptions-and-categories"></a>名前、説明、およびカテゴリ  
 **名前と表示名**です。 ドメイン プロパティの定義では、プロパティの表示名は、[プロパティ] ウィンドウで実行時に表示される名前です。 これに対し、名前は、プロパティを更新するプログラム コードを記述する場合に使用されます。 名前が正しい CLR 英数字名前にする必要がありますが、表示名にスペースを含めることができます。  
  
 DSL 定義で、プロパティの名前を設定するときの表示名は自動的に名前のコピーに設定します。 "FuelGauge"など pascal 形式で大文字と小文字の名前を記述すると、表示名が自動的に入力する場所:「燃料計」です。 ただし、別の値に表示名を明示的に設定できます。  
  
 **説明**です。 ドメイン プロパティの説明は、2 つの場所が表示されます。  
  
-   で、ユーザーが、プロパティを選択したときに、[プロパティ] ウィンドウの下部です。 ユーザーに説明するプロパティが何を表すためには、それを使用できます。  
  
-   生成されたプログラム コード。 API のドキュメントを抽出するドキュメントの機能を使用する場合は、このプロパティは、API での説明として表示されます。  
  
 **カテゴリ**。 カテゴリは、[プロパティ] ウィンドウの見出しです。  
  
## <a name="exposing-style-features"></a>スタイル機能を公開します。  
 グラフィック要素の動的機能の一部を表すことができますか*公開*ドメインのプロパティとして。 ユーザーがこの方法で公開されている機能を更新してより簡単に更新できる、プログラム コード。  
  
 DSL 定義内の図形のクラスを右クリックし、順にポイント**公開追加**機能を選択します。  
  
 図形の上に公開する、**れた**、**囲んで**、 **TextColor**、 **OutlineDashStyle**、 **OutlineThickness**と**FillGradientMode**プロパティです。 コネクタで公開することができます、**色**`,`**TextColor**、 **DashStyle**、および**太さ**プロパティです。 ダイアグラムで公開することができます、**れた**と**TextColor**プロパティです。  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>: 転送に関連する要素のプロパティを表示します。  
 DSL のユーザーは、モデル内の要素を選択するときにその要素のプロパティは、[プロパティ] ウィンドウに表示されます。 ただし、指定された関連する要素のプロパティを表示することもできます。 これが連携している要素のグループを定義している場合に便利です。 たとえば、主要な要素と省略可能なプラグイン要素を定義できます。 Main 要素は、図形にマップがない場合は、場合と同様に 1 つの要素は、すべてのプロパティを表示すると便利です。  
  
 この特殊効果の名前は*プロパティ転送*、し、いくつかのケースでは自動的に実行します。 その他の場合、プロパティは、ドメインの型記述子を定義することで転送を実現できます。  
  
### <a name="default-property-forwarding-cases"></a>既定のプロパティの転送の場合  
 ユーザーは、エクスプ ローラーで、図形またはコネクタ、または要素を選択するときに、[プロパティ] ウィンドウで、次のプロパティが表示されます。  
  
-   基本クラスで定義されたものも含め、モデル要素のドメイン クラスで定義されているドメインのプロパティです。 例外は、ドメインのプロパティを設定する**は参照可能な**に`False`です。  
  
-   0..1 の多重度のリレーションシップからリンクされている要素の名前。 これにより、必要に応じて表示を簡単に、要素がリンクされているコネクタのマッピングのリレーションシップを定義していない場合でもです。  
  
-   要素を対象とする埋め込みリレーションシップのドメインのプロパティです。 通常埋め込みリレーションシップは明示的に表示されないためこれにより、そのプロパティを参照してください。  
  
-   選択した図形またはコネクタで定義されているドメインのプロパティです。  
  
### <a name="adding-property-forwarding"></a>プロパティの転送を追加します。  
 プロパティを転送するには、ドメインの型記述子を定義します。 2 つのドメイン クラス間でドメインの関係がある場合は場合、は、2 番目のドメイン クラス内のドメイン プロパティの値に最初のクラスでドメインのプロパティを設定するドメインの型記述子を使用できます。 間のリレーションシップがある場合など、 **Book**ドメイン クラスおよび**作成者**ドメイン クラスをドメインの型記述子を使用することができます、**名前**のプロパティ、ブックの**作成者**書籍を選択すると、[プロパティ] ウィンドウに表示されます。  
  
> [!NOTE]
>  プロパティの転送は、ユーザーが、モデルを編集するときのプロパティ ウィンドウのみに影響します。 ドメイン プロパティは、受信側のクラスでは定義しません。 DSL 定義の他の部分、またはプログラム コードでは、転送されたドメイン プロパティにアクセスする場合は、転送の要素にアクセスする必要があります。  
  
 次の手順では、DSL が作成されたことを前提としています。 最初のいくつかの手順では、前提条件をまとめています。  
  
##### <a name="to-forward-a-property-from-another-element"></a>他の要素からプロパティを転送するには  
  
1.  作成、[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]をこの例と呼ばれるには、少なくとも 2 つのクラスを含むソリューションを**Book**と**作成者**です。 どちらの種類の間のリレーションシップが存在する必要があります**Book**と**作成者**です。  
  
     ソース ロールの多重度 (のロール、 **Book**側) 0..1 または 1..1、する必要がありますので各**Book**が 1 つ**作成者**です。  
  
2.  **DSL のエクスプ ローラー**を右クリックし、 **Book**ドメイン クラス、およびクリック**新しい DomainTypeDescriptor の追加**です。  
  
     という名前のノード**カスタム プロパティ記述子のパス**下に表示されます、**カスタム型記述子**ノード。  
  
3.  右クリックし、**カスタム型記述子**ノードをクリックして**追加新しい PropertyPath**です。  
  
     下に新しいプロパティのパスが表示されます、**カスタム プロパティ記述子のパス**ノード。  
  
4.  新しいプロパティのパスを選択し、、**プロパティ**ウィンドウで、設定**プロパティへのパス**適切なモデル要素のパスにします。  
  
     ツリー ビューのパスを編集するには、このプロパティの右側にある下向きの矢印をクリックします。 ドメイン パスの詳細については、次を参照してください。[ドメイン パス構文](../modeling/domain-path-syntax.md)です。 パスのようになります終えたら、 **BookReferencesAuthor.Author/!作成者**です。  
  
5.  設定**プロパティ**を**名前**のドメイン プロパティ**作成者**です。  
  
6.  設定**表示名**に**作成者名**です。  
  
7.  すべてのテンプレートの変換、ビルドおよび実行 DSL です。  
  
8.  モデル図の作成者は、本を作成し、参照リレーションシップを使用してそれらをリンクします。 Book 要素を選択し、[プロパティ] ウィンドウでは、ブックのプロパティだけでなく作成者の名前が表示されます。 リンクの作成者の名前を変更または 別の著者を book をリンクを book の作成者の名前が変更されているを確認します。  
  
## <a name="custom-property-editors"></a>カスタム プロパティ エディター  
 [プロパティ] ウィンドウは、適切な既定のドメインの各プロパティの型を使用したエディターを提供します。 たとえば、列挙型、ユーザーはドロップダウン リストでは、しを数値プロパティのユーザーが数字を入力できます。 これは、組み込み型の場合は true のみです。 外部型を指定すると、ユーザーはプロパティの値を参照しても編集できないことになります。  
  
 ただし、次のエディターと型を指定できます。  
  
1.  標準の型で使用される他のエディターです。 たとえば、文字列プロパティのファイル パス エディターを指定できます。  
  
2.  ドメイン プロパティとそのエディターの外部の型。  
  
3.  ファイル パスのエディターなどの .NET エディターは、独自のカスタム プロパティ エディターを作成できます。  
  
     外部型と既定のエディターを持つ文字列など、型の間で変換します。  
  
 DSL で、*外部タイプ*(ブール値を Int32 など) の単純型または文字列のいずれかではない型であります。  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>外部の型を持つドメイン プロパティを定義するには  
  
1.  **ソリューション エクスプ ローラー**で外部の型を格納しているアセンブリ (DLL) への参照を追加、 **Dsl**プロジェクト。  
  
     アセンブリには、.NET アセンブリ、またはユーザーによって指定されたアセンブリを指定できます。  
  
2.  種類を追加、**ドメイン型**したがまだ完了していない限り、一覧表示します。  
  
    1.  開く DslDefinition.dsl、し、 **DSL のエクスプ ローラー**をルート ノードを右クリックし、をクリックして**新しい外部型の追加**です。  
  
         下に新しいエントリが表示されます、**ドメイン型**ノード。  
  
        > [!WARNING]
        >  メニュー項目が、DSL のルート ノードで、**ドメイン型**ノード。  
  
    2.  [プロパティ] ウィンドウで、名前と、新しい種類の名前空間を設定します。  
  
3.  ドメイン クラスに通常の方法でドメインのプロパティを追加します。  
  
     [プロパティ] ウィンドウでのドロップ ダウン リストから外部の型を選択、**型**フィールドです。  
  
 この段階では、ユーザーは、プロパティの値を表示できますが、編集はできません。 表示されている値がから取得した、`ToString()`関数。 コマンドまたはルールで、たとえば、プロパティの値を設定するプログラム コードを記述することもできます。  
  
### <a name="setting-a-property-editor"></a>プロパティ エディターの設定  
 次の形式での domain プロパティには、CLR 属性を追加します。  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 使用してプロパティの属性を設定することができます、**カスタム属性**プロパティ ウィンドウで入力します。  
  
 型`AnEditor`2 番目のパラメーターで指定された型から派生する必要があります。 2 番目のパラメーターはいずれかにする必要があります<xref:System.Drawing.Design.UITypeEditor>または<xref:System.ComponentModel.ComponentEditor>です。 詳細については、「<xref:System.ComponentModel.EditorAttribute>」を参照してください。  
  
 独自のエディターまたはで指定されたエディターのいずれかを指定することができます、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]など<xref:System.Windows.Forms.Design.FileNameEditor>または<xref:System.Drawing.Design.ImageEditor>です。 たとえば、次の手順を使用して、プロパティが、ユーザーがファイル名を入力できます。  
  
##### <a name="to-define-a-file-name-domain-property"></a>ファイル名のドメインのプロパティを定義するには  
  
1.  ドメインのプロパティを DSL 定義内のドメイン クラスに追加します。  
  
2.  新しいプロパティを選択します。 **カスタム属性**プロパティ ウィンドウでフィールドに、次の属性を入力します。 この属性を入力するには、省略記号ボタンをクリックして**[...]**し、属性名とパラメーターを個別に入力します。  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  ドメイン プロパティの型の既定の設定のままにして**文字列**です。  
  
4.  エディターをテストするには、ユーザーが、ドメインのプロパティを編集するファイル名のエディターを開くことができますを確認します。  
  
    1.  Ctrl キーを押しながら f5 キーまたは f5 キーを押します。 ソリューションでは、デバッグ、テスト ファイルを開きます。 ドメイン クラスの要素を作成し、それを選択します。  
  
    2.  [プロパティ] ウィンドウでは、ドメインのプロパティを選択します。 [値] フィールドは、省略記号を示しています**[...]。**.  
  
    3.  省略記号ボタンをクリックします。 ファイル ダイアログ ボックスが表示されます。 ファイルを選択し、ダイアログ ボックスを閉じます。 ファイルのパスは、今すぐドメイン プロパティの値です。  
  
### <a name="defining-your-own-property-editor"></a>独自のプロパティ エディターを定義します。  
 独自のエディターを定義することができます。 これを使用する、ユーザーを定義する型を編集するか、特殊な方法で、標準型を編集するかを実行します。 たとえば、数式を表す文字列を入力するユーザーを許可する可能性があります。  
  
 派生したクラスを記述してエディターを定義する<xref:System.Drawing.Design.UITypeEditor>です。 クラスをオーバーライドする必要があります。  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>、ユーザーと対話し、プロパティの値を更新します。  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>、、エディター、ダイアログを開くか、ドロップダウン メニューを提供するかどうかを指定します。  
  
 プロパティのグリッドに表示されるプロパティの値のグラフィカル表現を指定することもできます。 これを行うには、オーバーライド`GetPaintValueSupported`、および`PaintValue`です。  詳細については、「<xref:System.Drawing.Design.UITypeEditor>」を参照してください。  
  
> [!NOTE]
>  個別のコード ファイル内でコードを追加、 **Dsl**プロジェクト。  
  
 例:  
  
```  
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor  
{  
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)  
  {  
    base.InitializeDialog(openFileDialog);  
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";  
    openFileDialog.Title = "Select a text file";  
  }  
}  
  
```  
  
 このエディターを使用する設定、**カスタム属性**ドメインのプロパティの。  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 詳細については、「<xref:System.Drawing.Design.UITypeEditor>」を参照してください。  
  
## <a name="providing-a-drop-down-list-of-values"></a>値のドロップダウン リストを提供します。  
 選択するユーザーの値の一覧を指定することができます。  
  
> [!NOTE]
>  この手法は、実行時に変更できる値の一覧を示します。 変化しない一覧を指定する場合は、代わりに検討してください、ドメインのプロパティの型として列挙型を使用します。  
  
 標準値のリストを定義するには、プロパティに追加する、ドメインを次の形式を持つ CLR 属性。  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 <xref:System.ComponentModel.TypeConverter> から派生するクラスを定義します。 別のファイルにコードを追加、 **Dsl**プロジェクト。 例:  
  
```csharp  
/// <summary>  
/// Type converter that provides a list of values   
/// to be displayed in the property grid.  
/// </summary>  
/// <remarks>This type converter returns a list   
/// of the names of all "ExampleElements" in the   
/// current store.</remarks>  
public class MyTypeConverter : System.ComponentModel.TypeConverter  
{  
  /// <summary>  
  /// Return true to indicate that we return a list of values to choose from  
  /// </summary>  
  /// <param name="context"></param>  
  public override bool GetStandardValuesSupported  
    (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Returns true to indicate that the user has   
  /// to select a value from the list  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>If we returned false, the user would   
  /// be able to either select a value from   
  /// the list or type in a value that is not in the list.</returns>  
  public override bool GetStandardValuesExclusive  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Return a list of the values to display in the grid  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>A list of values the user can choose from</returns>  
  public override StandardValuesCollection GetStandardValues  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    // Try to get a store from the current context  
    // "context.Instance"  returns the element(s) that   
    // are currently selected i.e. whose values are being  
    // shown in the property grid.   
    // Note that the user could have selected multiple objects,   
    // in which case context.Instance will be an array.  
    Store store = GetStore(context.Instance);  
  
    List<string> values = new List<string>();  
  
    if (store != null)  
    {  
      values.AddRange(store.ElementDirectory  
        .FindElements<ExampleElement>()  
        .Select<ExampleElement, string>(e =>   
      {  
        return e.Name;  
      }));  
    }  
    return new StandardValuesCollection(values);  
  }  
  
  /// <summary>  
  /// Attempts to get to a store from the currently selected object(s)  
  /// in the property grid.  
  /// </summary>  
  private Store GetStore(object gridSelection)  
  {  
    // We assume that "instance" will either be a single model element, or   
    // an array of model elements (if multiple items are selected).  
  
    ModelElement currentElement = null;  
  
    object[] objects = gridSelection as object[];  
    if (objects != null && objects.Length > 0)  
    {  
      currentElement = objects[0] as ModelElement;  
    }  
    else  
    {  
        currentElement = gridSelection as ModelElement;  
    }  
  
    return (currentElement == null) ? null : currentElement.Store;  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>関連項目  
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)