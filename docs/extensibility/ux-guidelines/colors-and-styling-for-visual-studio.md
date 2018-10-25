---
title: Visual Studio の色とスタイル |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f184fc08679100562a53c1f3f27d797a4cdff37
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918026"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio の色とスタイル

## <a name="use-color-in-visual-studio"></a>Visual Studio での色を使用します。

Visual Studio で、色は、主に装飾としてだけでなく、通信ツールとして使用されます。 必要がある場合の予約し、最小限の色を使用します。

- 意味や所属 (たとえば、プラットフォームや言語の修飾子を) 通信します。

- (たとえば、状態の変更を示す) の注意をひきつける

- 読みやすさを向上させるし、UI を移動するためのランドマークの提供

- 魅力を増やす

Visual Studio での UI 要素に色を割り当てるのいくつかのオプションが存在します。 場合によっては難しい図を使用することになっているオプションを判断またはそれを正しく使用する方法。 このトピックに役立ちます。

- Visual Studio での色を定義するために使用するシステムのさまざまなサービスを把握します。

- 指定された要素の適切なオプションを選択します。

- 正しく選択したオプションを使用します。

> [!NOTE]
> ありませんハードコーディング 16 進数、RGB、または、UI 要素に色のシステム カラーにします。 サービスを使用すると、柔軟性が hue をチューニングします。 さらに、サービス、することができなくのテーマの切り替え機能を活用するために[VSColor service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)します。

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio のインターフェイスの要素に色を割り当てる方法

UI 要素に最も適した方法を選択します。

| UI | メソッド | でしょうか。 |
| --- | --- | --- |
| 埋め込まれているか、スタンドアロンのダイアログ ボックス。 | **システム カラー** | コモン ダイアログのコントロールのようなオペレーティング システムの色と、UI 要素の外観を定義できるようにするシステムの名前。 |
| VS 環境全体と一致するカスタム UI があり、カテゴリおよび共有のトークンの意味と一致する UI 要素があります。 | **一般的な共有色** | 特定の UI 要素の既存の定義済みの色のトークン名 |
| 個々 の機能や機能のグループがあるし、同様の要素の色を共有することはありません。 | **カスタム色** | 色のトークン名を領域に固有の他の UI と共有することはできません。 |
| エンドユーザー (たとえば、テキスト エディターまたはデザイナーの特殊化されたウィンドウ)、UI またはコンテンツをカスタマイズすることを許可するには。 | **エンドユーザーのカスタマイズ**<br /><br />**(ツール&gt;オプション ダイアログ ボックス)** | 設定の"フォントおよび色 ページで定義されている、**ツール&gt;オプション**ダイアログまたは UI 機能の 1 つに固有の特殊化されたページ。 |

### <a name="visual-studio-themes"></a>Visual Studio のテーマ

Visual Studio 機能の 3 つの異なる配色テーマ: 明色、暗色、青。 また、ユーザー補助用に設計されたシステム全体の配色テーマは、ハイ コントラスト モードを検出します。

ユーザーは、Visual Studio の最初の使用時にテーマを選択するように求められますに移動して、後でテーマを切り替えができるように**ツール&gt;オプション&gt;環境&gt;全般**から新しいテーマを選択して"配色テーマ ドロップダウン メニュー。

ユーザーはコントロール パネルを使用してもいくつかのハイ コントラスト テーマの 1 つに、システム全体を切り替えます。 ユーザーは、ハイ コントラストのテーマを選択する場合 Visual Studio の色のテーマ セレクターに影響しません Visual Studio での色が、ハイ コントラスト モードを終了するときに、テーマの変更が保存されます。 ハイ コントラスト モードの詳細については、次を参照してください。[ハイ コントラストの選択色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)します。

### <a name="the-vscolor-service"></a>VSColor service

Visual Studio では、各 Visual Studio のテーマの色の値を含む名前付きエントリに、UI 要素の色の値をバインドすることができます VSColor service と呼ばれる環境の色サービスを提供します。 これにより、色は、現在ユーザーが選択したテーマやシステム ハイ コントラスト モードを反映するように自動的に変更します。 サービスの使用は、すべての色のテーマに関連する変更の実装が 1 つの場所で処理され、サービスからの一般的な共有色を使用している場合、UI が自動的に Visual Studio の将来のバージョンで新しいテーマを反映ことを意味します。

### <a name="implementation"></a>実装

Visual Studio のソース コードには、トークンの名前と各テーマのそれぞれの色の値の一覧が含まれているいくつかのパッケージ定義ファイルが含まれています。 色のサービスでは、これらのパッケージ定義ファイルで定義されている VSColors を読み取ります。 これらの色が XAML マークアップまたはコードで参照されているし、そこにいずれかで、`IVsUIShell5.GetThemedColor`メソッドまたは DynamicResource マッピングします。

### <a name="system-colors"></a>システム カラー

一般的なコントロールは、既定でシステム カラーを参照します。 埋め込みまたはスタンドアロン ダイアログを作成するときのように、システム カラーを使用するように UI の場合は、何もする必要はありません。

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor service での一般的な共有色

インターフェイスの要素には、全体的な Visual Studio 環境を反映する必要があります。 設計する UI コンポーネントに適した一般的な共有の色を再利用して、インターフェイスが Visual Studio の他のインターフェイスと一致して、テーマが追加または更新されること、色が自動的に更新することを確認します。

一般的な共有色を使用する前に、それらを正しく使用する方法を理解することを確認します。 一般的な共有色の不適切な使用すると、ユーザーの混乱やフラストレーション一貫性のない経験する可能性がありますが、

### <a name="user-customizable-colors"></a>ユーザーがカスタマイズできる色

参照:[エンドユーザーの色を公開します。](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

場合によっては、コード エディターまたはデザイン画面を作成する場合と同様に、UI をカスタマイズするには、エンドユーザーを許可するされます。 カスタマイズ可能な UI コンポーネントがある、**フォントおよび色**のセクション、**ツール&gt;オプション**ダイアログ ボックスで、ユーザーが、前景色、背景色、またはその両方を変更する選択できます。

![ツール&gt;オプション ダイアログ ボックス](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />ツール&gt;オプション ダイアログ ボックス

##  <a name="BKMK_TheVSColorService"></a> VSColor Service

Visual Studio では、VSColor service またはシェル カラー サービスとも呼ばれる環境の色サービスを提供します。 このサービスでは、各テーマの色を含む名前と値の色に、UI 要素の色の値をバインドできます。 すべての UI 要素の色は自動的に現在のユーザーが選択したテーマを反映するように変更し、UI は、環境の色のサービスにバインドされているようにと統合される新しいテーマ将来のバージョンの Visual Studio ように、VSColor サービスを使用する必要があります。

### <a name="how-the-service-works"></a>サービスのしくみ

環境の色のサービスでは、UI コンポーネントの .pkgdef で定義されている VSColors を読み取ります。 これら VSColors XAML マークアップまたはコードで参照されるといずれかで読み込まれて、`IVsUIShell5.GetThemedColor`または`DynamicResource`マッピングします。

![環境の色のサービス アーキテクチャ](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />環境の色のサービス アーキテクチャ

### <a name="accessing-the-service"></a>サービスへのアクセス

アクセスするトークンの色の種類に応じて、VSColor service を使用している必要があるコードの種類をいくつかのさまざまな方法はあります。

#### <a name="predefined-environment-colors"></a>定義済みの環境の色

##### <a name="from-native-code"></a>ネイティブ コードから

シェルへのアクセスを提供するサービスを提供する、`COLORREF`の色。 サービス/インターフェイスは次のとおりです。

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

ファイル VSShell80.idl、列挙体で`__VSSYSCOLOREX`がシェルの色の定数。 これを使用するとして渡すインデックス値から値のいずれかの`enum __VSSYSCOLOREX`で文書化されている MSDN または通常のインデックス番号を Windows システム API、 `GetSysColor`、受け入れます。 これが 2 番目のパラメーターに使用する必要がある色の RGB 値返されます。

必要な場合は、ペンまたは新しい色のブラシを保存するには、 `AdviseBroadcastMessages` (から Visual Studio シェル) をリッスンし、`WM_SYSCOLORCHANGE`と`WM_THEMECHANGED`メッセージ。


ネイティブ コードで、色のサービスにアクセスするには、次のように呼び出しを行います。

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF`によって返される値`GetVSSysColorEx()`だけ R、G を含むテーマの色の B コンポーネント。 テーマのエントリは、透明度を使用して、アルファ チャネル値を返す前に破棄されます。 そのため、関心のある環境の色を透過なチャネルが重要となる場所で使用する場合は、使用してください`IVsUIShell5.GetThemedColor`の代わりに`IVsUIShell2::GetVSSysColorEx`、このトピックの後半で説明します。

##### <a name="from-managed-code"></a>マネージ コードから

ネイティブ コード VSColor service へのアクセスはとても簡単です。 マネージ コードで作業している場合、サービスを使用する方法を決定するはたいへん。 念頭に、このプロセスを示す c# コード スニペットを示します。

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Visual Basic で作業している場合は、次のコマンドを使用します。

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF の UI から

アプリケーションのエクスポート値を Visual Studio の色にバインドできます`ResourceDictionary`します。 カラー テーブルからのリソースを使用して、XAML で環境フォント データへのバインドの例を次に示します。

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>ヘルパー クラスとマネージ コードのメソッド

マネージ コード、シェルの Managed Package Framework ライブラリの (`Microsoft.VisualStudio.Shell.12.0.dll`)、いくつかヘルパー クラスのテーマが適用された色の使用を促進することにはが含まれています。

ヘルパー メソッド、 `Microsoft.VisualStudio.Shell.VsColors` MPF でクラスが含まれて`GetThemedGDIColor()`と`GetThemedWPFColor()`します。 これらのヘルパー メソッドとしてテーマのエントリの色の値を返す`System.Drawing.Color`または`System.Windows.Media.Color`WinForms と WPF の UI で使用します。

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

クラスが指定の WPF 色リソース キーの VSCOLOR 識別子を取得することもできまたはその逆です。

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

メソッド`VsColors`クラスが呼び出されるたびに、色の値を返す VSColor service をクエリします。 色の値として取得する`System.Drawing.Color`のメソッドを使用する代わりにパフォーマンスを向上させるには、 `Microsoft.VisualStudio.PlatformUI.VSThemeColor` VSColor service から取得した色の値がキャッシュされているクラス。 クラスでは、内部的にシェルのブロードキャスト メッセージ イベントをサブスクライブし、テーマ変更イベントが発生した場合、キャッシュされた値を破棄します。 また、クラスを提供します。テーマの変更をサブスクライブする NET に適したイベントです。 使用して、 `ThemeChanged` 、新しいハンドラーを追加して、イベント、`GetThemedColor()`色を取得するメソッドの値を`ThemeResourceKeys`関心のあります。 このようなサンプル コードになります。

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

##  <a name="BKMK_ChoosingHighContrastColors"></a> ハイ コントラストの色を選択します。

### <a name="overview"></a>概要

Windows では、画面上のより明確に表示される要素を行うテキスト、背景、およびイメージの色のコントラストを向上させるいくつかのハイ コントラストのシステム レベル テーマを使用します。 ユーザー補助上の理由から、ユーザーは、ハイ コントラストのテーマに切り替えるときに、Visual Studio のインターフェイスの要素が正しく応答することが重要です。

ごく少数のシステム カラーは、ハイ コントラスト テーマで使用できます。 色の名前をシステムを選択する場合は、次のヒントに注意してください。

- **色のシステム カラーを同じ意味を持つ選択**色分けは要素として。 たとえば、ウィンドウ内のテキストのハイ コントラストの配色を選択する場合は、WindowText と ControlText いないを使用します。

- **前景と背景のペアを選択**一緒またはすべてのハイ コントラスト テーマで、色の選択が動作することを確信はできません。

- **UI のどの部分が最も重要な判断し、コンテンツ領域の目立つことを確認します。** カラー バリアントをさまざまなコンテンツ領域がないため、強力な境界線の色の使用は、コンテンツ領域を定義する一般的な色の色合いにわずかな違いを区別は通常、詳細の多くは失われます。

### <a name="system-color-set"></a>システム カラー セット

ある表[WPF チーム ブログ: SystemColors 参照](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/)のシステム色の名前、および対応する色合いがテーマごとに表示される完全なセットを示します。

Ui、色のセットを制限するこれを適用するときに *「標準」のテーマで存在していた微妙な詳細情報が失われることが必要ですが*します。 ツール ウィンドウ内の領域を区別するために使用されるグレー色が微妙には、UI の例を次に示します。 ハイ コントラスト モードで表示される同じウィンドウと組み合わせると、すべての背景は同じ色合いをこれらの領域の枠線は単独で境界線で示されますを確認できます。

![微妙な方法の詳細な例は、ハイ コントラストに失われます](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />微妙な方法の詳細な例は、ハイ コントラストに失われます

#### <a name="choosing-text-colors-in-an-editor"></a>エディターでテキストの色を選択します。

色分けされたテキストでは、エディターまたはデザイン サーフェイスを類似した項目のグループを識別しやすくすることができますのような意味を示すために使用されます。 ハイ コントラスト テーマでは、ただしがありません 4 つ以上のテキストの色を区別する機能。 WindowText、GrayText および HotTrackText は WindowBackground サーフェスで使用できる唯一の色です。 3 色以上を使用することはできませんので、ハイ コントラスト モードで表示する最も重要な相違点を慎重に選択します。

ハイ コントラスト テーマごとに表示される、エディターの画面で許可されているトークン名ごとの色相:

![ハイ コントラスト エディターの比較](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />ハイ コントラスト エディターの比較

青のテーマでのエディターの画面の例:

![青のテーマでのエディター](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />青のテーマでのエディター

![ハイコントラスト #1 のテーマでのエディター](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />ハイコントラスト #1 のテーマでのエディター

### <a name="usage-patterns"></a>使用パターン

多くの一般的な UI 要素では、定義されているハイ コントラストの色が既にあります。 UI 要素が、同様のコンポーネントと一致するように、独自のシステム色の名前を選択するときにこれらの使用状況パターンを参照することができます。

| システム カラー | 使用法 |
| --- | --- |
| ActiveCaption | アクティブな IDE と rafted ウィンドウ ボタンのグリフ ホバーとキーを押します<br />IDE および rafted ウィンドウのタイトル バーの背景<br />既定のステータス バーの背景 |
| ActiveCaptionText | -アクティブな IDE と rafted のウィンドウのタイトル バーの前景 (テキストとグリフ)<br />背景し、枠線のホバー時およびキーを押してアクティブなウィンドウのボタンの |
| コントロール | -既定値を制御し、ドロップダウン ボタンの背景を無効になっているコンボ ボックス、ドロップダウン リスト、および検索<br />-ターゲットのボタンの背景をドッキングします。<br />コマンド バーの背景<br />ツール ウィンドウの背景 |
| ControlDark | -IDE 背景<br />メニューとコマンド バーの区切り記号<br />コマンド バーの境界線<br />メニューの影<br />-ツール ウィンドウ タブの既定し、マウス ポインターの境界線との区切り記号<br />-ドキュメント オーバーフロー ボタンの背景では、<br />ドッキング ターゲット グリフの境界 |
| ControlDarkDark |-フォーカスされていない、選択されているドキュメント タブ ウィンドウ |
| ControlLight |自動的に隠す タブの境界線<br />-コンボ ボックスとドロップダウン リストの枠線<br />-ターゲットの背景や罫線をドッキングします。 |
| ControlLightLight | -選択された状態でフォーカスがある一時的な境界線 |
| ControlText | -コンボ ボックスとドロップダウン リストのグリフ<br />ツール ウィンドウが選択されていないタブのテキスト |
| GrayText |-コンボ ボックスとドロップダウン リストの境界線、グリフのドロップダウン リスト、テキスト、およびメニュー項目のテキストを無効になります。<br />-無効なメニューのテキスト<br />検索コントロール '検索オプション' ヘッダー テキスト<br />検索コントロール」セクションの区切り記号 |
| ハイライト | -すべてのホバーし、押された背景や罫線、コンボ ボックス ドロップダウン ボタンの背景とドキュメント ウェルのオーバーフロー ボタンの境界線を除く<br />-選択した項目の背景 |
| HighlightText | -すべてのホバー時および押された foregrounds (テキストとグリフ)<br />-限定的なツール ウィンドウとドキュメント タブ ウィンドウ コントロールの前景<br />-限定的なツール ウィンドウのタイトル バーの境界線<br />フォーカスがある、選択した一時的なタブの前景色<br />Hover でキーを押してドキュメント ウェルのオーバーフロー ボタンの境界線<br />-選択したアイコンの境界線|
| ホット トラック | -スクロール バーのつまみの背景と境界線でキーを押します<br />-スクロール バーの矢印のグリフでキーを押します |
| InactiveCaption | -非アクティブな IDE と rafted ウィンドウ ボタンのグリフ ホバー<br />IDE および rafted ウィンドウのタイトル バーの背景<br />-無効な検索コントロールの背景色 |
| InactiveCaptionText | -非アクティブな IDE と rafted windows タイトル バーの前景 (テキストとグリフ)<br />-非アクティブなウィンドウのボタンの背景と境界線ホバー<br />-フォーカスされていないツール ウィンドウのボタンの背景や罫線<br />-無効な検索コントロールの前景 |
| メニュー | ドロップダウン メニューの背景<br />チェックされ、無効にされたチェック マークの背景 |
| MenuText | ドロップダウン メニューの境界線<br />-のチェック マーク<br />メニュー グリフ<br />ドロップダウン メニューのテキスト<br />-選択したアイコンの境界線 |
| スクロール バー | -スクロール バー、スクロール バーの矢印の背景、すべての状態 |
| [Window] | 自動的に隠す タブの背景<br />メニュー バーし、コマンド シェルフの背景<br />-フォーカスされていないか、選択されていないドキュメント ウィンドウ タブの背景と開いていると、一時的なタブのドキュメントの境界線<br />-フォーカスされていないツール ウィンドウのタイトル バーの背景<br />ツール ウィンドウ タブの背景を両方選択し、選択解除 |
| WindowFrame | -IDE の枠線 |
| WindowText | 自動的に隠す タブの前景色<br />-選択したツール ウィンドウ タブの前景色<br />-フォーカスされていないドキュメント ウィンドウ タブ、フォーカスされていない、または未選択の一時的なタブの前景色<br />-既定の前景を表示し、マウス ポインターをツリー未選択のグリフの上<br />-ツール ウィンドウの選択されているタブ境界線<br />-スクロール バーのつまみの背景、境界線、およびグリフ |

##  <a name="BKMK_ExposingColorsForEndUsers"></a> エンドユーザーの色を公開します。

### <a name="overview"></a>概要

コード エディターまたはデザイン画面を作成するときと同様に、UI をカスタマイズしてエンドユーザーに許可するする場合があります。 これを行う最も一般的な方法を使用して、**ツール&gt;オプション**ダイアログ。 UI の特殊なコントロールを必要とする高度な専門、しない限り、カスタマイズを提示する最も簡単な方法は、**フォントおよび色**内でページ、**環境**ダイアログ ボックスのセクション。 カスタマイズして公開する各要素の前景色、背景色、またはその両方を変更するユーザーを選択できます。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>VSPackage、カスタマイズ可能な色の構築

VSPackage では、フォントと色カスタム カテゴリを制御でき、[フォントおよび色のプロパティ] ページの項目を表示することができます。 このメカニズムを使用して、Vspackage を実装する必要があります、 [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider)インターフェイスとその関連するインターフェイス。

原則として、既存のすべての表示項目およびそれらが含まれているカテゴリを変更するこのメカニズムを使用できます。 ただし、その使わないでテキスト エディターのカテゴリまたはその表示項目を変更します。 テキスト エディターのカテゴリの詳細については、次を参照してください。[フォントと色の概要](../font-and-color-overview.md)します。

カスタム カテゴリを実装または項目を表示、VSPackage では次の必要があります。

- **作成するか、レジストリ内のカテゴリを特定します。** IDE の実装、**フォントおよび色**プロパティ ページでは、この情報を使用して、特定のカテゴリをサポートしているサービスのクエリを正常にします。

- **作成または (省略可能) のレジストリ内のグループを識別します。** 2 つ以上のカテゴリの和集合を表すグループを定義すると便利な場合があります。 グループが定義されている場合、IDE によって自動的にサブカテゴリをマージし、配布グループ内のアイテムの表示。

- **IDE のサポートを実装します。**

- **フォントと色の変更を処理します。**

#### <a name="to-create-or-identify-categories"></a>作成またはカテゴリを識別するには

カテゴリのレジストリ エントリの特殊な型を構築`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]`場所`<Category>`カテゴリのローカライズされていない名前を指定します。

2 つの値を使用してレジストリを設定します。

| 名前 | 型 | データ | 説明 |
| --- | --- | --- | --- |
| カテゴリ | REG_SZ | GUID | カテゴリを識別するために作成された GUID |
| Package | REG_SZ | GUID | カテゴリをサポートする VSPackage のサービスの GUID |

 レジストリで指定されたサービスの実装を提供する必要があります[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)の対応するカテゴリ。

#### <a name="to-create-or-identify-groups"></a>グループを作成または識別するのには

カテゴリのレジストリ エントリの特殊な型を構築`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]`場所`<group>`はローカライズされていないグループの名前です。

2 つの値を使用してレジストリを設定します。

| 名前 | 型 | データ | 説明 |
|--- | --- | --- | --- |
| カテゴリ | REG_SZ | GUID | カテゴリを識別するために作成された GUID |
| Package | REG_SZ | GUID | カテゴリをサポートする VSPackage のサービスの GUID |

レジストリで指定されたサービスの実装を提供する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>の対応するグループ。

![照会先との実装](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />実装 `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>IDE のサポートを実装するには

実装[GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)、いずれかが返されます、 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)インターフェイスまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>インターフェイスの各カテゴリの IDE にまたはグループの GUID が指定されています。

すべてのカテゴリをサポートしています、VSPackage 実装の別のインスタンス、 [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)インターフェイス。

メソッドの実装を通じて[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)を使用して IDE を提供する必要があります。

- カテゴリの表示項目の一覧

- 表示項目のローカライズ可能な名前

- カテゴリの各メンバーの情報を表示します。

> [!NOTE]
> すべてのカテゴリには、少なくとも 1 つの表示項目を含める必要があります。

IDE を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>いくつかのカテゴリの共用体を定義するインターフェイス。

その実装を使用して IDE を提供します。

- 特定のグループを構成するカテゴリの一覧

- インスタンスへのアクセス[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults)グループ内の各カテゴリのサポート

- ローカライズ可能なグループ名

#### <a name="updating-the-ide"></a>IDE の更新

IDE では、フォントと色の設定に関する情報をキャッシュします。 そのため、IDE のフォントと色の構成の変更、後に、ベスト プラクティスをキャッシュが最新であることを確認します。

キャッシュの更新を行う、 [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager)インターフェイスし、実行のグローバルまたはだけで選択した項目を指定できます。

### <a name="handling-font-and-color-changes"></a>フォントと色の変更の処理

VSPackage を表示するテキストの色づけを正しくサポートするには、VSPackage のサポートの色づけサービスは、フォントおよび色のプロパティ ページで加えられたユーザーによる変更に応答する必要があります。

これを行うには、VSPackage では次の必要があります。

- **IDE で生成されたイベントを処理する**実装することによって、 [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents)インターフェイス。 IDE では、次のユーザーの変更、フォントおよび色 ページの適切なメソッドを呼び出します。 たとえば、呼び出す、 [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged)メソッドが新しいフォントが選択されている場合。

  **OR**

- **IDE の変更をポーリング**します。 これは、システムによって実装されるを通して実行[IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)インターフェイス。 主に、永続化のサポートには、 [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem)メソッドは、表示項目のフォントと色の情報を取得できます。 フォントおよび色の設定の詳細については、MSDN の記事を参照してください。[にアクセスする格納されているフォントと色の設定](../accessing-stored-font-and-color-settings.md)します。

> [!NOTE]
> ポーリングの結果が正しいことを確認するを使用して、 [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager)インターフェイスの取得メソッドを呼び出す前に、キャッシュのフラッシュと更新プログラムが必要なかどうかを決定する、 [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage)インターフェイス。

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>インターフェイスを実装することがなく、カスタムのフォントと色のカテゴリを登録します。

次のコード例では、カスタム フォントを登録し、インターフェイスを実装することがなくカテゴリの色の方法を示します。

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

このコード例。

- `"NameID"` パッケージにローカライズされたカテゴリ名のリソース ID を =
- `"ToolWindowPackage"` = パッケージ GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` 一例は、実際の値は、実装側によって提供される新しい GUID を指定できます。

### <a name="set-the-font-and-color-property-category-guid"></a>フォントおよび色プロパティ カテゴリ GUID を設定します。

次のコード例では、カテゴリの Guid の設定を示します。

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
