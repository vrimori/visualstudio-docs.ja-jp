---
title: "VSIX の色エディター | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# VSIX の色エディター
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 拡張機能の色エディター ツールでは、作成でき、Visual Studio のカスタム カラーを編集することができます。 色は、コードで使用できるようにするツールもテーマ リソース キーを生成できます。 このツールは、テーマをサポートする Visual Studio 拡張機能に使用する色の作成に役立ちます。 このツールは、.pkgdef と .xml ファイルを開くことができます。 Visual Studio のテーマ \(.vstheme ファイル\) をファイル拡張子を .xml に変更することで Visual Studio 拡張機能の色エディターを使用できます。 さらに、.vstheme ファイルは、現在の .xml ファイルにインポートできます。  
  
 ![VSIX カラー エディターのヒーロー](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX Color Editor Hero")  
  
 **パッケージ定義ファイル**  
  
 パッケージ定義 \(.pkgdef\) ファイルは、テーマを定義するファイルです。 カラー自体は、.pkgdef ファイルにコンパイルされるテーマの色 .xml ファイルに格納されます。 .Pkgdef ファイルの Visual Studio の検索可能な場所に配置、実行時に、処理およびを結合してテーマを定義していること。  
  
 **色のトークン**  
  
 色のトークンは、4 つの要素で構成されています。  
  
-   **カテゴリ名:** 色のセットの論理的なグループです。 既に目的の UI 要素または UI 要素のグループに固有の色がある場合は、既存のカテゴリ名を使用します。  
  
-   **トークン名:** 色トークンとトークンのセットのわかりやすい名前。 セットには、バック グラウンド トークン名の前景色 \(テキスト\) とそのすべての状態が含まれます。 し、これらはという名前で、ペアとが適用される状態を識別しやすいようにします。  
  
-   **色の値 \(または色相\):** カラー テーマごとに必要です。 常に作成背景色とテキスト色の値のペアにします。 \(フォア グラウンドで\) テキストの色が常が描画される背景色を読み取れるように背景と前景の色が組み合わされています。 これらの色はリンクされ、UI で同時に使用されます。 背景は、テキストで使用するためのものではありません、前景の色を定義してください。  
  
-   **システム カラー名:** ハイ コントラストの表示で使用するためです。  
  
## ツールを使用する方法  
 可能な限り、新しいものを作るのではなく既存の Visual Studio の色を再利用する、適切な場所です。 ただし、適切な色が定義されていない場合は、カスタム カラーを互換性のある拡張機能テーマを保持する作成する必要があります。  
  
 **新しい色のトークンの作成**  
  
 Visual Studio 拡張機能の色エディターを使用して作成した色を作成するには、次の手順を実行します。  
  
1.  新しい色トークンのカテゴリとトークンの名前を決定します。  
  
2.  UI 要素は各テーマと、システム カラーを使用ハイ コントラストの色合いを選択します。  
  
3.  カラー エディターを使用すると、新しい色のトークンを作成できます。  
  
4.  Visual Studio 拡張機能では、色を使用します。  
  
5.  Visual Studio で、変更をテストします。  
  
 **手順 1: は、カテゴリと、新しい色トークンのトークン名を決定します。**  
  
 VSColor は優先名前付ける方式 **\[Category\] \[UI type\] \[状態\]**します。 冗長であるため、VSColor 名に"color"という単語を使わないでください。  
  
 カテゴリ名は、論理的なグループを示し、可能な限り狭くとして定義する必要があります。 たとえば、カテゴリ名を指定することが 1 つのツール ウィンドウの名前が全体のビジネス単位またはプロジェクト チームの名前ではありません。 エントリのカテゴリにグループ化では、同じ名前の色の間で混乱を防止します。  
  
 トークンの名前が必要があります、要素の型と、状況、または「状態を」色の適用を明確に表示します。 など、アクティブなデータ ヒントで **\[UI type\]** という可能性があります"**データヒント**"および **\[状態\]** という可能性があります"**Active**,、"の色の名前に"**DataTipActive**." データ ヒント テキストがあるため、前景色と背景色の両方を定義する必要があります。 背景と前景の組み合わせを使用して、カラー エディターが自動的に作成、色"**DataTipActive**"の背景と"**DataTipActiveText**"前景色にします。  
  
 UI の部分に 1 つの状態がある場合、 **\[状態\]** 名の一部を省略できます。 たとえば、検索ボックスは枠を持つ、枠線の色に影響を及ぼす状態変更がない場合は、枠線の色のトークンの名前だけで呼び出せる"**SearchBoxBorder**."  
  
 いくつかの一般的な州名は次のとおりです。  
  
-   アクティブ  
  
-   非アクティブ  
  
-   マウスを移動  
  
-   MouseDown  
  
-   選択済み  
  
-   Focused  
  
 リスト項目コントロールの部分に、いくつかのトークン名の例:  
  
-   ListItem  
  
-   ListItemBorder  
  
-   ListItemMouseOver  
  
-   ListItemMouseOverBorder  
  
-   ListItemSelected  
  
-   ListItemSelectedBorder  
  
-   ListItemDisabled  
  
-   ListItemDisabledBorder  
  
 **手順 2: は、UI 要素は各テーマと、システム カラーを使用ハイ コントラストの色合いを選択します。**  
  
 UI を作成した色を選択する場合のような既存の UI 要素を選択し、その色のベースとして使用します。 ボックスの UI 要素の色が確認とテスト、発生したため、適切な参照は、すべてのテーマで正しく機能するとします。  
  
 **手順 3: では、カラー エディターを使用して、新しい色のトークンを作成します。**  
  
 カラー エディターを起動し、開くか、新しいユーザー定義のテーマの色の .xml ファイルを作成します。 選択 **編集 \> 新しい色** \] メニューからです。 これは、そのカテゴリ内の色のエントリの 1 つまたは複数の名前とカテゴリを指定するダイアログが開きます。  
  
 ![VSIX カラー エディターの新しい色](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX Color Editor New Color")  
  
 既存のカテゴリを選択するか選択 **新しいカテゴリ** 新しいカテゴリを作成します。 別のダイアログ ボックスが開き、新しいカテゴリの名前を作成します。  
  
 ![VSIX カラー エディターの新しいカテゴリ](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX Color Editor New Category")  
  
 新しいカテゴリで可能になりますが、 **新しい色** カテゴリ ドロップ ダウン メニュー。 カテゴリを選択すると、新しい各色トークンの 1 行につき 1 つの名前を入力し、完了したら \[作成\] を選択します。  
  
 ![VSIX カラー エディターの新しい色 &#40;塗りつぶし&#41;](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX Color Editor New Color Filled")  
  
 色の値は、"None"色が定義されていないことを示すで背景と前景のペアで示されます。 注: 色がテキストの色や背景の色ペアを持たない場合、背景のみが定義する必要があります。  
  
 ![VSIX カラー エディターのカラー値](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX Color Editor Color Values")  
  
 色のトークンを編集するには、そのトークンのテーマ \(列\) の色のエントリを選択します。 ARGB 形式の 8 桁の 16 進カラー値を入力する、セルに、システムの色の名前を入力するかドロップダウン メニューを使用して、一連の色スライダーまたはシステムの色の一覧を使用して目的の色を選択するには、色の値を追加します。  
  
 ![VSIX カラー エディターの色の編集](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX Color Editor Edit Color")  
  
 ![VSIX カラー エディターの背景](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX Color Editor Background")  
  
 テキストを表示する必要のないコンポーネントの 1 つだけの色の値を入力してください: 背景色。 それ以外の場合、スラッシュで区切られた、背景色とテキストの両方の色の値を入力します。  
  
 ハイ コントラストの値を入力するときに、有効な Windows システムの色の名前を入力します。 ハードコードされた ARGB 値を入力しません。 有効なシステムの色の名前の一覧を表示するには、色の値のドロップダウン メニューから「:: システムのバック グラウンド」または「フォア グラウンド:: システム」を選択します。 テキスト コンポーネントを含む要素を作成するときに正しい背景のテキストのシステム カラー ペアを使用またはテキストが読みやすくない可能性があります。  
  
 作成、設定、および色のトークンの編集が完了したら、必要な .xml または .pkgdef 形式に保存します。 どちらの背景を持つトークンの色もフォア グラウンドのセットを .xml 形式で空の色として保存されますが、.pkgdef 形式で破棄されます。 .Pkgdef ファイルに空の色を保存しようとする場合は、ダイアログ ボックスは色損失の可能性ので表示されます。  
  
 **手順 4: は、Visual Studio 拡張機能で、色を使用します。**  
  
 新しい色を定義した後、トークンは、「ビルド アクション」を「コンテンツ」に設定をプロジェクト ファイルで、.pkgdef を含めるし、"VSIX に含める"が"True"に設定  
  
 ![VSIX カラー エディターの pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX Color Editor pkgdef")  
  
 Visual Studio 拡張機能の色エディターで、ファイルを選択して \> WPF ベースの UI で \[ユーザー設定にアクセスするために使用されるコードを表示するコードのリソースの色します。  
  
 ![VSIX カラー エディターのリソース コード ビューアー](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX Color Editor Resource Code Viewer")  
  
 このコードをプロジェクト内の静的クラスに含めます。 参照を **Microsoft.VisualStudio.Shell。 \< VSVersion \>.0.dll** を使用するプロジェクトに追加する必要がある、 **ThemeResourceKey** 型です。  
  
```c#  
namespace MyCustomColors { public static class MyCategory { #region Autogenerated resource keys // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category. public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe"); private static ThemeResourceKey _MyColor1ColorKey; private static ThemeResourceKey _MyColor1BrushKey; private static ThemeResourceKey _MyColor1TextColorKey; private static ThemeResourceKey _MyColor1TextBrushKey; public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } } public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } } public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } } public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } } #endregion } }  
```  
  
 これにより、XAML コードの色へのアクセスし、UI のテーマの変更に応答することができます。  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:ns="clr-namespace:MyCustomColors"> <Grid> <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}" Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}" >Sample Text</TextBlock> </Grid> </UserControl>  
```  
  
 **手順 5: は、Visual Studio で、変更をテストします。**  
  
 カラー エディターは、拡張機能パッケージを再構築しないで色にライブの変更を表示する Visual Studio の実行中のインスタンスに色のトークンを一時的に適用できます。 これを行うには、テーマの各列のヘッダーにある"Visual Studio の windows を実行するこのテーマを適用する\] ボタンをクリックします。 この一時的なテーマと解消されます VSIX カラー エディターを終了します。  
  
 ![VSIX カラー エディターによる適用](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX Color Editor Apply")  
  
 変更を恒久的な再構築し、.pkgdef ファイルを新しい色を追加し、その色が使用するコードを記述した後、Visual Studio 拡張機能を再展開します。 Visual Studio 拡張機能を再構築すると、テーマの残りの部分に新しい色のレジストリ値がマージされます。 Visual Studio を再起動し、UI を表示し、予期したとおりに新しい色が表示されることを確認します。  
  
## ノート  
 このツールは、既存の Visual Studio のテーマやカスタムの Visual Studio のテーマの色を編集するためのカスタムの色を作成するために使用するものです。 完全なカスタム Visual Studio のテーマを作成するには、ダウンロード、 [Visual Studio の配色テーマ エディター拡張機能](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b) Visual Studio Extensions Gallery からです。  
  
## 出力例  
 **色の XML 出力**  
  
 ツールによって生成された .xml ファイルに次のようになります。  
  
```xml  
<Themes> <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}"> <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}"> <Color Name="ColorName1"> <Background Type="CT_RAW" Source="FFFFFFFF" /> </Color> <Color Name="ColorName2"> <Background Type="CT_RAW" Source="FFFFFFFF" /> <Foreground Type="CT_RAW" Source="FF000000" /> </Color> <Color Name="ColorName3"> <Background Type="CT_RAW" Source="FFFF0000" /> </Color> <Color Name="ColorName4"> <Background Type="CT_RAW" Source="FF000088" /> <Foreground Type="CT_RAW" Source="FFFFFFFF" /> </Color> </Category> </Theme> <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme> <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme> <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme> </Themes>  
  
```  
  
 **PKGDEF カラー出力**  
  
 ツールによって生成された .pkgdef ファイルは、次のようになります。  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName] "Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff [$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName] "Data"=hex:... [$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName] "Data"=hex:... [$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName] "Data"=hex:...  
  
```  
  
 **C\# リソース キーのラッパー**  
  
 ツールによって生成される色リソース キーは、次のようになります。  
  
```c#  
namespace MyNamespace { public static class MyColors { #region Autogenerated resource keys // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category. public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } } public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } } public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } } public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } } public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } } public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } } public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } } public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } } public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } } public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } } #endregion } }  
```  
  
 **WPF リソース ディクショナリのラッパー**  
  
 色 **ResourceDictionary** ツールによって生成されたキーに次のようになります。  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:colors="clr-namespace:MyNamespace"> <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" /> <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" /> <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" /> <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" /> <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" /> <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" /> <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" /> <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" /> <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" /> <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" /> <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" /> <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" /> </ResourceDictionary>  
```