---
title: 色とスタイルが Visual Studio の |Microsoft ドキュメント
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
ms.openlocfilehash: 5cee3ec1308ee103d279a0d77ded4092e4ccf9b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="colors-and-styling-for-visual-studio"></a>色とスタイルが Visual Studio の
## <a name="using-color-in-visual-studio"></a>Visual Studio での色を使用します。
Visual Studio で、色は、装飾としてだけでなく、コミュニケーション ツールとして、主に使用されます。 場合の予約し、最小限の色を使用します。

-   (たとえば、プラットフォームや言語の修飾子) への関連付けまたは意味を通信します。

-   読者の注意 (たとえば、状態の変更を示す)

-   読みやすさを向上させるし、UI を移動するための目印の提供

-   適切かどうかを増やす

いくつかのオプションは、Visual Studio での UI 要素に色の割り当てに存在します。 難しい場合があります図を out どのオプションを使用することになっているか、適切に使用する方法です。 このトピックに役立ちます。

1.  システムについて把握、さまざまなサービスを Visual Studio での色を定義するために使用します。

2.  指定された要素の適切なオプションを選択します。

3.  選択したオプションが正しく使用します。

> **注:**ハードコーディング 16 進数、RGB、または、UI 要素に色のシステム カラーことはありません。 サービスを使用すると、柔軟性が色合いをチューニングします。 さらに、このサービスがないいないことができますのテーマ切り替え機能を活用するために[VSColor サービス](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)です。

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio のインターフェイスの要素に色を割り当てる方法
UI 要素に最も適した方法を選択します。

| UI | メソッド | 新機能は、これらですか。 |
| --- | --- | --- |
| 埋め込まれているか、スタンドアロンのダイアログ ボックス。 | **システム カラー** | コモン ダイアログ コントロールのようなオペレーティング システムの色および UI 要素の外観を定義できるようにするシステムの名前。 |
| VS 環境全体で一貫性を保つようにするカスタムの UI があり、カテゴリおよび共有のトークンの意味と一致する UI 要素があります。 | **一般的な共有色** | 既存の特定の UI 要素の定義済みの色のトークン名 |
| 個々 の機能や機能のグループがあるし、類似の要素の色を共有することはありません。 | **カスタムの色** | 色のトークン名領域に固有なを他の UI と共有することはできません。 |
| (たとえば、テキスト エディターまたはデザイナー ウィンドウの特殊化された) UI またはコンテンツをカスタマイズするエンド ユーザーを許可するには。 | **エンドユーザーのカスタマイズ**<br /><br />**(ツール&gt;オプション ダイアログ ボックス)** | 「フォントおよび色」ページで定義されている設定、**ツール&gt;オプション**ダイアログまたは 1 つの UI 機能に固有の特殊なページです。 |

### <a name="visual-studio-themes"></a>Visual Studio のテーマ
Visual Studio 機能の 3 つの別の配色テーマ: ライト、濃色、および青。 また、ユーザー補助のために設計されたシステムの配色テーマは、ハイ コントラスト モードを検出します。

ユーザーが Visual Studio の最初の使用時にテーマを選択するように求められに移動して、後でテーマを切り替えることが**ツール&gt;オプション&gt;環境&gt;全般**から新しいテーマを選択して[色のテーマ] ドロップ ダウン メニュー。

ユーザーは、ハイ コントラスト テーマがいくつかのいずれかに、システム全体を切り替えるには、コントロール パネルも使用できます。 ユーザーは、ハイ コントラストのテーマを選択する場合、Visual Studio のカラー テーマ セレクター不要になったに影響 Visual Studio で、色ハイ コントラスト モードを終了するときのテーマの変更が保存されますがします。 ハイ コントラスト モードの詳細については、次を参照してください。[ハイ コントラストの選択色](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)です。

### <a name="the-vscolor-service"></a>VSColor サービス
Visual Studio では、環境の色を使用すると、各 Visual Studio のテーマの色の値を含む名前付きのエントリに、UI 要素の色の値をバインドする、VSColor サービスと呼ばれるサービスを提供します。 これにより、色は、現在ユーザーが選択したテーマまたはシステム ハイ コントラスト モードを反映するように自動的に変更します。 サービスの使用は、すべての色のテーマに関連する変更の実装が 1 つの場所で処理され、UI は将来のバージョンの Visual Studio で新しいテーマを反映して自動的にサービスからの一般的な共有色を使用している場合のことを意味します。

### <a name="implementation"></a>実装
Visual Studio ソース コードには、トークンの名前と各テーマのそれぞれの色の値の一覧を含むいくつかのパッケージ定義ファイルが含まれています。 色のサービスは、これらのパッケージ定義ファイルで定義されている VSColors を読み取ります。 これらの色の XAML マークアップやコードを参照し、いずれかで読み込まれます、`IVsUIShell5.GetThemedColor`メソッドまたは DynamicResource マッピングします。

### <a name="system-colors"></a>システム カラー
コモン コントロールは、既定では、システム カラーを参照します。 場合は、埋め込まれた、またはスタンドアロンのダイアログを作成する場合と同様に、システムの色を使用する UI は何もする必要はありません。

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor サービスでの一般的な共有色
インターフェイスの要素には、全体的な Visual Studio 環境を反映する必要があります。 UI コンポーネントを設計するのに適した一般的な共有色を再利用して、インターフェイスが他の Visual Studio のインターフェイスと一致して、テーマを追加または更新されたときに、色が自動的に更新を確認します。

一般的な共有色を使用する前にそれらを正しく使用する方法を理解していることを確認します。 一般的な共有色の不適切な使用は、ユーザーの操作に一貫性のないと手間が、または混乱を招く可能性があります。

### <a name="user-customizable-colors"></a>ユーザーがカスタマイズできる色
参照:[エンドユーザーの色を公開します。](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

場合によっては、コード エディターまたはデザイン画面を作成する場合と同様に、UI をカスタマイズするエンド ユーザーを許可するされます。 カスタマイズ可能な UI コンポーネントに含まれて、**フォントおよび色**のセクションで、**ツール&gt;オプション**ダイアログ ボックスで、ユーザーが、前景色と背景色のどちらか一方または両方を選択できます。

![ツール&gt;オプション ダイアログ ボックス](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301 a_ToolsOptionsDialog")<br />ツール&gt;オプション ダイアログ ボックス

##  <a name="BKMK_TheVSColorService"></a> VSColor サービス
Visual Studio では、環境の色とも呼ばれます VSColor サービス シェルの色のサービスのサービスを提供します。 このサービスでは、各テーマの色を含む名前と値の色に、UI 要素の色の値をバインドすることができます。 色は自動的にユーザーが選択した、現在のテーマを反映するように変更し、UI は、環境の色のサービスにバインドされているように統合されます新しいテーマを使用して将来のバージョンの Visual Studio ようには、すべての UI 要素に VSColor service を使用する必要があります。

### <a name="how-the-service-works"></a>サービスの動作方法
環境の色のサービスでは、UI コンポーネントの .pkgdef で定義されている VSColors を読み取ります。 これらの VSColors は XAML マークアップやコード内で参照し、およびがいずれかで読み込まれている、`IVsUIShell5.GetThemedColor`または`DynamicResource`マッピングします。

![環境の色のサービス アーキテクチャ](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302 a_EnvironmentColorServiceArchitecture")<br />環境の色のサービス アーキテクチャ

### <a name="accessing-the-service"></a>サービスへのアクセス
アクセスするトークンの色の種類に応じて、VSColor サービスを使用しているコードの種類を使用していくつかの方法があります。

#### <a name="predefined-environment-colors"></a>定義済みの環境の色

##### <a name="from-native-code"></a>ネイティブ コードから
シェルが備えるへのアクセスを提供するサービス、`COLORREF`の色。 サービスまたはインターフェイスは。

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

ファイル VSShell80.idl、列挙体に`__VSSYSCOLOREX`シェル色定数がします。 これを使用するとして渡したインデックス値から値のいずれか、`enum __VSSYSCOLOREX`で文書化された MSDN または Windows システムの API、番号と標準インデックス`GetSysColor`、受け入れます。 これが 2 番目のパラメーターで使用される色の RGB 値戻す取得します。

ペンまたは新しい色のブラシを格納する必要があります`AdviseBroadcastMessages`(Visual Studio シェル) からのリッスンと`WM_SYSCOLORCHANGE`と`WM_THEMECHANGED`メッセージ。


ネイティブ コードで、色のサービスにアクセスするには、このような呼び出しを行うします。

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> **注:** 、`COLORREF`によって返される値`GetVSSysColorEx()`だけ R、G を含むテーマの色の B のコンポーネントです。 テーマのエントリは、透過性を使用して、アルファ チャネル値を返す前に破棄されます。 したがって、目的の環境の色を透過なチャネルが重要となる場所で使用する必要がある、する必要がありますを使用`IVsUIShell5.GetThemedColor`の代わりに`IVsUIShell2::GetVSSysColorEx`、このトピックの後半で説明します。

##### <a name="from-managed-code"></a>マネージ コードから
ネイティブ コードを VSColor サービスへのアクセスが簡単にします。 マネージ コードで作業している場合、サービスを使用する方法を決定する難しくなってきます。 念頭に、このプロセスを示す c# のコード スニペットを次に示します。

```
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

Visual Basic で作業している場合に使用します。

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF の UI から
値に、アプリケーションのエクスポートを Visual Studio の色にバインドできる`ResourceDictionary`です。 カラー テーブルからリソースを使用して、XAML で環境フォント データへのバインドの例を次に示します。

```
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
マネージ コードの場合は、シェルの Managed Package Framework ライブラリ (`Microsoft.VisualStudio.Shell.12.0.dll`) テーマの色の使用を促進するヘルパー クラスのいくつか含まれます。

内のヘルパー メソッド、 `Microsoft.VisualStudio.Shell.VsColors` MPF 内のクラスを含める`GetThemedGDIColor()`と`GetThemedWPFColor()`です。 これらのヘルパー メソッド、色の戻り値としてテーマ エントリ`System.Drawing.Color`または`System.Windows.Media.Color`、WinForms または WPF UI で使用します。

```
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

クラスは、特定の WPF 色リソース キーの VSCOLOR 識別子を取得するも使用できますまたはその逆です。

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

メソッド`VsColors`クラスが呼び出されるたびに、色の値を返す VSColor サービスを照会します。 として色値を取得する`System.Drawing.Color`、パフォーマンスに優れた代替手段は、代わりのメソッドを使用する、 `Microsoft.VisualStudio.PlatformUI.VSThemeColor` VSColor サービスから取得した色の値がキャッシュされているクラスです。 クラスでは、内部的にシェルのブロードキャスト メッセージをイベントにサブスクライブし、テーマ変更イベントが発生したときに、キャッシュされた値を破棄します。 また、クラスを提供します。テーマの変更をサブスクライブする NET が容易なイベントです。 使用して、`ThemeChanged`新しいハンドラーを追加して、イベント、`GetThemedColor()`色を取得するメソッドの値を`ThemeResourceKeys`関心のあります。 サンプル コードは、次のようになります。

```
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
Windows では、要素が画面により明確に表示するテキスト、背景、および画像の色コントラストを向上させるいくつかのハイ コントラスト システム レベルのテーマを使用します。 ユーザー補助上の理由から、ユーザーは、ハイ コントラストのテーマを切り替えると、Visual Studio のインターフェイスの要素が正しく応答している重要なです。

ハイ コントラストのテーマのシステム カラーのほんの一部のみを使用できます。 システム色の名前を選択するときに、次のことに注意してください。

1.  **同じ意味のあるシステムの色を選択**を色分けする要素とします。 たとえば、ウィンドウ内のテキストのハイ コントラストの配色を選択する場合は、WindowText といない ControlText を使用します。

2.  **前景色と背景のペアを選択**一緒にすべてのハイ コントラスト テーマで、色の選択が動作することを確信するはありません。

3.  **UI のどの部分は、最も重要な決定して、コンテンツ領域の目立つことを確認してください。**さまざまなコンテンツ領域の色のバリエーションが存在しないために、強力な境界線の色を使用するはコンテンツの領域を定義する一般的なので、多くの色の色合いにわずかな違いを区別は通常、詳細は失われます。

### <a name="system-color-set"></a>システム カラー セット
ある表[WPF チーム ブログ: SystemColors 参照](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx)システム色の名前、および各テーマに表示される対応する色合いの完全なセットを示します。

UI に色のセットを制限するこれを適用するときに*"normal"のテーマで存在していた微妙な詳細情報が失われることを想定して*です。 ツール ウィンドウ内の領域を区別するために使用される微妙なグレー色の UI の例を次に示します。 ハイ コントラスト モードで表示される同じウィンドウと組み合わせると、すべての背景が同じ色合いと単独の枠線でこれらの領域の枠線が示されていることを確認できます。

![ハイ コントラストで微妙な方法の詳細な例が失われること](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303 a_PropertiesWindow")<br />微妙な方法の詳細な例は、ハイ コントラスト時に失われます

#### <a name="choosing-text-colors-in-an-editor"></a>エディターでテキストの色を選択します。
色分けされたテキストでは、エディターまたはデザイン サーフェイスを類似した項目のグループを識別しやすくための許可などの意味を示すために使用されます。 ハイ コントラスト テーマでただし、されませんが 4 つ以上のテキストの色を区別する機能。 WindowText、GrayText および HotTrackText WindowBackground サーフェスで使用できる唯一の色がします。 3 色以上を使用することはできませんので、ハイ コントラスト モードのときに表示する最も重要な相違点を慎重に選択します。

各ハイ コントラスト テーマで表示されるとおりに、エディターの領域では、許可されるトークン名ごとの色相:

![ハイ コントラスト エディターの比較](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303 b_HCEditorComparison")<br />ハイ コントラスト エディターの比較

青のテーマで、エディターの画面の例:

![青のテーマでのエディター](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303 c_EditorBlue")<br />青のテーマでのエディター

![ハイコントラスト #1 テーマでのエディター](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303 d_EditorHC1")<br />ハイコントラスト #1 テーマでのエディター

### <a name="usage-patterns"></a>使用状況パターン
多くの一般的な UI 要素では、ハイコントラスト色の定義が既にあります。 UI 要素はのようなコンポーネントと一貫性のあるように、独自のシステムの色の名前を選択するときにこれらの使用パターンを参照することができます。

| システム カラー | 使用法 |
| --- | --- |
| ActiveCaption | アクティブな IDE し rafted ウィンドウ ボタンをホバー時およびキーを押して上のグリフ<br />IDE および rafted ウィンドウのタイトル バーの背景<br />既定のステータス バーの背景 |
| ActiveCaptionText | アクティブな IDE と rafted のウィンドウのタイトル バーの前景 (テキストとグリフ)<br />の枠線し、バック グラウンドのホバー時およびキーを押してアクティブなウィンドウのボタン |
| コントロール | -既定値を制御し、ドロップダウン ボタンの背景を無効になっているコンボ ボックス、ドロップダウン リスト、および検索<br />-ターゲット ボタンの背景をドッキングします。<br />コマンド バーの背景<br />ツール ウィンドウの背景色 |
| ControlDark | -IDE 背景<br />メニューとコマンド バーの区切り記号<br />コマンド バーの境界線<br />メニューをシャドウします。<br />ツール ウィンドウ タブの既定値とホバーの境界線および区切り記号<br />-ドキュメント オーバーフロー ボタンの背景では、<br />ドッキング対象グリフの境界 |
| ControlDarkDark |-フォーカスされていない、選択したドキュメント タブ ウィンドウ |
| ControlLight |自動的に隠す タブの境界線<br />-コンボ ボックスとドロップダウン リストの枠線<br />-ターゲット背景や罫線をドッキングします。 |
| ControlLightLight | -選択した対象を絞った開境界線 |
| ControlText | -コンボ ボックスとドロップダウン リストのグリフ<br />ツール ウィンドウの選択を解除 タブのテキスト |
| GrayText |の罫線、ドロップ ダウン グリフ、テキスト、およびメニュー項目のテキスト コンボ ボックスとドロップダウン リストが無効に<br />-無効なメニュー テキスト<br />検索コントロール '' 検索オプションのヘッダー テキスト<br />検索コントロール セクション区切り記号 |
| ハイライト | -すべてのホバー時および押された背景およびコンボ ボックス ドロップダウン ボタンの背景とドキュメントもオーバーフロー ボタンの境界線を除く、枠線<br />-選択した項目の背景 |
| HighlightText | -すべてのホバー時および押された foregrounds (テキストとグリフ)<br />フォーカスがあるツール ウィンドウとドキュメント タブ ウィンドウ コントロールの前景<br />フォーカスがあるツール ウィンドウのタイトル バーの境界線<br />フォーカスがある、選択した開 タブの前景色<br />ホバー時およびキーを押してのドキュメントもオーバーフロー ボタンの境界線<br />-選択したアイコンの境界線|
| ホット トラック | スクロール バーのバーのつまみの背景や罫線にキーを押します<br />-スクロール バーの矢印グリフ |
| InactiveCaption | -使用頻度の低い IDE し rafted ウィンドウ ボタンをホバー時のグリフ<br />IDE および rafted ウィンドウのタイトル バーの背景<br />-無効な検索コントロールの背景色 |
| InactiveCaptionText | -使用頻度の低い IDE と rafted windows タイトル バーの前景 (テキストとグリフ)<br />非アクティブ ウィンドウのボタンの背景とホバー時の枠線<br />-フォーカスされていないツール ウィンドウのボタンの背景や罫線<br />-無効な検索コントロールの前景色 |
| メニュー | ドロップダウン メニューの背景<br />-チェックされ、無効にされたチェック マークの背景 |
| MenuText | ドロップダウン メニューの境界線<br />-チェック マーク<br />グリフのメニュー<br />ドロップダウン メニューのテキスト<br />-選択したアイコンの境界線 |
| スクロール バー | -スクロール バー、スクロール バーの矢印のバック グラウンドでのすべての状態 |
| ウィンドウ | 自動的に隠す タブの背景<br />メニュー バーし、コマンド シェルフの背景<br />-フォーカスされていないか、選択されていないドキュメント ウィンドウ タブの背景とオープンと仮の両方のタブのためのドキュメントの境界線<br />-フォーカスされていないツール ウィンドウのタイトル バーの背景<br />ツール ウィンドウ タブの背景を両方選択されている、選択されていません |
| WindowFrame | の IDE 枠線 |
| WindowText | 自動的に隠す タブの前景色<br />-選択したツール ウィンドウ タブの前景色<br />-フォーカスされていないドキュメントのウィンドウ タブ、フォーカスされていないか、選択されていない開 タブの前景色<br />ツリー ビューの既定の前景色およびホバー未選択グリフ経由で<br />ツール ウィンドウ タブの境界線の選択<br />-スクロール バーのつまみのバック グラウンド、罫線、およびグリフ |

##  <a name="BKMK_ExposingColorsForEndUsers"></a> エンドユーザーの色を公開します。

### <a name="overview"></a>概要
コード エディターまたはデザイン画面を作成する場合と同様に、UI をカスタマイズするエンド ユーザーを許可する場合があります。 これを行う最も一般的な方法を使用して、**ツール&gt;オプション**ダイアログ。 カスタマイズを表示する最も簡単な方法を使用する高の専門的な UI の特殊なコントロールが必要ですが、しない限り、**フォントおよび色**内でページ、**環境**ダイアログ ボックスのセクションです。 カスタマイズ用に公開する各要素では、ユーザーは、前景の色、背景色、またはその両方を変更するを選択できます。

### <a name="building-a-vspackage-for-your-customizable-colors"></a>カスタマイズ可能な色の VSPackage をビルド
VSPackage では、カスタム カテゴリを色とフォントを制御でき、フォントおよび色 プロパティ ページにアイテムを表示することができます。 Vspackage を実装する必要がありますこのメカニズムを使用する場合、 [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx)インターフェイスとその関連するインターフェイスです。

原則として、既存のすべての表示項目とそれを格納するカテゴリを変更するこのメカニズムを使用できます。 ただし、その必要があります指定しないで、テキスト エディター カテゴリ、またはそのアイテムの表示を変更します。 [テキスト エディター] の詳細については、次を参照してください。[フォントと色の概要](../font-and-color-overview.md)です。

カスタムのカテゴリを実装またはアイテムの表示、VSPackage が必要です。

-   **作成または、レジストリ内のカテゴリを指定します。** IDE の実装、**フォントおよび色**プロパティ ページでは、この情報を使用して、正しく指定されたカテゴリをサポートするサービスを照会します。

-   **作成または (省略可能) のレジストリ内のグループを指定します。** 2 つまたは複数のカテゴリの和集合を表すグループを定義すると便利な場合があります。 グループが定義されている場合、IDE は自動的にサブカテゴリをマージし、配布グループ内のアイテムを表示します。

-   **IDE のサポートを実装します。**

-   **フォントと色の変更を処理します。**

#### <a name="to-create-or-identify-categories"></a>作成またはカテゴリを識別するには
カテゴリのレジストリ エントリの特殊な型を構築`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]`場所`<Category>`カテゴリのローカライズされていない名前を指定します。

2 つの値を使用してレジストリを設定します。

| 名前 | 型 | データ | 説明 |
| --- | --- | --- | --- |
| カテゴリ | REG_SZ | GUID | カテゴリを識別する GUID の作成 |
| Package | REG_SZ | GUID | カテゴリをサポートする VSPackage サービスの GUID |

 レジストリで指定されたサービスの実装を提供する必要があります[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)の対応するカテゴリ。

#### <a name="to-create-or-identify-groups"></a>作成またはグループを識別するには
カテゴリのレジストリ エントリの特殊な型を構築`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]`場所`<group>`グループのローカライズされていない名前を指定します。

2 つの値を使用してレジストリを設定します。

| 名前 | 型 | データ | 説明 |
|--- | --- | --- | --- |
| カテゴリ | REG_SZ | GUID | カテゴリを識別する GUID の作成 |
| Package | REG_SZ | GUID | カテゴリをサポートする VSPackage サービスの GUID |

レジストリで指定されたサービスの実装を提供する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>対応するグループです。

![先との実装](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304 a_FontAndColorGroup")<br />実装 `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>IDE のサポートを実装するには
実装[GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx)、いずれかが返されます、 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)インターフェイスまたは<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>カテゴリごとに、IDE へのインターフェイスまたはグループの GUID を指定します。

これをサポートしているすべてのカテゴリの VSPackage 実装の個別のインスタンス、 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)インターフェイスです。

メソッドの実装を通じて[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)を使用して IDE を提供する必要があります。

-   カテゴリの表示項目の一覧

-   表示項目のローカライズ可能な名前

-   カテゴリの各メンバーの情報を表示します。

 > **注:**すべてのカテゴリが少なくとも 1 つの表示項目を含める必要があります。

IDE を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>いくつかのカテゴリの共用体を定義するインターフェイスです。

その実装を使用して IDE を提供します。

-   指定したグループを構成するカテゴリの一覧

-   インスタンスへのアクセス[IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx)グループ内の各カテゴリをサポートします。

-   ローカライズ可能なグループ名

#### <a name="updating-the-ide"></a>IDE の更新
IDE では、フォントと色の設定に関する情報をキャッシュします。 そのため、IDE のフォントと色の構成の変更、後に、キャッシュが最新であることが保証をお勧めします。

キャッシュの更新は、操作には、 [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)インターフェイスし、実行のグローバルまたはだけで選択した項目を指定できます。

### <a name="handling-font-and-color-changes"></a>フォントと色の変更の処理
VSPackage を表示するテキストの色づけを正しくサポートするには、VSPackage をサポートする色付けサービスは、フォントおよび色のプロパティ ページに加えられたユーザーによる変更に応答する必要があります。

これを行うには、VSPackage では次の必要があります。

-   **IDE で生成されたイベントを処理**実装することによって、 [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx)インターフェイスです。 IDE では、次のユーザーの変更、フォントおよび色 ページの適切なメソッドを呼び出します。 たとえば、呼び出し、 [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx)メソッドの場合は、新しいフォントを選択します。

 **OR**

-   **IDE の変更をポーリング**です。 これは、操作にはシステムに実装された[IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)インターフェイスです。 永続化ストアのサポートについては、主には、 [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx)メソッドは、表示項目のフォントと色の情報を取得できます。 フォントおよび色の設定の詳細については、MSDN の記事を参照してください。[にアクセスする格納されているフォントと色の設定](../accessing-stored-font-and-color-settings.md)です。

> **注:**ポーリング結果が正しいことを確認するを使用して、 [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx)インターフェイスの取得方法を呼び出す前に、キャッシュのフラッシュと更新プログラムが必要なかどうかを決定する、 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx)インターフェイスです。

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>インターフェイスを実装することがなくカスタム フォントと色のカテゴリを登録します。
次のコード例では、カスタム フォントを登録し、インターフェイスを実装することがなくカテゴリのカラーする方法を示します。

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

このコード例。
-   `"NameID"` ローカライズされたカテゴリ名、パッケージ内のリソース ID を =
-   `"ToolWindowPackage"` = パッケージ GUID
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` 単なる例は、実際の値は、実装者によって提供される新しい GUID を指定できます。

### <a name="set-the-font-and-color-property-category-guid"></a>フォントおよびカラー プロパティ カテゴリ GUID を設定します。
カテゴリの Guid を設定するコード例を次に示します。

```
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
