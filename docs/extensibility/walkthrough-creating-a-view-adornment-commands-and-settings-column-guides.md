---
title: ビューの表示要素、コマンドおよび設定の作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4de9446afcc7528ba5c27160b4e00ad911b657e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958742"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>チュートリアル: ビューの表示要素、コマンド、および設定 (ガイド) を作成します。
コマンドとビューの効果を Visual Studio のテキストまたはコード エディターを拡張することができます。 この記事では、人気のある拡張機能、列ガイドを使用する方法を示します。 列ガイドは、特定の列の幅にコードを管理するために、テキスト エディターのビューに描画される視覚的にライトの線です。 具体的には、書式設定されたコードは、ドキュメント、ブログの投稿に含めるか、バグのレポートのサンプルについてがあります。

このチュートリアルでしました。
- VSIX プロジェクトを作成します。
- エディター ビューの表示要素を追加します。
- 保存と設定の取得 (どこに描画列ガイドと、色) のサポートを追加します。
- コマンドの追加 (列ガイドの追加と削除、その色を変更する)
- テキスト ドキュメントのコンテキスト メニューの [編集] メニューで、コマンドを配置します。
- Visual Studio コマンド ウィンドウからコマンドを呼び出すためのサポートを追加します。  
  
  この Visual Studio ギャラリーで列ガイド機能のバージョンを試すことができます[拡張子](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)します。  
  
  **注**: このチュートリアルでは、Visual Studio 拡張機能テンプレートによって生成されるいくつかのファイルに大量のコードを貼り付けます。 しかし、すぐにこのチュートリアルでは他の拡張機能の例を含む GitHub で完成したソリューションを参照します。 Generictemplate アイコンを使用する代わりに実際のコマンドのアイコンがあることで、完成したコードは若干異なります。

## <a name="get-started"></a>作業開始
Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。

## <a name="set-up-the-solution"></a>ソリューションをセットアップします。
最初に、VSIX プロジェクトを作成する、エディター ビュー表示要素を追加し (これは、コマンドを所有するために VSPackage を追加) コマンドを追加します。 基本的なアーキテクチャは次のとおりです。
- テキスト ビュー作成リスナーを作成するがある、`ColumnGuideAdornment`ビューごとにオブジェクト。 このオブジェクトがビューの変更に関するイベントをリッスンまたはの設定変更、列を更新または再描画が必要に応じてガイドします。
- `GuidesSettingsManager` Visual Studio の設定の保存場所から読み取りと書き込みを処理します。 設定マネージャーは、ユーザーのコマンドをサポートする設定を更新するための操作もあります (列を追加、列の削除、色を変更する)。
- ユーザーのコマンドがある場合に必要な VSIP パッケージがありますが、コマンドの実装オブジェクトを初期化する定型コードだけです。
- `ColumnGuideCommands`ユーザーを実行しているオブジェクトのコマンドで宣言されたコマンドは、コマンド ハンドラーをフック、 *.vsct*ファイル。  
  
  **VSIX**します。 使用して**ファイル &#124; です。新機能 ...** プロジェクトを作成するコマンド。 選択、**拡張**ノードの下**c#** 左側のナビゲーション ウィンドウで選択**VSIX プロジェクト**右側のペインでします。 名前を入力します**ColumnGuides**選択**OK**プロジェクトを作成します。  
  
  **装飾の表示**します。 ソリューション エクスプ ローラーでプロジェクト ノードを右ポインター ボタンを押します。 選択、**追加&#124;新しい項目.** 新しいビューの表示要素項目を追加するコマンド。 選択**拡張&#124;エディター**左側のナビゲーション ウィンドウで選択**エディターのビューポート Adornment**右側のウィンドウで。 名前を入力します**ColumnGuideAdornment**項目として名前を指定し、選択**追加**に追加します。  
  
  この項目テンプレートのプロジェクト (だけでなく、参照およびなど) に 2 つのファイルの追加を確認できます。**ColumnGuideAdornment.cs**と**ColumnGuideAdornmentTextViewCreationListener.cs**します。 テンプレートは、ビューで、紫色の四角形を描画します。 次のセクションでは、ビューの作成のリスナー内の行のいくつかの変更し、の内容を置き換えます**ColumnGuideAdornment.cs**します。  
  
  **コマンド**します。 **ソリューション エクスプ ローラー**、プロジェクト ノードの右のポインター ボタンを押します。 選択、**追加&#124;新しい項目.** 新しいビューの表示要素項目を追加するコマンド。 選択**拡張&#124;VSPackage**左側のナビゲーション ウィンドウで選択**カスタム コマンド**右側のウィンドウでします。 名前を入力します**ColumnGuideCommands**項目として名前を指定し、選択**追加**します。 コマンドとも追加するパッケージを追加するだけでなく、複数の参照**ColumnGuideCommands.cs**、 **ColumnGuideCommandsPackage.cs**、および**ColumnGuideCommandsPackage.vsct**. 次のセクションでは、定義して、コマンドを実装する最初と最後のファイルの内容を置き換えます。

## <a name="set-up-the-text-view-creation-listener"></a>テキスト ビューの作成のリスナーを設定します。
開いている*ColumnGuideAdornmentTextViewCreationListener.cs*エディターでします。 このコードは、for Visual Studio でのテキスト ビューを作成するたびに、ハンドラーを実装します。 ビューの特性に応じて、ハンドラーが呼び出されたときを制御する属性があります。

コードは、装飾層も宣言する必要があります。 更新すると、エディター ビュー、ビューの表示要素のレイヤーを取得しをからには、表示要素の要素を取得します。 します。 属性を持つ他と比較した、レイヤーの順序を宣言することができます。 次の行に置き換えます。

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

これらの 2 行。

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

交換した行は、装飾層を宣言する属性のグループです。 最初の行の列のガイド線が表示される場所の変更のみを変更しました。 「前」をビュー内のテキストの背後にある、またはテキストの下に表示されることを意味に、します線を描画します。 2 行目では、列ガイドの表示要素は、概念のドキュメントに適合するエンティティをテキストに適用されますが、編集可能なテキストに対してのみ機能するなど、表示要素を宣言する可能性がありますを宣言します。 詳細については、[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>設定マネージャーを実装します。
内容を置き換える、 *GuidesSettingsManager.cs*を次のコード (詳細は後述)。

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

このコードのほとんどは、作成し、設定の形式を解析します。"RGB (\<int >、\<int >、\<int >) \<int >、 \<int >,..."です。  最後に、整数は、列ガイドとなる 1 から始まる列です。 列ガイドの拡張機能は、1 つの設定値の文字列内のすべての設定をキャプチャします。

注目すべきコードの一部があります。 次のコード行では、設定の保存場所の Visual Studio のマネージ ラッパーを取得します。 ほとんどの場合、これを Windows レジストリを抽象化が、この API は、ストレージ メカニズムに依存しません。

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Visual Studio のストレージ設定は、すべての設定を一意に識別するために、カテゴリ識別子と設定の識別子を使用します。

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

使用する必要はありません`"Text Editor"`カテゴリ名とします。 好きなデザインを選択することができます。

最初のいくつかの関数は、設定を変更するエントリ ポイントです。 これらは、許可されているガイドの最大数などの高度な制約を確認します。  次にそれらを呼び出す`WriteSettings`、設定文字列を作成し、プロパティを設定する`GuideLinesConfiguration`します。 Visual Studio 設定ストアと起動設定値を保存しますこのプロパティを設定、`SettingsChanged`すべてを更新するイベント、`ColumnGuideAdornment`テキスト ビューに関連付けられている各オブジェクトします。

など、いくつかのエントリ ポイント関数がある`CanAddGuideline`設定を変更するコマンドを実装するために使用されます。 Visual Studio には、メニューが表示されている場合は、かどうかのコマンドは、有効では、その名前が表示するコマンドの実装と具合を照会します。  次のコマンドの実装には、これらのエントリ ポイントをフックする方法について参照してください。 コマンドの詳細については、次を参照してください。[メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)します。

## <a name="implement-the-columnguideadornment-class"></a>ColumnGuideAdornment クラスを実装します。
`ColumnGuideAdornment`を修飾できるテキスト ビューごとにクラスをインスタンス化します。 このクラスは、ビューの変更や設定を変更すると、必要に応じて更新または再描画列ガイドに関するイベントをリッスンします。

内容を置き換える、 *ColumnGuideAdornment.cs*を次のコード (詳細は後述)。

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon 
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged += 
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment 
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

このクラスのインスタンスを関連付けられている保持<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>と一連の`Line`ビュー上に描画するオブジェクト。

コンス トラクター (から呼び出される`ColumnGuideAdornmentTextViewCreationListener`Visual Studio で新しいビューを作成するときに) 列ガイドを作成します。`Line`オブジェクト。  コンス トラクターものハンドラーを追加、`SettingsChanged`イベント (で定義されている`GuidesSettingsManager`) とイベントの表示`LayoutChanged`と`Closed`します。

`LayoutChanged`いくつかの種類など、Visual Studio は、ビューを作成するときに、ビュー内の変更のためのイベントが発生します。 `OnViewLayoutChanged`ハンドラー呼び出し`AddGuidelinesToAdornmentLayer`を実行します。 コードでは、`OnViewLayoutChanged`フォント サイズを変更、ビューのとじしろ、水平方向にスクロール、および具合などの変更に基づく行の位置を更新することが必要と判断します。 コードでは、`UpdatePositions`文字またはテキストの行で指定された文字のオフセット内にあるテキストの列の直後後に描画するために、ガイド線をによりします。

設定が変更されるたびに、`SettingsChanged`関数をだけ再作成すべて、`Line`な新しい設定を持つオブジェクト。 行の位置を設定した後、コードを以前のすべて削除`Line`オブジェクトから、 `ColumnGuideAdornment` adornment レイヤー、新しいものを追加します。

## <a name="define-the-commands-menus-and-menu-placements"></a>コマンド、メニューのおよびメニューの配置を定義します。
可能性があります多くのコマンドとメニューを宣言、その他のさまざまなのメニュー コマンドやメニューのグループを配置することとコマンド ハンドラーをフックします。 このチュートリアルの詳細情報が、この拡張機能でのコマンドの機能を強調表示は、「[メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)します。

### <a name="introduction-to-the-code"></a>コードの概要
列ガイド拡張機能が一緒に属しているコマンドのグループを宣言することを示しています (列を追加、列の削除、線の色を変更する)、エディターのコンテキスト メニューのサブメニューでそのグループを配置します。  列ガイド拡張機能は、主に、コマンドを追加するも**編集**メニューが表示しないことにより、非表示として次の一般的なパターンについて説明します。

これには、コマンドの実装に 3 つの部分があります。ColumnGuideCommandsPackage.cs、ColumnGuideCommandsPackage.vsct、および ColumnGuideCommands.cs です。 コマンドによって自動生成、テンプレートによって生成されるコード、**ツール**実装としてダイアログ ボックスが表示されるメニューです。 実装される方法を見て、 *.vsct*と*ColumnGuideCommands.cs*ファイルのため、これは簡単です。 これらのファイルは次のコードを置き換えるとします。

パッケージのコードには、Visual Studio 拡張機能がコマンドを提供することを検出して、コマンドを配置する場所を検索するに必要な定型宣言が含まれています。 パッケージは、初期化時に、コマンドの実装クラスがインスタンス化します。 パッケージに関連するコマンドの詳細については、次を参照してください。[メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)します。

### <a name="a-common-commands-pattern"></a>コマンドの一般的なパターン
列ガイド拡張機能のコマンドは、Visual Studio での非常に一般的なパターンの例です。 グループに関連するコマンドを配置するされをそのグループ メイン メニューで、多くの場合と配置"`<CommandFlag>CommandWellOnly</CommandFlag>`"コマンドを非表示を設定します。  メイン メニューのコマンドを配置すること (など**編集**) ためには便利な名前 (など**Edit.AddColumnGuide**) は再でキー バインドを割り当てるときにコマンドを見つけるに役立ちます**ツールオプション**します。 コマンドを呼び出すときに、入力候補を取得するのに役立ちますも、**コマンド ウィンドウ**します。

コンテキスト メニューにコマンドのグループを追加または sub メニュー コマンドを使用するユーザーを想定している場所。 Visual Studio 扱います`CommandWellOnly`メイン メニューの場合のみ、非表示フラグ。 コンテキスト メニューまたはサブメニューにコマンドの同じグループを配置すると、コマンドが表示されます。

一般的なパターンの一部として、列ガイド拡張機能は、1 つのサブメニューを保持する 2 番目のグループを作成します。 さらに、サブメニューには、4 つの列ガイド コマンドを使用して最初のグループが含まれています。 サブメニューを保持する 2 番目のグループは、再利用可能な資産をさまざまなコンテキスト メニュー上に配置するをこれらのコンテキスト メニューのサブメニューがなさないです。

### <a name="the-vsct-file"></a>.Vsct ファイル
*.Vsct*ファイルは、コマンドと、どこで、アイコンとこれに宣言します。 内容を置き換える、 *.vsct* (下記参照)、次のコード ファイル。

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet" 
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**GUID**します。 コマンド ハンドラーを検索し、呼び出すことに、Visual Studio のパッケージの GUID で宣言されていることを確認する必要があります、 *ColumnGuideCommandsPackage.cs* (プロジェクト項目テンプレートから生成された) ファイルで宣言されている GUID のパッケージに一致 *.vsct*ファイル (上記のコピー) します。 このサンプル コードを再利用する場合は他のユーザーにこのコードをコピーした場合とが競合しないように、別の GUID を行ったことを確認する必要があります。

行を見つけます。 *ColumnGuideCommandsPackage.cs*引用符の間の GUID をコピーします。

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

内の GUID を貼り付けて、 *.vsct*に次の行があるように、ファイル、`Symbols`宣言。

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

コマンドの Guid を設定、ビットマップ イメージ ファイルが一意であるため、拡張機能では、すぎます。

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

ただし、コマンド セットを変更し、ビットマップ イメージの Guid このチュートリアルで動作するコードを取得する必要はありません。 GUID での宣言と一致する必要があるコマンドのセット、 *ColumnGuideCommands.cs*ファイルも、そのファイルの内容に置き換えます。 そのため、Guid が一致します。

内の他の Guid、 *.vsct*ファイルには、列ガイド コマンドを追加する、既存のメニューが識別するため、変更しないでください。

**ファイルのセクションでは**します。 *.Vsct*は外側の 3 つのセクションがあります。 コマンド、配置、およびシンボル。 コマンドのセクションでは、コマンド グループ、メニューのボタンまたはメニュー項目、およびアイコンのビットマップを定義します。 メニュー上の既存のメニューに追加の配置グループはどこに配置されたセクションを宣言します。 Symbols セクションで他の場所で使用される識別子の宣言、 *.vsct*ファイルは、これにより、 *.vsct* Guid と 16 進数よりも読みやすいコード番号のすべての場所。

**コマンドのセクションを定義をグループ化**します。 コマンド セクションでは、最初のコマンド グループを定義します。 コマンドのグループは、若干の灰色の線のグループを分離することでメニューに表示するコマンドです。 グループは、この例のように、全体サブメニューを入力も可能性があり、灰色の線をここで分離することが表示されません。 *.Vsct*ファイルは、2 つのグループを宣言、`GuidesMenuItemsGroup`を親には、 `IDM_VS_MENU_EDIT` (メイン**編集**メニュー)、`GuidesContextMenuGroup`を親には、 `IDM_VS_CTXT_CODEWIN` (コードエディターのコンテキスト メニュー)。

2 番目のグループ宣言には、`0x0600`優先順位。

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

考え方は、列の挿入ガイドを sub メニュー グループを追加する任意のコンテキスト メニューの最後に、サブメニューです。 しかし、よく知っているし、常に最後の優先順位を使用して、あるサブメニューを強制するとは考えないでください`0xFFFF`します。 サブメニューがショートカット メニューを配置する上にある場所を表示する数みたりする場合があります。 この場合、`0x0600`が十分に高いことがわかりますが、そのことが望ましい場合に列ガイドの拡張機能よりも少なくなる、拡張機能を設計する他のユーザー用の領域の外に出て限り、メニューの末尾に配置します。

**コマンドのセクションでは、メニュー定義**します。 次に、サブメニューの定義コマンド セクション`GuidesSubMenu`に親が設定、`GuidesContextMenuGroup`します。 `GuidesContextMenuGroup`はすべての関連するコンテキスト メニューに追加するグループです。 配置セクションでは、コードは、このサブメニューに 4 つの列ガイド コマンドを使用してグループを配置します。

**コマンドのセクションをボタンの定義**します。 コマンドのセクションでは、4 つの列ガイド コマンド ボタン、メニュー項目を定義します。 `CommandWellOnly`、前述のように、コマンドがメイン メニューに配置する場合に表示されないことを意味します。 メニュー項目の 2 つのボタンの宣言 (ガイドを追加および削除のガイド) があることも、`AllowParams`フラグ。

```xml
<CommandFlag>AllowParams</CommandFlag>
```

このフラグにより、と共に、メイン メニューに配置された、コマンドは、Visual Studio は、コマンド ハンドラーを呼び出すときに引数を受け取る必要があります。  ユーザーは、コマンド ウィンドウからコマンドを実行する場合、引数が、イベント引数のコマンド ハンドラーに渡されるが。

**コマンドのセクションでは、ビットマップ定義**します。 最後に、commands セクションでは、ビットマップやコマンドに使用されるアイコンを宣言します。 このセクションでは、プロジェクト リソースを識別し、使用するアイコンの 1 から始まるインデックスを一覧表示する単純な宣言です。 Symbols セクション、 *.vsct*ファイルのインデックスとして使用される識別子の値を宣言します。 このチュートリアルでは、プロジェクトに追加するカスタム コマンドの項目テンプレートで提供されるビットマップ ストリップを使用します。

**配置セクション**します。 コマンドの後のセクションは、配置セクションです。 1 つは、場所、コードを追加する前に説明した最初のグループを保持する 4 つの列ガイド サブメニューにコマンド コマンドが表示されます。

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

その他の配置のすべてを追加、 `GuidesContextMenuGroup` (が含まれています、 `GuidesSubMenu`) 他のエディターのコンテキスト メニューにします。 コードが宣言されている場合、 `GuidesContextMenuGroup`、親がコード エディターのコンテキスト メニューに設定します。 理由コード エディターのコンテキスト メニューの配置が表示されません。

**セクションのシンボル**します。 前述のように、symbols セクションがで他の場所で使用される識別子を宣言、 *.vsct*これにより、ファイル、 *.vsct* Guid と 16 進数よりも読みやすいコード番号のすべての場所。 このセクションでは、重要な点は、パッケージの GUID がパッケージ クラスで宣言同意する必要があります。 また、コマンド セットの GUID は、コマンドの実装クラスで宣言と一致する必要があります。

## <a name="implement-the-commands"></a>コマンドを実装します。
*ColumnGuideCommands.cs*ファイルは、コマンドを実装して、ハンドラーをフックします。 Visual Studio では、パッケージを読み込みし、初期化、パッケージを呼び出して`Initialize`コマンドの実装クラス。 コマンドの初期化は単に、クラスをインスタンス化し、コンス トラクターは、すべてのコマンド ハンドラーをフックします。

内容を置き換える、 *ColumnGuideCommands.cs* (下記参照)、次のコード ファイル。

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet = 
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor = 
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**参照の修正**します。 この時点での参照をありませんしています。 ソリューション エクスプ ローラーで [参照] ノードで、右ポインター ボタンを押します。 選択、**を追加しています.** コマンド。 **参照の追加**ダイアログに、右上隅にある検索ボックスがあります。 (二重引用符) を含まない「エディター」を入力します。 選択、 **Microsoft.VisualStudio.Editor** (する必要があります、チェック ボックスをオン、しない選択された項目の左側に、項目) 項目を選択して **[ok]** 参照を追加します。

**初期化**します。  パッケージ クラスが初期化されるときに呼び出す`Initialize`コマンド実装クラス。 `ColumnGuideCommands`初期化はクラスをインスタンス化し、クラス メンバーに、クラスのインスタンスと、パッケージ参照を保存します。

クラス コンス トラクターから、コマンド ハンドラーのフック ups のいずれかを見てみましょう。

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

作成する、`OleMenuCommand`します。 Visual Studio では、Microsoft Office コマンドのシステムを使用します。 キーの引数をインスタンス化するときに、`OleMenuCommand`コマンドを実装する関数は、(`AddColumnGuideExecuted`)、Visual Studio コマンドを使用してメニューを表示するときに呼び出す関数 (`AddColumnGuideBeforeQueryStatus`)、およびコマンド id。 Visual studio では、クエリ ステータス関数を呼び出し、コマンドで、自身で非表示またはメニューの特定のディスプレイの灰色をメニューにコマンドを表示する前に (たとえば、無効にすると**コピー**選択されていない場合)、そのアイコンを変更またはも (たとえば、追加ものから削除するものに)、その名前を変更して、具合です。 コマンド ID がコマンドで宣言されている ID と一致する必要があります、 *.vsct*ファイル。 コマンド セットと列ガイドの文字列の追加コマンド間で一致する必要があります、 *.vsct*ファイルと*ColumnGuideCommands.cs*します。

次の行は、ユーザーが (詳細は後述)、コマンド ウィンドウを使用してコマンドを呼び出すときのアシスタンスを提供します。

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **状態をクエリする**します。 状態のクエリ関数`AddColumnGuideBeforeQueryStatus`と`RemoveColumnGuideBeforeQueryStatus`ガイドや max の列の最大数) などのいくつかの設定を確認または削除する列ガイドがある場合。 コマンドは、条件が適切な場合は、有効にします。  状態のクエリ関数では、メニューの Visual Studio メニューに表示するたびに、コマンドごとに実行されるため、効率を必要があります。

 **AddColumnGuideExecuted 関数**します。 現在のエディターのビューとキャレット位置見極めることのガイドを追加の興味深い部分です。  最初に、この関数を呼び出して`GetApplicableColumn`かどうか、コマンド ハンドラーのイベントの引数であるユーザーが指定した引数とまったくが存在しない場合は、関数のエディターのビューを確認します。

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` 取得する、もう少し詳しく説明する必要があります、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>コードのビュー。  トレースする場合`GetActiveTextView`、 `GetActiveView`、および`GetTextViewFromVsTextView`、その方法を確認できます。 次のコードは、抽象化すると、関連するコード以降では、現在の選択、選択範囲のフレームを取得し、フレームの DocView として取得する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>、取得し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> IVsTextView からビューのホストを取得し、最後に、IWpfTextView:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection)) 
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

を作成した後、IWpfTextView キャレットが置かれている列を取得できます。

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

現在の列を持つ一方でユーザーがクリックした場合、コード呼び出すだけです、列を追加または削除設定マネージャーの。 設定マネージャーは、すべてのイベントを発生させます。`ColumnGuideAdornment`オブジェクトをリッスンします。 イベントが発生したとき、これらのオブジェクトは、新しい列ガイドの設定で、関連付けられているテキスト ビューを更新します。

## <a name="invoke-command-from-the-command-window"></a>コマンド ウィンドウからコマンドを呼び出す
列ガイドのサンプルでは、機能拡張の形式として、コマンド ウィンドウから 2 つのコマンドを呼び出すことができます。 使用する場合、**ビュー&#124;その他の Windows&#124;コマンド ウィンドウ**コマンド、コマンド ウィンドウに表示することができます。 コマンド ウィンドウを対話するには、「編集」を入力して、コマンド名の補完と 120 引数を指定して、次の結果がある場合。

```csharp
> Edit.AddColumnGuide 120
>
```

この動作を有効にするサンプルの部分は、 *.vsct*宣言、ファイル、`ColumnGuideCommands`コマンド ハンドラー、およびイベントの引数をチェックするコマンド ハンドラーの実装をフックし、ときに、クラス コンス トラクター。

見た"`<CommandFlag>CommandWellOnly</CommandFlag>`"で、 *.vsct*ファイルへの配置と、**編集**メイン メニューにコマンドが表示されていない場合でも、**編集**UI メニュー。 メイン**編集** メニューからそれらのような名前**Edit.AddColumnGuide**します。 4 つのコマンドを保持するコマンドのグループ宣言に、グループの配置、**編集**直接 メニュー。

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

ボタン セクションには、コマンドは、後で宣言されている`CommandWellOnly`メイン メニューに表示されないようにするために使用して宣言されていると`AllowParams`:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

コマンド ハンドラーをフックするコードを見た、`ColumnGuideCommands`クラスのコンス トラクターが許可されているパラメーターの説明を入力します。

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

見た、`GetApplicableColumn`チェック関数`OleMenuCmdEventArgs`エディターのビューの現在の列を確認する前に、値。

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>拡張機能をお試しください。
これでキーを押して**F5**列ガイド拡張機能を実行します。 テキスト ファイルを開き、エディターのコンテキスト メニューを使用して、ガイド線を追加、削除、色を変更します。 テキストをクリックして (空白文字以外は、行の末尾を越えた) 列を追加するガイド、またはエディターに追加の行の最後の列。 コマンド ウィンドウを使用して引数を指定してコマンドを呼び出す場合は、列ガイドを任意の場所を追加できます。

さまざまなコマンドの配置を再試行してください、名前変更、アイコン、および、変更するメニューで、最新のコードを示す Visual Studio での問題がある場合は、デバッグしている実験用ハイブをリセットできます。 起動、 **Windows [スタート] メニュー** 「リセット」を入力します。 検索し、コマンドを実行して **[次へ] Visual Studio の実験用インスタンスをリセット**します。 このコマンドは、すべての拡張機能コンポーネントの実験用のレジストリ ハイブをクリーンアップします。 そうでないコンポーネントからの設定をクリーンアップため Visual Studio の実験用ハイブをシャット ダウンするときに行われていれば任意のガイドは引き続き行われます、コードは、次回の起動時に、設定ストアを読み取るとき。

## <a name="finished-code-project"></a>完成したコード プロジェクト
Visual Studio 機能拡張のサンプルの GitHub プロジェクトはまもなくし、完成したプロジェクトがあります。 この記事では、次のようが発生するとが更新されます。 完全なサンプル プロジェクトでは、異なる guid があり、コマンドのアイコンの異なるビットマップ ストリップになります。

この Visual Studio ギャラリーで列ガイド機能のバージョンを試すことができます[拡張子](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)します。

## <a name="see-also"></a>関連項目
[エディター内で](../extensibility/inside-the-editor.md)
[エディターと言語サービス拡張](../extensibility/extending-the-editor-and-language-services.md) 
[言語サービスとエディターの拡張機能ポイント](../extensibility/language-service-and-editor-extension-points.md) 
 [メニューとコマンドの拡張](../extensibility/extending-menus-and-commands.md)
[メニューにサブメニューを追加する](../extensibility/adding-a-submenu-to-a-menu.md)
[とエディターの項目テンプレートの拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)
