---
title: "色と Visual Studio のスタイル設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# 色と Visual Studio のスタイル設定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Visual Studio での色を使用します。  
 Visual Studio で、色は、主に装飾としてだけでなく、通信ツールとして使用されます。 場合の予約し、最小限の色を使用します。  
  
-   意味または所属 \(たとえば、プラットフォームや言語の修飾子\) に送信します。  
  
-   読者の注意 \(たとえば、状態の変更を示す\)  
  
-   読みやすさを向上させるし、UI 内の移動に関する目標物を提供  
  
-   魅力を増やす  
  
 いくつかのオプションは、Visual Studio での UI 要素に色の割り当てに存在します。 場合によって、図が難しくなりますが正しく使用する方法や使用することになっているオプションを判断します。 このトピックを説明します。  
  
1.  さまざまなサービスと Visual Studio での色の定義に使用するシステムを理解します。  
  
2.  指定された要素の適切なオプションを選択します。  
  
3.  正しく指定したオプションを使用します。  
  
 **重要:** ハードコーディング 16 進数、RGB、または UI 要素に色のシステム カラーことはありません。 サービスを使用すると、柔軟性が色合いを調整します。 さらに、このサービスがないしないことができますのテーマを切り替える機能を活用するために、 [VSColor サービス](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)です。  
  
### Visual Studio インターフェイスの要素に色を割り当てる方法  
 UI 要素に最も適した方法を選択します。  
  
|UI|メソッド|どのようなにあるか。|  
|--------|----------|----------------|  
|埋め込まれているか、スタンドアロンのダイアログ ボックス。|**システム カラー**|オペレーティング システムは、コモン ダイアログ コントロールなどの色と UI 要素の外観を定義できるようにシステムの名前。|  
|カスタム UI を VS 環境全体で一貫性を維持する必要があり、カテゴリおよび共有のトークンの意味と一致する UI 要素があります。|**一般的な共有の色**|特定の UI 要素の既存の定義済みの色トークン名|  
|個々 の機能や機能のグループがあるし、類似した要素の共有の色はありません。|**カスタムの色**|色のトークン名領域に固有なを共有する他の UI ではありません。|  
|エンドユーザーが \(たとえば、テキスト エディターまたはデザイナー ウィンドウの特殊な\) UI またはコンテンツをカスタマイズしたりできるようにするには。|**エンドユーザーのカスタマイズ**<br /><br /> **\(ツール \> オプション\] ダイアログ ボックス\)**|"フォントおよび色\] ページで定義されている設定、 **ツール \> オプション** ダイアログまたは目的別ページの UI 機能の 1 つに固有です。|  
|HTML で作成した UI があります。|**Daytona**|色とフォントのサービスにアクセスする HTML で作成した UI を使用します。|  
  
### Visual Studio のテーマ  
 Visual Studio 機能を次の 3 つの異なる配色テーマ: ライト、暗い、および青。 ユーザー補助用に設計されたシステムの配色テーマは、ハイ コントラスト モードも検出します。  
  
 ユーザーは、最初に使用する Visual Studio の中にテーマを選択するように求められますに移動してテーマを後で切り替えができるように **ツール \> オプション \> 環境 \> 一般的な** "配色テーマ\] ドロップダウン メニューから新しいテーマを選択するとします。  
  
 ユーザーはコントロール パネルを使用してもいくつかのハイ コントラスト テーマの 1 つに、システム全体を切り替えます。 ユーザーは、ハイ コントラストのテーマを選択する場合、Visual Studio の色のテーマ セレクター不要になったに影響 Visual Studio の配色が、ハイ コントラスト モードを終了するときのため、テーマの変更は保存します。 ハイ コントラスト モードの詳細については、次を参照してください。 [ハイ コントラストの色を選択します。](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)します。  
  
### VSColor サービス  
 Visual Studio では、VSColor サービスは、使用すると、各 Visual Studio のテーマの色の値を含む名前付きエントリに UI 要素の色値がバインドと呼ばれる環境の色サービスを提供します。 これにより、色は、現在ユーザーが選択したテーマやシステム ハイ コントラスト モードを反映するように自動的に変更されます。 サービスの使用では、1 つの場所でのすべての色のテーマに関連する変更の実装が渡され、サービスからの一般的な共有色を使用している場合、UI が自動的に Visual Studio の今後のバージョンで新しいテーマを反映ことを示します。  
  
### 実装  
 Visual Studio ソース コードには、トークンの名前と各テーマのそれぞれの色の値のリストを含むいくつかのパッケージ定義ファイルが含まれています。 色のサービスでは、これらのパッケージ定義ファイルで定義されている VSColors を読み取ります。 これらの色が XAML マークアップまたはコードを参照し、いずれかで読み込まれます、 **IVsUIShell5.GetThemedColor** メソッドまたは DynamicResource マッピングです。  
  
### システム カラー  
 コモン コントロールは、既定では、システムの色を参照します。 埋め込まれた、またはスタンドアロンのダイアログ ボックスで作成する場合などのシステム カラーを使用するように UI をする場合は何もする必要はありません。  
  
### VSColor サービスでの一般的な共有色  
 インターフェイス要素には、全体的な Visual Studio 環境を反映する必要があります。 UI コンポーネントを設計するのに適した一般的な共有の色を再利用して、インターフェイスが他の Visual Studio インターフェイスと一致して、テーマを追加または更新するとき、色が自動的に更新を確認します。  
  
 一般的な共有の色を使用する前に、それらを正しく使用する方法を理解することを確認します。 一般的な共有色が不適切に使用すると、ユーザーのための一貫性のない、フラストレーションをまたは混乱を招くの操作可能性があります。  
  
### ユーザーがカスタマイズできる色  
 参照してください。 [エンドユーザーの色を公開します。](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 場合によっては、コード エディターまたはデザイン画面を作成する場合など、UI をカスタマイズするエンドユーザーを許可するされます。 カスタマイズ可能な UI コンポーネントは、 **フォントおよび色** のセクションで、 **ツール \> オプション** ダイアログ ボックスで、ユーザーが、前景色と背景色のどちらか一方または両方を選択できます。  
  
 ![Tools &#62; Options dialog in Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301\-a\_ToolsOptionsDialog")  
  
 **ツール \> オプション\] ダイアログ ボックス**  
  
### Web UI の色  
 Visual Studio Online との両方で Visual Studio 内で使用できるように、HTML を使用して、著者 UI コンポーネントに共通することが高まっています。 HTML で記述された UI は、Visual Studio 環境内で実行するときに、VSColor サービスを使用する必要があります。 Daytona とその使用方法については、次を参照してください。 [Daytona と web UI](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI)します。  
  
##  <a name="BKMK_TheVSColorService"></a> VSColor サービス  
 Visual Studio では、VSColor サービスまたはシェルの色のサービスとも呼ばれます環境の色サービスを提供します。 このサービスでは、各テーマの色を含む名前と値の色に UI 要素の色の値をバインドすることができます。 色は自動的に現在のユーザーが選択したテーマを反映するように変更し、UI は、環境の色のサービスにバインドされているようにと統合する新しいテーマ将来のバージョンの Visual Studio ように、すべての UI 要素の VSColor サービスを使用する必要があります。  
  
### サービスの動作方法  
 環境の色のサービスでは、UI コンポーネントの .pkgdef で定義されている VSColors を読み取ります。 これら VSColors XAML マークアップまたはコードで、参照されているし、いずれかで読み込まれて、 **IVsUIShell5.GetThemedColor** または DynamicResource マッピングです。  
  
 ![Environment color service architecture](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302\-a\_EnvironmentColorServiceArchitecture")  
  
 **環境の色のサービス アーキテクチャ**  
  
### サービスへのアクセス  
 アクセスするトークンの色の種類に応じて、VSColor サービスを使用しているコードの種類を使用していくつかの方法があります。  
  
#### 定義済みの環境の色  
  
##### ネイティブ コードから  
 シェルでは、色の COLORREF にアクセスできるようにサービスを提供します。 サービスまたはインターフェイスを示します。  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 ファイル VSShell80.idl、列挙体に **\_\_VSSYSCOLOREX** がシェルの色の定数です。 これを使用するには、MSDN に記載されている列挙 \_\_VSSYSCOLOREX からの値のいずれかの値のインデックスまたは通常のインデックス番号を Windows システム API に渡す **GetSysColor**, 、受け入れます。 これは、2 番目のパラメーターで使用される色の RGB 値で取得バックアップします。  
  
 ペンまたは新しい色とブラシを保存している場合、AdviseBroadcastMessages \(外部の Visual Studio シェル\) して WM\_SYSCOLORCHANGE と WM\_THEMECHANGED のメッセージをリッスンします。  
  
```  
// To access the color service in native code, you'll make a call that resembles this: pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **注:** によって返される値を「COLORREF **GetVSSysColorEx\(\)** だけ R G、が含まれてテーマ色の B 要素です。 テーマのエントリは、透明度を使用している場合は、戻る前にアルファ チャネルの値が破棄されます。 そのため、環境の任意の色は、透過なチャネルが重要となる場所で使用する必要がある場合は、このトピックで後述するよう IVsUIShell2::GetVSSysColorEx、代わりに IVsUIShell5.GetThemedColor を使用する必要があります。  
  
##### マネージ コードから  
 ネイティブ コードを VSColor サービスへのアクセスはいたって簡単です。 マネージ コードを使用している場合、サービスを使用する方法を決定する難しくなってきます。 念頭には、次にこのプロセスを示す c\# コード スニペットを示します。  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e) { //getIVSUIShell2 IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2; Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2"); if (uiShell2 != null) { //get the COLORREF structure uint win32Color; uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color); //translate it to a managed Color structure Color myColor = ColorTranslator.FromWin32((int)win32Color); //use it e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100); } }  
```  
  
 Visual Basic で作業している場合を使用します。  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### WPF の UI から  
 アプリケーションの ResourceDictionary にエクスポート値を通じて Visual Studio の色にバインドすることができます。 次には、カラー テーブルからリソースを使用して、XAML で環境フォント データへのバインドの例を示します。  
  
```  
<Style TargetType="{x:Type Button}"> <Setter Property="TextBlock.FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter Property="TextBlock.FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" /> <Setter Property="Background" Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" /> </Style>  
```  
  
#### ヘルパー クラスとマネージ コードのメソッド  
 マネージ コード用のシェルのパッケージの管理フレームワーク ライブラリ \(Microsoft.VisualStudio.Shell.12.0.dll\) には、いくつかテーマの色の使用を円滑にするヘルパー クラスにはが含まれています。  
  
 内のヘルパー メソッド、 **Microsoft.VisualStudio.Shell.VsColors** MPF でクラスが含まれて **GetThemedGDIColor\(\)** と **GetThemedWPFColor\(\)**します。 これらのヘルパー メソッドは、WinForms または WPF の UI で使用するには、System.Drawing.Color または System.Windows.Media.Color、としてテーマ エントリの色値を返します。  
  
```  
IVsUIShell5 shell5; Button button = new Button(); button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey); button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey); /// <summary> /// Gets a System.Drawing.Color value from the current theme for the given color key. /// </summary> /// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param> /// <param name="themeResourceKey">The key to find the color for.</param> /// <returns>The current theme's value of the named color.</returns> public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey); // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); } private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Guid category = themeResourceKey.Category; __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush) { colorType = __THEMEDCOLORTYPE.TCT_Background; } // This call will throw an exception if the color is not found uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType); return BitConverter.GetBytes(rgbaColor); } public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey); return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); }  
  
```  
  
 また、クラスを VSCOLOR の識別子を指定の WPF 色リソース キーの取得を使用またはその逆です。  
  
```  
public static string GetColorBaseKey(int vsSysColor); public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 メソッド **VsColors** クラスが呼び出されるたびに色の値を返す VSColor サービスを照会します。 としての色値を取得する **System.Drawing.Color**, 、代わりにパフォーマンスを向上させるには、代わりのメソッドを使用する、 **Microsoft.VisualStudio.PlatformUI.VSThemeColor** VSColor サービスから取得した色の値がキャッシュされているクラス。 クラスは、シェルのブロードキャスト メッセージのイベントを内部的にサブスクライブし、テーマ変更イベントが発生したときに、キャッシュされた値を破棄します。 また、クラスを提供します。テーマの変更を購読する NET が容易なイベントです。 使用して、 **ThemeChanged** 新しいハンドラーを追加して、イベント、 **GetThemedColor\(\)** の値が色を取得するメソッド、 **ThemeResourceKeys** 関心のあります。 サンプル コードは、次のようになります。  
  
```  
public MyWindowPanel() { InitializeComponent(); // Subscribe to theme changes events so we can refresh the colors VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged; RefreshColors(); } private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e) { RefreshColors(); // Also post a message to all the children so they can apply the current theme appropriately foreach (System.Windows.Forms.Control child in this.Controls) { NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero); } } private void RefreshColors() { this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey); this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey); } protected override void Dispose(bool disposing) { if (disposing) { VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged; base.Dispose(disposing);} }  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a> ハイ コントラストの色を選択します。  
  
### 概要  
 Windows は、テキスト、背景、および画像の色コントラストを向上させるいくつかのハイ コントラスト システム レベル テーマを使用し、画面のより明確に表示される要素を作成します。 ユーザー補助の理由から、ユーザーは、ハイ コントラストのテーマを切り替えると、Visual Studio インターフェイスの要素が正しく応答している重要な勧めします。  
  
 ハイ コントラストのテーマには、少数のシステム カラーを使用できます。 システム色の名前を選択する場合は、次のヒントに注意してください。  
  
1.  **を同じ意味を持つシステム カラーを選択して** 色分けは要素として。 たとえば、ウィンドウ内のテキストのハイ コントラスト カラーを選択する場合は、WindowText といない ControlText を使用します。  
  
2.  **前景色と背景色のペアを選択** 一緒またはすべてのハイ コントラスト テーマで、色の選択が動作する保証はできません。  
  
3.  **UI のどの部分が最も重要なであるかを判別して、コンテンツ領域の目立つことを確認してください。**強力な境界線の色の使用は、さまざまなコンテンツ領域の色のバリエーションが存在しないために、コンテンツ領域を定義する一般的なので、多くの色の色合いにわずかな違いを区別は通常、詳細は失われます。  
  
### システム カラー セット  
 ある表 [WPF チーム ブログ: SystemColors 参照](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) システム色の名前、および各テーマに表示される対応する色相の完全なセットを示します。  
  
 これを適用する制限のある、UI に色のセットと *「通常の」テーマ内に存在した微妙な細部が失われることを想定して*します。 ツール ウィンドウ内の領域を区別するために使用されるグレー色の微妙な UI の例を次に示します。 ハイ コントラスト モードで表示される同じウィンドウと組み合わせると、すべての背景は同じ色合いと、枠線だけでこれらの領域の枠線が示されていることを確認できます。  
  
 ![Properties window](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303\-a\_PropertiesWindow")  
  
 **ハイ コントラストで微妙な方法の詳細な例は失われます**  
  
#### エディターでテキストの色を選択します。  
 色分けされたテキストでは、エディターまたはデザイン サーフェイスを類似した項目のグループを識別しやすくを許可するなどの意味を示すために使用されます。 ハイ コントラスト テーマでただし、されませんが 3 つ以上のテキストの色を区別する機能。 WindowText、GrayText および HotTrackText は、WindowBackground サーフェスで利用できる唯一の色です。 3 色以上を使用できないために、ハイ コントラスト モードのときに表示する最も重要な相違点を慎重に選択します。  
  
 各ハイ コントラスト テーマで表示されるとおりに、エディターのサーフェイスに許可されるトークン名ごとの色相:  
  
 ![High Contrast editor comparison](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303\-b\_HCEditorComparison")  
  
 **ハイ コントラスト エディターの比較**  
  
 青のテーマでのエディターの画面の例:  
  
 ![Editor in Blue theme](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303\-c\_EditorBlue")  
  
 **青のテーマでのエディター**  
  
 ![Editor in High Contrast theme](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303\-d\_EditorHC1")  
  
 **ハイコントラスト \#1 テーマでのエディター**  
  
### 使用パターン  
 多くの一般的な UI 要素が既にあるは、ハイコントラスト色を定義します。 UI 要素に類似したコンポーネントと一貫性のあるように、独自のシステムの色の名前を選択する場合に、これらの使用状況パターンを参照することができます。  
  
|システム カラー|使用法|  
|--------------|---------|  
|ActiveCaption|-   アクティブな IDE し rafted ウィンドウ、ボタンをホバーとキーを押して上のグリフ<br />-   IDE および rafted ウィンドウのタイトル バーの背景<br />-   既定のステータス バーの背景|  
|ActiveCaptionText|-   アクティブな IDE と rafted ウィンドウのタイトル バーの前景 \(テキストとグリフ\)<br />-   バック グラウンドとホバーとキーを押してアクティブなウィンドウのボタンの境界線|  
|コントロール|-   コンボ ボックス、ドロップダウン リスト、および検索が既定とドロップダウン ボタンを含む、無効になっているバック グラウンドを制御します。<br />-   ターゲットのボタンの背景をドッキングします。<br />-   コマンド バーの背景<br />-   ツール ウィンドウの背景色|  
|プロパティ|-   IDE のバック グラウンド<br />-   メニューとコマンド バーの区切り記号<br />-   コマンド バーの境界線<br />-   メニュー シャドウ<br />-   ツール ウィンドウ\] タブの既定し、マウス ポインターの境界線と区切り記号<br />-   オーバーフロー ボタンの背景をも文書化します。<br />-   ドッキング ステーション対象グリフの境界|  
|ControlDarkDark|-   フォーカスされていない、選択したドキュメント タブ ウィンドウ|  
|ControlLight|-   自動非表示タブの境界線<br />-   コンボ ボックスとドロップダウン リストの枠線<br />-   ドッキング先の背景や罫線|  
|ControlLightLight|-   選択された状態でフォーカスがある一時的な境界線|  
|ControlText|-   コンボ ボックスとドロップダウン リストのグリフ<br />-   ツール ウィンドウが選択されていないタブのテキスト|  
|GrayText|-   コンボ ボックスやドロップダウン リストには、罫線、グリフのドロップダウン リスト、テキスト、およびメニュー項目のテキストが無効になっています<br />-   無効なメニュー テキスト<br />-   検索コントロールの \[検索オプション\] のヘッダー テキスト<br />-   検索コントロール セクション区切り記号|  
|強調表示します。|-   すべてを置き、背景や罫線のコンボ ボックスの一覧を除く、押されたボタンの背景とドキュメントもオーバーフロー ボタンの境界線<br />-   選択した項目の背景|  
|HighlightText|-   すべてのホバーおよび押された foregrounds \(テキストとグリフ\)<br />-   限定的なツール ウィンドウとドキュメント タブ ウィンドウ コントロールの前景<br />-   限定的なツール ウィンドウのタイトル バーの境界線<br />-   フォーカスのある、選択した一時的なタブの前景色<br />-   ホバー時とキーを押してドキュメントもオーバーフロー ボタンの境界線<br />-   選択したアイコンの境界|  
|ホット トラック|-   スクロール バーのつまみの背景とキーを押して \[枠線<br />-   キーを押して上のスクロール バーの矢印のグリフ|  
|InactiveCaption|-   非アクティブな IDE し rafted ウィンドウ、ボタンをホバー時のグリフ<br />-   IDE および rafted ウィンドウのタイトル バーの背景<br />-   無効な検索コントロールの背景色|  
|InactiveCaptionText|-   非アクティブな IDE と rafted windows タイトル バー前景色 \(テキストとグリフ\)<br />-   アクティブでないウィンドウのボタンの背景とホバー時の枠線<br />-   フォーカスされていないツール ウィンドウのボタンの背景や罫線<br />-   検索を無効になっているコントロールの前景色|  
|メニュー|-   ドロップダウン メニューの背景<br />-   Checked と無効になっているチェック マークのバック グラウンド|  
|MenuText|-   ドロップダウン メニューの境界線<br />-   チェック マークのチェック<br />-   グリフのメニュー<br />-   ドロップ ダウン メニュー テキスト<br />-   選択したアイコンの境界|  
|スクロール バー|-   スクロール バーとスクロール バーの矢印の背景、すべての状態|  
|ウィンドウ|-   自動的に隠す\] タブの背景<br />-   メニュー バーし、コマンドの棚のバック グラウンド<br />-   フォーカスされていないか、選択されていないドキュメント ウィンドウ\] タブの背景とドキュメントの枠線、オープン、および一時的な\] タブ<br />-   フォーカスされていないツール ウィンドウのタイトル バーの背景<br />-   ツール ウィンドウ\] タブの背景を両方選択し、選択解除|  
|WindowFrame|-   IDE の枠線|  
|WindowText|-   自動的に隠す\] タブの前景色<br />-   選択したツール ウィンドウ\] タブの前景色<br />-   フォーカスされていないドキュメント ウィンドウ\] タブに、フォーカスされていないか、選択されていないの一時的なタブの前景色<br />-   ツリー ビューの既定の前景、グリフが選択されていないポイント<br />-   ツール ウィンドウの選択されているタブ境界線<br />-   スクロール バーのつまみの背景、罫線、およびグリフ|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> エンドユーザーの色を公開します。  
  
### 概要  
 コード エディターまたはデザイン画面を作成する場合など、UI をカスタマイズするエンドユーザーを許可する場合があります。 これを行う最も一般的な方法を使用して、 **ツール \> オプション** ダイアログ。 特殊なコントロールを必要とする UI が高い専門化しない限り、カスタマイズを提示する最も簡単な方法は、 **フォントおよび色** 内でページ、 **環境** ダイアログの部分です。 カスタマイズ用の公開された各要素に対して、ユーザーは、前景色と背景色のどちらか一方または両方を選択できます。  
  
### カラーのカスタマイズ可能な場合、VSPackage を作成します。  
 VSPackage では、フォントおよびカスタムのカテゴリの色を制御して、フォントおよび色\] プロパティ ページにアイテムを表示することができます。 Vspackage を実装する必要がありますこのメカニズムを使用する場合、 [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) インターフェイスと関連付けられているインターフェイス。  
  
 原則として、既存のすべての表示項目およびそれを格納するカテゴリを変更するこのメカニズムを使用できます。 ただし、その指定しないで \[テキスト エディター\] またはその表示項目を変更します。 テキスト エディター\] カテゴリの詳細については、次を参照してください。 [フォントと色の概要](https://msdn.microsoft.com/en-us/library/bb165065.aspx)します。  
  
 カスタム カテゴリを実装するか、項目を表示、VSPackage 必要があります。  
  
-   **作成するか、レジストリ内のカテゴリを特定します。**IDE の実装、 **フォントおよび色** \] プロパティ ページでは、この情報を使用して、1 つのカテゴリをサポートするサービスのクエリを正常にします。  
  
-   **作成または \(省略可能\) のレジストリ内のグループを指定します。**2 つまたは複数のカテゴリの和集合を表すグループを定義すると便利な場合があります。 グループが定義されている場合、IDE によって自動的にサブカテゴリをマージし、配布グループ内のアイテムを表示します。  
  
-   **IDE のサポートを実装します。**  
  
-   **フォントと色の変更を処理します。**  
  
#### 作成またはカテゴリを指定するには  
 \[Hklm \\software\\microsoft \\Visual Studio\\ \< Visual Studio のバージョン \> \\FontAndColors\\ \< Category \>\] の下のレジストリ エントリのカテゴリの特殊な型を作成します。 \< category \> は、カテゴリのローカライズされていない名前です。  
  
 2 つの値を使用してレジストリを設定します。  
  
|名前|型|データ|説明|  
|--------|-------|---------|--------|  
|カテゴリ|REG\_SZ|GUID|カテゴリを識別するために、GUID の作成|  
|パッケージ|REG\_SZ|GUID|カテゴリをサポートする VSPackage サービスの GUID|  
  
 レジストリで指定されたサービスの実装を提供する必要があります [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) の対応するカテゴリ。  
  
#### グループを作成または識別するのには  
 \[Hklm \\software\\microsoft \\Visual Studio\\ \< Visual Studio のバージョン \> \\FontAndColors\\ \< グループ \>\] の下のレジストリ エントリのカテゴリの特殊な型を作成します。 \< グループ \> は、グループのローカライズされていない名前です。  
  
 2 つの値を使用してレジストリを設定します。  
  
|名前|型|データ|説明|  
|--------|-------|---------|--------|  
|カテゴリ|REG\_SZ|GUID|カテゴリを識別するために、GUID の作成|  
|パッケージ|REG\_SZ|GUID|カテゴリをサポートする VSPackage サービスの GUID|  
  
 レジストリで指定されたサービスの実装を提供する必要があります **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** の対応するグループです。  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304\-a\_FontAndColorGroup")  
  
### IDE のサポートを実装するには  
 実装 [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), を返すことをするか、 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) インターフェイスまたは **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** カテゴリごとに、IDE へのインターフェイスまたは指定された GUID をグループ化します。  
  
 VSPackage としては、すべての項目の個別のインスタンスを実装して、 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) インターフェイスです。  
  
 メソッドの実装を通じて [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) を使用して IDE を提供する必要があります。  
  
-   カテゴリの表示項目の一覧  
  
-   表示項目のローカライズ可能な名前  
  
-   カテゴリの各メンバーの情報を表示します。  
  
 **注:** のすべてのカテゴリには、少なくとも 1 つの表示項目が含まれている必要があります。  
  
 IDE を使用して、 **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** いくつかのカテゴリの和集合を定義するインターフェイスです。  
  
 その実装を使用して IDE を提供します。  
  
-   指定したグループを構成するカテゴリの一覧  
  
-   インスタンスへのアクセス [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) グループ内の各カテゴリをサポートします。  
  
-   ローカライズ可能なグループ名  
  
#### IDE の更新  
 IDE では、フォントと色の設定に関する情報をキャッシュします。 そのため、IDE のフォントと色の構成の変更、後に、キャッシュが最新であることが保証をお勧めします。  
  
 キャッシュの更新を行う、 [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) インターフェイスし、実行のグローバルまたはだけで選択した項目を指定できます。  
  
### フォントと色の変更の処理  
 VSPackage を表示するテキストの色付けを正しくサポートするには、VSPackage をサポートする色付けサービスは、フォントおよび色のプロパティ\] ページを通じて行われたユーザーによる変更に応答する必要があります。  
  
 これを行うには、VSPackage 必要があります。  
  
-   **IDE によって生成されたイベントを処理** 実装することによって、 [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) インターフェイスです。 IDE では、フォントおよび色\] ページのユーザーによる変更の後、適切なメソッドを呼び出します。 たとえばの呼び出し、 [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) メソッドが新しいフォントが選択されている場合。  
  
 **OR**  
  
-   **、IDE の変更をポーリング**します。 これをシステムに実装された [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) インターフェイスです。 主に、永続化のサポートでは、 [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) メソッドは、表示項目のフォントと色の情報を取得できます。 フォントおよび色の設定の詳細については、MSDN の記事を参照してください。 [にアクセスする格納されているフォントと色の設定](https://msdn.microsoft.com/en-us/library/bb166382.aspx)します。  
  
 **注:** ポーリング結果が正しいことを確認するを使用して、 [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) の取得方法を呼び出す前に、キャッシュのフラッシュと更新プログラムが必要なかどうかを判断するインターフェイス、 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) インターフェイスです。  
  
#### インターフェイスを実装することがなく、カスタム フォントと色のカテゴリを登録します。  
 次のコード例では、インターフェイスを実装することがなく色分け類項目をカスタム フォントを登録する方法を示しています。  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window] "Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}" "Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" "ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}" "NameID"=dword:00000064  
```  
  
 **注:**  
  
-   "NameID"パッケージにローカライズされたカテゴリ名のリソース ID \=  
  
-   "ToolWindowPackage"パッケージの GUID を \=  
  
-   "Category"\="{9FF46859\-A47E\-47bf\-8AC5\-EC3DBE69D1FE}"はほんの一例と、実際の値は、実装者によって提供される新しい GUID を指定できます。  
  
### フォントおよび色プロパティ カテゴリの GUID を設定します。  
 次のコード例では、カテゴリの Guid の設定を示します。  
  
```  
// m_pView is your IVsTextView IVsTextEditorPropertyCategoryContainer spPropCatContainer = (IVsTextEditorPropertyCategoryContainer)m_pView; if (spPropCatContainer != null) { IVsTextEditorPropertyContainer spPropContainer; Guid GUID_EditPropCategory_View_MasterSettings = new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}"); hr = spPropCatContainer.GetPropertyCategory( ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer); if(hr == 0) { hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID); hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID); } }  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a> Daytona と web UI  
  
### 概要  
 "Daytona"は、Api、ツール、および HTML、CSS、およびさまざまな Visual Studio または f12 キーを押すなどのホストで使用できる JavaScript でプラグインを作成するユーザーを有効にするサービスのセットです。 プラグインは、HTML、CSS および JavaScript で記述された、ポータブル コンポーネントと省略可能なホストに固有のコンポーネントで構成されます。 各 Daytona ホストには、UI の表記規則、暗黙的または明示的にプラグインする必要がありますネイティブの環境を表示するために従っていることの独自セットを設定できます。 Visual Studio などの一部のホストには、エンドユーザーがスタイル シートを作成するときに、ホストの視覚的な側面を静的に対象することはできませんするために、既定の「テーマ」に変更を行いますができるようにします。 これにより、問題がポータブル プラグインを作成する開発者が生じます。 このトピックでは、web テーマとハイ コントラストの両方を正しくサポートするように、Daytona ホストを使用して Visual Studio に表示される UI を作成する方法について説明します。  
  
### Daytona テーマ メカニズム  
 Daytona ランタイムは、UI の表記規則を抽象化する一連のサービスとホストのテーマの機能を提供します。 これらのサービスでは、プラグインが自動的に visual でホストされている環境に基づくユーザーの期待を満たしていることを確認します。 この動作は、次の 3 つの主な機能で提供されます。  
  
1.  透過的にプラグインの UI に CSS ルールのセットを適用し、HTML コントロール \(たとえば、HTMLInputElement および HTMLButtonElement 一連の既定のスタイルを設定するランタイムにより挿入されたスタイル シート \(plugin.css\)  
  
2.  ハードコードされたのではなくテーマに基づいて値を使用して UI 要素のスタイルを使用できるホストから提供されたトークンのセット  
  
    1.  CSS を使用してこれらのトークンにアクセスするための宣言構文  
  
    2.  JavaScript からプログラムを使用してテーマ トークンにアクセスするための API  
  
3.  テーマの変更の通知  
  
#### ランタイムにより挿入されたスタイル シート  
 スタイルを挿入するホストと Daytona ランタイム座標はシート自動的にプラグインの標準的な UI 要素のテーマです。 これには、次の概念については、スタイル設定が含まれます。  
  
-   環境フォント  
  
-   背景色  
  
-   ハイパーリンク  
  
-   フォーム コントロール \(例: \< 選択 \> \< 入力 \>、\< ボタン \>  
  
-   \[テーブル\]  
  
-   見出し  
  
-   スクロール バー  
  
 つまり、こと、UI が標準の HTML UI コントロールの完全で構成される場合、追加の作業は必要ないテーマの変更に応答し、ハイ コントラストをサポートするためです。  
  
#### カスタム UI  
 ほぼすべての重要なケースで標準の HTML の UI コントロールはプラグインの包括的なエクスペリエンスを提供するための十分なカスタム UI を導入する必要があります。 適切なフォントの選択および色の使用をサポートするために **テーマ トークン** CSS で宣言または以下に示す JavaScript API を使用して強制的に使用する必要があります。 Daytona ランタイムは、プラグインの読み込みとテーマの変更は、これらのトークンを使用してスタイル シートの更新の対処します。  
  
##### テーマ トークン  
 両方の標準とホスト固有のテーマ トークン利用できます。 標準トークンは、ホストにより挿入された常に利用可能です。 可能な場合は、標準的なトークンを使用することをお勧めします。 標準トークンからのすべてのホストを指定することが保証され、本質的に移植性の高いプラグインには、それらを使用します。 唯一の新しいトークンを追加する必要があり、\[なし\] を削除するか、一連の標準トークンは、変更されます。 Visual Studio 2013 バージョンは、以下に記載されています。  
  
|トークンの名前|説明|  
|-------------|--------|  
|背景色のプラグイン|プラグインの既定の背景色|  
|プラグインの色|プラグインの既定の前景色|  
|プラグイン contextmenu アクティブな色|既定の選択の前景色がアクティブであるときに、コンテキスト メニュー \(にフォーカスがある\)|  
|プラグイン コンテキスト メニュー背景色|コンテキスト メニューの既定の背景色|  
|プラグイン contextmenu 罫線色|コンテキスト メニューの既定の境界線の色|  
|プラグイン contextmenu カラー|コンテキスト メニューの既定の前景色|  
|プラグイン contextmenu ホバー色|コンテキスト メニューの既定のホバー時の背景色|  
|プラグインのコンテキスト メニューのホバー時の色|コンテキスト メニューの既定のホバー時前景色|  
|プラグイン contextmenu アイコン チェック|コンテキスト メニューの既定\] チェック ボックス アイコンの色|  
|プラグインのコンテキスト メニュー\-使用頻度の低いの色|既定の選択の前景色アクティブでないときに、コンテキスト メニュー|  
|プラグイン contextmenu 区切り文字色|コンテキスト メニューの既定の区切り記号の色|  
|フォント ファミリのプラグイン|このプラグインを使用する既定のフォント ファミリ|  
  
 Visual Studio で、次のプラグイン フォント トークンは、環境フォントの設定に基づいています。  
  
-   フォント サイズのプラグイン  
  
-   プラグインのフォントの太さ  
  
-   プラグインの強調表示の背景色  
  
-   プラグイン強調表示色  
  
-   非アクティブな色のプラグイン  
  
 次のプラグインのリンク トークンを使用して、HTMLElements \(ハイパーリンク\) のスタイルを設定します。  
  
-   プラグインの色のリンク  
  
-   プラグインのリンクのアクティブな色  
  
-   プラグイン リンク ホバー色  
  
 Plugin.css のサポートを強化する次のトークンを使用して既定では、スクロール バーが \(具体的には、Visual Studio\) でホストがさまざまなテーマでスタイルします。  
  
-   プラグイン スクロール バーの矢印色  
  
-   プラグイン スクロール バーの背景色  
  
-   プラグイン scrollbar 表面色  
  
 次のプラグインの選択のトークンを使用して、HTMLSelectElement \(コンボ ボックス ドロップダウン\) のスタイルを設定します。  
  
-   プラグインの選択\-オプション\-背景色  
  
-   プラグインを選択オプション色  
  
-   plugin\-select\-option\-checked\-background\-color  
  
-   plugin\-select\-option\-checked\-border\-color  
  
-   plugin\-select\-option\-checked\-foreground\-color  
  
-   plugin\-select\-option\-hover\-background\-color  
  
-   plugin\-select\-option\-hover\-border\-color  
  
-   plugin\-select\-option\-hover\-foreground\-color  
  
-   プラグインを選択境界線色  
  
-   プラグイン \[背景色  
  
-   プラグイン \[前景色\]  
  
-   プラグインの選択のホバー時の背景色  
  
-   プラグインを選択\-ホバー\-罫線の色  
  
-   プラグインの選択\-ホバー時の前景色\-\]  
  
-   プラグインのテーブルの境界線色  
  
-   プラグインのテーブルのヘッダーの背景色  
  
-   プラグインのテーブル ヘッダー色  
  
-   プラグイン\] テキスト ボックスの境界線色  
  
-   プラグイン\] テキスト ボックスの背景色  
  
-   プラグインの色\] ボックスに貼り付けます  
  
-   プラグインのテキスト ボックスに無効になっている\-背景色  
  
-   プラグイン\-テキスト ボックス\-無効になっている\-罫線の色  
  
-   プラグイン\] テキスト ボックスに無効になっている色  
  
 これらのトークンを使用する *すべて* ツリー ビューおよびテーブルの適切な既定値がテーマとハイ コントラストをサポートするさまざまなホストに設定しているため。  
  
-   プラグインのツリー ビュー\-コンテンツの背景色  
  
-   プラグイン treeview コンテンツ色  
  
-   plugin\-treeview\-content\-inactive\-selected\-color  
  
-   plugin\-treeview\-content\-mouseover\-background\-color  
  
-   プラグインの treeview\-コンテンツ\-マウスを置いたときの色  
  
-   plugin\-treeview\-content\-inactive\-selected\-color  
  
-   plugin\-treeview\-content\-selected\-background\-color  
  
-   plugin\-treeview\-content\-selected\-border\-color  
  
-   プラグイン treeview\-コンテンツの選択の色  
  
##### ホスト固有のトークン  
 トークンの標準セットをサポートしているだけでなく、ホストは非標準トークンを提供する可能性がありますもします。 Visual Studio ホスト マニフェストの Visual Studio 固有のセクションのテーマのトークンの別名を指定するためのプラグインを許可することで行われます。 例:  
  
```  
"vs": { "theme_token_aliases": { "diagnostics-host-border": { "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22", "key_type": "BackgroundColor", "name": "Border" }, ... } }  
  
```  
  
 この例では、テーマ、トークン「診断\-ホストの境界、」という名前と同じを上記で説明した標準的なトークンを参照できますが導入されています。 色を解決するのには、カテゴリ、key\_type、および名前が使用される、 **IVsFontAndColorStorage** インターフェイスです。 多くの場合は、vscommon\\themes にある XML ファイルに適切な色 \(と、カテゴリ、key\_type、および名前の情報\) を検索します。 パッケージが導入された新しい構成可能な色場合これと同じメカニズムを使用します。 カテゴリ、key\_type、および名前を使用する色に一致します。 プラグインの作成者は、可能な限り、標準的なトークンを使用しようとしています。 と、どうしても必要な場合、ホスト固有のトークンのみを使用する必要があります。  
  
##### CSS でテーマのトークンの使用  
 テーマのトークンは、具体的には書式設定されたコメント構文を使用して参照されます。 トークンを解析するための規則:  
  
1.  コメントの式は角かっこで囲む必要があります \(\)。  
  
2.  式の外側で、コメント内のすべての空白は無視されます。  
  
3.  コメント式は、置換プロパティを直接従う必要があります。  
  
4.  式内の先頭または末尾の空白文字は除去されます。  
  
5.  式に含まれる各トークンの名前は、中かっこで囲む必要があります \(たとえば、 **{フォント ファミリ}** と **{ボタン ホバー カラー}**\)。 それ以外の場合、リテラル値として処理されます。  
  
 トークンのパーサーがあると仮定して、CSS の値を置換する方法の例を次に、 **プラグイン背景色** トークン \#000 の値には、および **プラグイン フォント ファミリ** トークン"Verdana"の値には  
  
|ユーザーが作成した CSS|CSS の解析|ノート|  
|-------------------|-------------|---------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|既定値は、ホスト固有の動的な値に置き換えられます。|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|式の外部での空白は無視されます。|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|式内の末尾、先頭の空白文字は切り捨てられます。|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|式が角かっこで囲まれていないし、そのため、コメントは無視されます。|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|トークンは、中かっこで囲まれていないし、リテラルの値として扱われるためです。|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|コメントは、プロパティの値に従っていないし、したがっては無視されます。|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #fff;`|*上記と同じ*|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|*上記と同じ*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|トークンが置き換えられ、リテラルのコンテンツが保持されます。|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*上記と同じ*|  
  
 CSS ファイルには、テーマのトークンが含まれている場合は、HTML ファイル内のリンク要素のデータのプラグインの theme 属性でマークする必要があります。 例:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### JavaScript からテーマ トークンを使用します。  
 カスタム UI は、テーマが適用された CSS で可能な限り必要がありますがシナリオがあるテーマの値のトークンのプログラムからアクセスする必要があります。 たとえば、カスタム UI が CSS からスタイルを継承しない CanvasElement 上に描画されている場合、または UI 要素が動的にされている場合は、スタイル シートを参照するいるとは対照的に作成されます。 Daytona API を使用して、シナリオが有効になっている **Plugin.Theme.getValue**します。 この関数は、トークン名を指定すると、ホストから提供されたテーマ値を返します。  
  
|テーマが適用されたできません。|テーマが適用されました。|  
|---------------------|------------------|  
|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = "#ccc"; surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = ("plugin-background-color"); surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div"); el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div"); el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 JavaScript からトークンが使用される場合**, 、テーマ変更イベントを処理すると、更新に対応する必要があります**します。 これは CSS では、宣言的に使用するテーマ トークンに必要な Daytona ランタイムがに代わって、プラグインとします。 テーマのイベントは、次のように処理できます。  
  
|メンバー \(1 つのハンドラー\)|DOM イベント \(複数のハンドラーを\)|  
|------------------------|----------------------------|  
|`Plugin.Theme.onchange = function () { // re-draw dynamic UI here }`|`Plugin.Theme.addEventListener("change", function () { // re-draw dynamic UI here });`|  
  
 この場合、なりますを再度呼び出す非常に一般的な **Plugin.Theme.getValue** テーマが変更されたときに変更された可能性の高いテーマ トークンの値として、これらのハンドラーにします。  
  
##### トークンの標準のマッピング  
 標準のトークンは、環境とシェルの色にマップされます。 次の一覧は、これらのマッピングのフレーバーを示しています。  
  
|トークンの名前|VS のマッピング \(EnvironmentColors\)|  
|-------------|-------------------------------------|  
|プラグインの色|ToolWindowTextColorKey|  
|背景色のプラグイン|ToolWindowBackgroundColorKey|  
|プラグインの色のリンク|ControlLinkTextColorKey|  
|プラグイン リンク ホバー色|ControlLinkTextHoverColorKey|  
|プラグインのリンクのアクティブな色|ControlLinkTextPressedColorKey|  
|プラグイン強調表示色|HighlightTextColorKey|  
|プラグインの強調表示の背景色|HighlightColorKey|  
|プラグインのテーブルのヘッダーの背景色|GridHeadingBackgroundColorKey|  
|プラグインのテーブル ヘッダー色|GridHeadingTextColorKey|  
|プラグインのテーブルの境界線色|GridLineColorKey|  
|プラグイン ボタンの背景色|ButtonFaceColorKey|  
|プラグインのボタン\-ホバー時の背景色|ButtonHighlightColorKey|  
|プラグインの色\] ボタン|ButtonTextColorKey|  
|プラグイン ボタンの境界線色|ButtonBorderColorKey|  
  
##### テーマの変更  
 Visual Studio ホスト トリガー プラグイン テーマの変更時に、エンドユーザーは、次の設定に変更を加えます。  
  
 **配色テーマ:**  
  
 ![Color theme changes](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305\-a\_ColorTheme")  
  
 **環境テーマ:**  
  
 ![Environment theme changes](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305\-b\_EnvironmentTheme")  
  
 **オペレーティング システムのテーマ** \(ハイ コントラストとの間の変更\) の場合のみ。  
  
 ![OS theme changes](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305\-c\_OSTheme")