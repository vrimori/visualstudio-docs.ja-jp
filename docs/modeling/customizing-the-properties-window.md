---
title: "プロパティ ウィンドウのカスタマイズ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, [プロパティ] ウィンドウ"
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# プロパティ ウィンドウのカスタマイズ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ドメイン固有の言語の \[プロパティ\] ウィンドウの外観および動作を \(DSL\) カスタマイズできます。  DSL 定義では各ドメインのドメイン クラスのプロパティを定義します。  図またはモデル エクスプローラーでクラスのインスタンスを選択すると既定ではドメインのプロパティがプロパティ ウィンドウに表示されます。  これは図のフィールドを具体化ようにマップしていないドメインのプロパティの値を表示して編集できるようにします。  
  
## 名前説明およびカテゴリ  
 **名前および表示名** 。  ドメインのプロパティの定義ではプロパティの表示名はプロパティ ウィンドウのランタイムに表示されます。  これに対して場合はプロパティを更新するプログラム コードを記述するときに使用されます。  名前が正しい CLR の英数字の名前である必要があります表示名に空白を含めることができます。  
  
 DSL を定義するプロパティの名前を設定すると表示名とのコピーが自動的に設定されます。  「」 FuelGauge などPascal 形式でパッケージ化された名前を作成する場合は表示名が自動的に空白が含まれる場合 : 「」燃料計。  ただし別の値の表示名を明示的に設定できます。  
  
 **説明**。  ドメインのプロパティの説明は 2 か所に表示されます :  
  
-   プロパティ ウィンドウの下部ユーザーがプロパティを選択するとします。  プロパティが表す項目をユーザーに示すために使用できます。  
  
-   生成されるプログラム コード。  API に関するドキュメントを抽出するためにドキュメント機能を使用する API ではこのプロパティの説明として表示されます。  
  
 **カテゴリ**。  カテゴリはプロパティ ウィンドウの見出しです。  
  
## スタイルの機能の公開  
 グラフィック要素の動的機能の一部はドメインのプロパティとして表現されるかまたは  *公開*  できます。  この方法で公開された機能のユーザーによる更新しプログラム コードをより簡単に更新できます。  
  
 DSL 定義のクラスの図形を右クリックしをポイント **\*\*\* Add Exposed \*\*\*** して機能を選択します。  
  
 図形で **\*\*\* FillColor \*\*\*\*\*\* OutlineColor \*\*\*\*\*\* TextColor \*\*\*\*\*\* OutlineDashStyle \*\*\*\*\*\* OutlineThickness \*\*\*** と **\*\*\* FillGradientMode \*\*\*** のプロパティを公開できます。  コネクタに  **カラー** `,`**\*\*\* TextColor \*\*\*\*\*\* DashStyle \*\*\*** と **\*\*\* Thickness \*\*\*** のプロパティを公開できます。  図に **\*\*\* FillColor \*\*\*** と **\*\*\* TextColor \*\*\*** のプロパティを公開できます。  
  
## 転送 : 関連要素のプロパティを表示する  
 DSL のユーザーがモデル要素を選択するとその要素のプロパティがプロパティ ウィンドウに表示されます。  ただし指定関連要素のプロパティを表示できます。  これは連携して動作する要素のグループを定義した場合に便利です。  たとえばメインの要素とオプションのプラグインの要素を定義する必要があります。  主要な要素が図形にマップされている場合などがない場合は1 個の要素に存在していたすべてのプロパティを確認できると便利です。  
  
 この効果は  *転送*  された名前付きプロパティはさまざまな状況で自動的に行われます。  またドメインの型記述子の定義を通じて転送されるプロパティを使用します。  
  
### ケースを転送既定のプロパティ  
 ユーザーがエクスプローラーのシェイプまたはコネクタまたは要素を選択すると次のプロパティがプロパティ ウィンドウに表示 :  
  
-   モデル要素のドメイン クラスで定義された基本クラスで定義されたプロパティを含むドメインのプロパティ。  例外は`False` に設定されている **\*\*\* Is Browsable \*\*\*** を持つドメインのプロパティです。  
  
-   0..1 の多重度を持つ関係によってリンクされた要素の名前。  これはリレーションシップのコネクタのマッピングを定義していない場合でもオプションでリンクされた要素を表示する簡単な方法を提供します。  
  
-   要素を対象とする埋め込みリレーションシップのドメインのプロパティ。  通常埋め込みリレーションシップを明示的に表示するためユーザーがプロパティを確認することができます。  
  
-   選択したシェイプまたはコネクタに定義されているドメインのプロパティ。  
  
### プロパティの事前の追加  
 プロパティを転送するにはドメインの型記述子を定義します。  2 個のドメイン クラスのドメイン リレーションシップが含まれ2 番目のドメインのドメイン クラスのプロパティの値にファースト クラスのドメインのプロパティを設定するドメインの型記述子を使用できます。  たとえば書籍のドメイン クラスと作成者のドメイン クラス間の関係がある場合ユーザーが書籍を選択すると本の作成者の名前のプロパティをプロパティ ウィンドウに表示するドメインの型記述子を使用できます。  
  
> [!NOTE]
>  ユーザーがモデルを編集しているときの影響を転送プロパティ ウィンドウだけです。  これは受け取る側のクラスがプロパティは定義されません。  DSL 定義の他の部分やプログラム コードの転送ドメインのプロパティにアクセスする場合はCOPY 要素にアクセスする必要があります。  
  
 次の手順ではDSL を作成していることを前提とします。  最初のいくつかの手順は必要条件の概要を示します。  
  
##### 別の要素からプロパティを転送する  
  
1.  この例で Book と作成と呼ばれる2 文字以上のクラスを含む [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] のソリューションを作成します。  そこで作成者と間で Kind いずれかの関係。  
  
     ソースのロール \(books 側のロール\) の多重度は各ブックに 1 人の作成者が 0..1 または 1..1 必要があります。  
  
2.  **\*\*\* DSL Explorer \*\*\*** では書籍のドメイン クラスを右クリックしを ENT1ENT \[\] をクリックします。  
  
     **\*\*\* Paths of Custom Property Descriptors \*\*\*** という名前のノードが ENT1ENT \[入力\] ノードの下に表示されます。  
  
3.  \[入力\] ENT0ENT ノードを右クリックしを ENT1ENT \[\] をクリックします。  
  
     新しいプロパティのパスは ENT0ENT \[入力\] ノードの下に表示されます。  
  
4.  \[入力\] ENT0ENT ウィンドウの新しいプロパティのパスを設定して適切なモデル要素のパスに **\*\*\* Path to Property \*\*\*** を選択します。  
  
     このプロパティの右にある矢印をクリックしてツリー ビューのパスを変更できます。  ドメインのパスに関する詳細については[ドメイン パス構文](../modeling/domain-path-syntax.md) を参照してください。  それを編集した場合パスは **BookReferencesAuthor.Author\/\! 作成者**  になります。  
  
5.  作成者の **Name** ドメインのプロパティに  **プロパティ**  を設定します。  
  
6.  著者名に  **表示名**  を設定します。  
  
7.  すべてのテンプレートを変換しDSL をビルドして実行します。  
  
8.  モデル図ではブック著者を作成し参照リレーションシップを使用してファイルをリンクします。  書籍要素を選択し\[プロパティ\] ウィンドウでプロパティの他に著者名が表示されます。  リンク作成者の名前を変更したり別の作成者が書籍をリンクし書籍の著者名が変更されたことを確認します。  
  
## カスタム プロパティ エディター  
 プロパティ ウィンドウがドメインの各プロパティの型に環境を編集する適切な既定値を指定します。  たとえば列挙型についてはユーザーがドロップダウン リストで数値プロパティではユーザーが数値を入力できます。  これは組み込み型にのみ当てはまります。  外部型を指定した場合ユーザーは属性を参照してそれを編集できます。  
  
 ただし次のエディターを指定できます :  
  
1.  基本データ型に使用される別のエディター。  たとえば文字列プロパティのファイル パスのエディターを指定できます。  
  
2.  ドメインのプロパティの外部の型およびのエディター。  
  
3.  ファイル パスのエディターもなどの .NET エディター独自のカスタム プロパティ エディターを作成できます。  
  
     既定のエディターを持つ文字列などの外部型と型の間の変換。  
  
 DSL では *外部の型は*  単純型 \(Boolean 値を Int32 など\) や文字列の 1 種類です。  
  
#### 外部型を持つドメインのプロパティを定義するには  
  
1.  **ソリューション エクスプローラー**  では**Dsl** プロジェクトの外部の型を含むアセンブリ \(DLL\) への参照を追加します。  
  
     アセンブリは .NET アセンブリまたは提供するアセンブリを指定できます。  
  
2.  まだ行っていない場合は\[入力\] ENT0ENT リストの型を追加します。  
  
    1.  **\*\*\* DSL Explorer \*\*\*** の開いている DslDefinition.dsl はルート ノードを右クリックしを ENT1ENT \[\] をクリックします。  
  
         新しいエントリが ENT1ENT \[入力\] ノードの下に表示されます。  
  
        > [!WARNING]
        >  メニュー項目は DSL のルート ノードに ENT2ENT \[入力\] ノードではなくです。  
  
    2.  ウィンドウのプロパティに新しい型の名前空間と名前空間を設定します。  
  
3.  通常の方法でドメインのドメイン クラスにプロパティを追加します。  
  
     \[プロパティ\] ウィンドウでENT1ENT \[入力\] フィールドのドロップダウン リストから外部型を選択します。  
  
 この段階ではユーザーはプロパティの値を表示できますが編集はできません。  表示される値は `ToString()` の関数から派生します。  コマンドや規則のプロパティの値を設定するなどプログラム コードを記述できます。  
  
### プロパティ エディターの設定  
 次の形式のドメインのプロパティに CLR 属性を追加します :  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 \[プロパティ\] ウィンドウで **\*\*\* Custom Attribute \*\*\*** のエントリを使用してプロパティの属性を設定します。  
  
 `AnEditor` の種類は 2 番目のパラメーターで指定された型から派生している必要があります。  2 番目のパラメーターは <xref:System.Drawing.Design.UITypeEditor> または <xref:System.ComponentModel.ComponentEditor> 必要があります。  詳細については、「<xref:System.ComponentModel.EditorAttribute>」を参照してください。  
  
 <xref:System.Windows.Forms.Design.FileNameEditor> または <xref:System.Drawing.Design.ImageEditor> などの [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] で独自のエディターまたは指定されたエディターを指定できます。  たとえばユーザーがファイル名を入力できるプロパティを使用するには次の手順を使用します。  
  
##### ファイル名のドメインのプロパティを定義するには  
  
1.  DSL 定義のドメイン クラスにドメインのプロパティを追加します。  
  
2.  新しいプロパティを選択します。  \[プロパティ\] ウィンドウの \[ENT0ENT\] フィールドでは次の属性を入力します。  この属性を入力するには省略記号 **\[...\]** をクリックし属性名とパラメーターを個別に指定します :  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  **文字列**  の既定の設定でドメインのプロパティの型をそのまま使用します。  
  
4.  ドメインのプロパティを編集するためのユーザーがファイル名のエディターを開くことができることをエディターをテストするには確認します。  
  
    1.  F5 キーまたは Ctrl \+ F5 キーを押します。  デバッグのソリューションではテスト ファイルを開きます。  ドメイン クラスの要素を作成しをクリックします。  
  
    2.  \[プロパティ\] ウィンドウでドメインのプロパティを選択します。  フィールド値は省略記号 **\[...\]** を示します。  
  
    3.  省略記号をクリックします。  ファイル ダイアログ ボックスが表示されます。  ファイルを選択しダイアログ ボックスを閉じます。  これでファイル パスはドメインのプロパティの値です。  
  
### 独自のプロパティ エディターの定義  
 独自のエディターを定義できます。  ユーザーのいずれかに編集するを定義して特殊な方法で基本型を型を編集する行います。  たとえばユーザーが式を表す文字列を送信することを許可できます。  
  
 <xref:System.Drawing.Design.UITypeEditor> から派生したクラスを記述することでエディターを定義します。  クラスでをオーバーライドする必要があります :  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>ユーザーとやり取りしプロパティ値を更新します。  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>ダイアログ エディターでを開くかドロップダウン メニューを使用するかどうかを指定します。  
  
 またプロパティ グリッドに表示されるプロパティの値をグラフィカル表示を使用できます。  これを行うには`GetPaintValueSupported` と `PaintValue` をオーバーライドします。  詳細については、「<xref:System.Drawing.Design.UITypeEditor>」を参照してください。  
  
> [!NOTE]
>  **Dsl** プロジェクトの別のコード ファイルにコードを追加します。  
  
 次に例を示します。  
  
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
  
 このエディターを使用するにはドメインの **\*\*\* Custom Attribute \*\*\*** のプロパティをに設定します :  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 詳細については、「<xref:System.Drawing.Design.UITypeEditor>」を参照してください。  
  
## 値のドロップダウン リストの使用  
 ユーザーが選択できるように値のリストを提供できます。  
  
> [!NOTE]
>  この方法は実行時に変更できる値の一覧を示します。  変更されないリストを指定するには代わりにドメインのプロパティの型として列挙型を使用することを検討してください。  
  
 標準値のリストを定義するにはドメインのプロパティに次の形式を持つ CLR 属性を追加します :  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 <xref:System.ComponentModel.TypeConverter> から派生するクラスを定義します。  **Dsl** プロジェクトの別のファイルのコードを追加します。  次に例を示します。  
  
```c#  
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
  
## 参照  
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)