---
title: プロパティ ウィンドウのカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, Properties window
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: aa690b88b5ab2d7aac3f8aea9967419dcbd43df1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241736"
---
# <a name="customizing-the-properties-window"></a>プロパティ ウィンドウのカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

カスタマイズできますプロパティ ウィンドウの動作と外観をドメイン固有言語 (DSL) で[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 DSL 定義では、各ドメイン クラスのドメインのプロパティを定義します。 既定では、図またはモデル エクスプ ローラーで、クラスのインスタンスを選択するとすべてのドメイン プロパティが [プロパティ] ウィンドウに表示されます。 これにより、ドメイン プロパティの値を編集するダイアグラムで図形のフィールドにマップするがいない場合でもできます。  
  
## <a name="names-descriptions-and-categories"></a>名前、説明、およびカテゴリ  
 **名前と表示名**します。 ドメイン プロパティの定義では、プロパティの表示名は、[プロパティ] ウィンドウで実行時に表示される名前です。 これに対し、名前は、プロパティを更新するプログラム コードを記述するときに使用されます。 名前は、適切な CLR の英数字名をする必要がありますが、表示名にスペースを含めることができます。  
  
 DSL 定義で、プロパティの名前を設定するとその表示名は自動的に名前のコピーに設定します。 "FuelGauge"など、pascal 形式の大文字と小文字名を記述する場合、表示名が自動的にスペースを含める:「燃料計」。 ただし、別の値を表示名を明示的に設定できます。  
  
 **説明**です。 ドメイン プロパティの説明は、2 つの場所が表示されます。  
  
-   ユーザーのプロパティを選択するときに、[プロパティ] ウィンドウの下部にあります。 プロパティの意味をユーザーに説明を使用できます。  
  
-   生成するプログラム コード。 API のドキュメントを抽出するドキュメントの機能を使用する場合は、API では、このプロパティの説明として表示されます。  
  
 **カテゴリ**。 カテゴリは、[プロパティ] ウィンドウの見出しです。  
  
## <a name="exposing-style-features"></a>スタイルの機能を公開します。  
 表現できるいくつかのグラフィカル要素の動的機能または*公開*ドメインのプロパティとして。 ユーザーがこの方法で公開されている機能を更新してより簡単に更新できるプログラム コード。  
  
 DSL 定義内の図形クラスを右クリックし、**公開追加**機能を選択します。  
  
 図形に公開することができます、 **FillColor**、 **OutlineColor**、 **TextColor**、 **OutlineDashStyle**、 **OutlineThickness**と**FillGradientMode**プロパティ。 コネクタで公開することができます、**色**`,`**TextColor**、 **DashStyle**、および**太さ**プロパティ。 ダイアグラムで公開することができます、 **FillColor**と**TextColor**プロパティ。  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>転送: 関連要素のプロパティを表示します。  
 DSL のユーザーは、モデル内の要素を選択するときに、[プロパティ] ウィンドウでその要素のプロパティが表示されます。 ただし、指定された関連する要素のプロパティを表示することもできます。 これは、連携する要素のグループを定義している場合に便利です。 たとえば、主な要素と省略可能なプラグインの要素を定義する可能性があります。 主な要素を図形にマップされますがない場合は、すべてのプロパティを参照してくださいか 1 つの要素上にいるかのように便利です。  
  
 この効果の名前は*プロパティ転送*、いくつかのケースでは自動的に実行するとします。 それ以外の場合は、プロパティのドメイン型記述子を定義することで転送を実現できます。  
  
### <a name="default-property-forwarding-cases"></a>プロパティの既定の転送ケース  
 ユーザーは、エクスプ ローラーで、図形またはコネクタ、または要素を選択するときに、[プロパティ] ウィンドウで、次のプロパティが表示されます。  
  
-   基底クラスで定義されているものも含め、モデル要素のドメイン クラスで定義されているドメインのプロパティ。 例外は、ドメインのプロパティを設定する**参照可能**に`False`します。  
  
-   0..1 の多重度を持つリレーションシップをリンクされている要素の名前。 これにより、必要に応じて表示の便利なメソッドには、要素がリンクされている場合でも、リレーションシップのコネクタのマッピングが定義されていません。  
  
-   要素を対象とする埋め込みリレーションシップのドメインのプロパティ。 通常、埋め込みリレーションシップが明示的に表示されないため、これにより、ユーザーがそのプロパティを参照してくださいです。  
  
-   選択した図形またはコネクタで定義されているドメインのプロパティ。  
  
### <a name="adding-property-forwarding"></a>プロパティの転送を追加します。  
 プロパティを転送するには、ドメインの型記述子を定義します。 2 つのドメイン クラス間のドメイン リレーションシップがある場合は、2 つ目のドメイン クラス内のドメイン プロパティの値に最初のクラスにドメイン プロパティを設定するドメイン型記述子を使用できます。 間のリレーションシップがある場合など、**帳**ドメイン クラスと**作成者**ドメイン クラスにするドメイン型記述子を使用することができます、**名前**のプロパティをこの本の**作成者**ユーザーが本を選択すると、[プロパティ] ウィンドウに表示されます。  
  
> [!NOTE]
>  プロパティの転送は、ユーザーがモデルを編集するときに、プロパティ ウィンドウのみに影響します。 ドメイン プロパティは、受信側のクラスでは定義しません。 DSL 定義の他の部分で、またはプログラム コードでは、転送されたドメイン プロパティにアクセスする場合は、転送の要素にアクセスする必要があります。  
  
 次の手順では、DSL を作成することを前提としています。 最初のほとんどの手順では、前提条件を示しません。  
  
##### <a name="to-forward-a-property-from-another-element"></a>別の要素からプロパティを転送するには  
  
1.  作成、[!INCLUDE[dsl](../includes/dsl-md.md)]この例でと呼ばれるには少なくとも 2 つのクラスを含むソリューションを**帳**と**作成者**します。 いずれかの種類の間の関係が存在する必要があります**帳**と**作成者**します。  
  
     ソース ロールの多重度 (のロール、**書籍**側) 0..1 または 1..1、する必要がありますのでそれぞれ**帳**に 1 つ**作成者**します。  
  
2.  **DSL エクスプ ローラー**を右クリックし、**帳**ドメイン クラス、およびクリック**新しい {0} の domaintypedescriptor での追加**します。  
  
     という名前のノード**カスタム プロパティ記述子のパス**下に表示されます、**カスタム型記述子**ノード。  
  
3.  右クリックし、**カスタム型記述子**ノードをクリック**追加新しい PropertyPath**します。  
  
     下に新しいプロパティのパスが表示されます、**カスタム プロパティ記述子のパス**ノード。  
  
4.  新しいプロパティのパスを選択し、**プロパティ**ウィンドウで、設定**プロパティへのパス**適切なモデル要素のパスにします。  
  
     ツリー ビュー内のパスを編集するには、このプロパティの右側の下矢印をクリックします。 ドメイン パスの詳細については、次を参照してください。[ドメイン パス構文](../modeling/domain-path-syntax.md)します。 編集したときに、パスのようになります**BookReferencesAuthor.Author/!作成者**します。  
  
5.  設定**プロパティ**を**名前**のドメイン プロパティ**作成者**します。  
  
6.  設定**表示名**に**作成者名**します。  
  
7.  すべてのテンプレートの変換、ビルドおよび DSL を実行します。  
  
8.  モデルの図では、書籍、作成者を作成し、参照リレーションシップを使用してそれらをリンクします。 Book 要素を選択し、[プロパティ] ウィンドウでは、ブックのプロパティだけでなく作成者の名前を表示する必要があります。 リンクの作成者の名前を変更または ブックにリンクする別の著者をブックの作成者の名前が変更を確認します。  
  
## <a name="custom-property-editors"></a>カスタム プロパティ エディター  
 [プロパティ] ウィンドウでは、各ドメイン プロパティの型のエクスペリエンスを編集する適切な既定を提供します。 たとえば、列挙型では、ユーザーには、ボックスの一覧が表示されます。 し数値プロパティの場合、ユーザーが桁の数字を入力できます。 組み込み型の場合のみです。 外部の型を指定する場合、ユーザーは同じにして、プロパティの値も編集できないことができます。  
  
 ただし、次のエディターと型を指定できます。  
  
1.  標準の型で使用される別のエディター。 たとえば、文字列プロパティのファイル パス エディターを指定できます。  
  
2.  ドメイン プロパティとそのエディターの外部の型。  
  
3.  または、ファイル パスのエディターなどの .NET エディターは、独自のカスタム プロパティ エディターを作成できます。  
  
     外部型と文字列が既定のエディターなど、型の間の変換。  
  
 DSL で、*外部型*は単純型 (Boolean、Int32 など) または文字列のいずれかではない任意の型。  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>外部の型を持つドメイン プロパティを定義するには  
  
1.  **ソリューション エクスプ ローラー**での外部の型を含むアセンブリ (DLL) への参照を追加、 **Dsl**プロジェクト。  
  
     アセンブリには、.NET アセンブリ、または自分で指定されたアセンブリを指定できます。  
  
2.  型を追加、**ドメイン型**既に同意している場合を除き、一覧表示します。  
  
    1.  DslDefinition.dsl を開き、 **DSL エクスプ ローラー**ルート ノードを右クリックし、クリックして**外部型の新しい追加**します。  
  
         下に新しいエントリが表示されます、**ドメイン型**ノード。  
  
        > [!WARNING]
        >  メニュー項目がない、DSL のルート ノードで、**ドメイン型**ノード。  
  
    2.  [プロパティ] ウィンドウで、名前と、新しい種類の名前空間を設定します。  
  
3.  通常の方法で、ドメイン クラスにドメイン プロパティを追加します。  
  
     [プロパティ] ウィンドウで、ドロップダウン リストから外部の種類を選択します。、**型**フィールド。  
  
 この段階では、ユーザーは、プロパティの値を表示できますが、編集はできません。 表示されている値がから取得した、`ToString()`関数。 コマンドまたはルールで、たとえば、プロパティの値を設定するプログラム コードを記述できます。  
  
### <a name="setting-a-property-editor"></a>プロパティ エディターの設定  
 次の形式でドメイン プロパティの CLR 属性を追加します。  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 使用してプロパティに属性を設定することができます、**カスタム属性**プロパティ ウィンドウ内のエントリ。  
  
 型`AnEditor`2 番目のパラメーターで指定された型から派生する必要があります。 2 番目のパラメーターはいずれかになります<xref:System.Drawing.Design.UITypeEditor>または<xref:System.ComponentModel.ComponentEditor>します。 詳細については、「 <xref:System.ComponentModel.EditorAttribute> 」を参照してください。  
  
 独自のエディターまたはで指定されたエディターのいずれかを指定することができます、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]など<xref:System.Windows.Forms.Design.FileNameEditor>または<xref:System.Drawing.Design.ImageEditor>します。 たとえば、ユーザーがファイル名を入力できるプロパティを持つ、次の手順を使用します。  
  
##### <a name="to-define-a-file-name-domain-property"></a>ファイル名のドメイン プロパティを定義するには  
  
1.  ドメイン プロパティを DSL 定義内のドメイン クラスに追加します。  
  
2.  新しいプロパティを選択します。 **カスタム属性**プロパティ ウィンドウでフィールドに、次の属性を入力します。 この属性を入力する、省略記号ボタンをクリックします **[...]。** し、属性名とパラメーターを個別に入力します。  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  ドメイン プロパティの型の既定の設定のままにして**文字列**します。  
  
4.  エディターをテストするには、ユーザーが、ドメイン プロパティを編集するファイル名のエディターを開くことを確認します。  
  
    1.  Ctrl キーを押しながら f5 キーまたは f5 キーを押します。 デバッグのソリューションでは、テスト ファイルを開きます。 ドメイン クラスの要素を作成し、それを選択します。  
  
    2.  [プロパティ] ウィンドウでは、ドメイン プロパティを選択します。 [値] フィールドは、省略記号を示しています **[...]**。  
  
    3.  省略記号をクリックします。 ファイル ダイアログ ボックスが表示されます。 ファイルを選択し、ダイアログ ボックスを閉じます。 ファイル パスは、ドメイン プロパティの値ではようになりました。  
  
### <a name="defining-your-own-property-editor"></a>独自のプロパティ エディターを定義します。  
 独自のエディターを定義することができます。 いずれかを定義する型を編集したり、特別な方法で標準の型を編集するユーザーを許可するように行います。 たとえば、数式を表す文字列を入力するユーザーを許可する可能性があります。  
  
 派生したクラスを記述することで、エディターを定義する<xref:System.Drawing.Design.UITypeEditor>します。 クラスをオーバーライドする必要があります。  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>、ユーザーと対話し、プロパティの値を更新します。  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>、、エディターはダイアログを開くか、ドロップダウン メニューを提供するかどうかを指定します。  
  
 プロパティ グリッドで表示されるプロパティの値をグラフィカルに表したを指定することもできます。 これを行うには、オーバーライド`GetPaintValueSupported`、および`PaintValue`します。  詳細については、「 <xref:System.Drawing.Design.UITypeEditor> 」を参照してください。  
  
> [!NOTE]
>  内の別のコード ファイルにコードを追加、 **Dsl**プロジェクト。  
  
 例えば:  
  
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
  
 このエディターを使用する設定、**カスタム属性**のドメインのプロパティ。  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 詳細については、「 <xref:System.Drawing.Design.UITypeEditor> 」を参照してください。  
  
## <a name="providing-a-drop-down-list-of-values"></a>値のドロップダウン リストを指定します。  
 選択するユーザーの値の一覧を指定することができます。  
  
> [!NOTE]
>  この手法では、実行時に変更できる値の一覧を示します。 変更しないリストを指定する場合は、代わりに検討してください、ドメイン プロパティの型と列挙型を使用します。  
  
 標準値のリストを定義するには、属性を追加する、ドメイン プロパティに CLR を持つ、次の形式。  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 <xref:System.ComponentModel.TypeConverter> から派生するクラスを定義します。 別のファイルにコードを追加、 **Dsl**プロジェクト。 例えば:  
  
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



