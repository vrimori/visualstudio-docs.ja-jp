---
title: "ビューの表示要素、コマンドおよび設定を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: f37f2f8243a49f4f85b0f4177f2f33a7a724f08b
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>チュートリアル: ビューの表示要素、コマンド、および設定 (列ガイド) を作成します。
コマンドとエフェクトの表示と、Visual Studio のテキスト/コード エディターを拡張することができます。  このトピックでは、人気のある拡張機能、段組ガイドを使用する方法を示します。  列ガイドでは、特定の列の幅をコードを管理するためのテキスト エディターのビューに描画される視覚的にライトの線です。  具体的には書式設定されたコードは、ドキュメント、ブログの投稿に含めるか、バグのレポートのサンプルについては重要でもあります。  
  
 このチュートリアルでは、次を行います。  
  
-   VSIX プロジェクトを作成します。  
  
-   エディターのビューの表示要素を追加します。  
  
-   保存と設定を取得する場所への (描画列ガイドおよびの色) のサポートを追加します。  
  
-   コマンドを追加 (列ガイドの追加と削除、その色を変更する)  
  
-   [編集] メニューとテキスト ドキュメントのコンテキスト メニューのコマンドを追加します。  
  
-   Visual Studio コマンド ウィンドウからコマンドを呼び出すためのサポートを追加します。  
  
 この Visual Studio ギャラリーで列のガイド機能のバージョンを試すことができます[拡張子](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)します。  
  
 **注**: このチュートリアルでは、多くのコードに貼り付ける visual studio 拡張機能のテンプレートによって生成されたいくつかのファイルが、すぐにこのチュートリアルではその他の拡張機能の例と github の完成したソリューションを参照します。  完成したコードは、generictemplate アイコンを使用する代わりに実際のコマンドのアイコンがある点で少し異なります。  
  
## <a name="getting-started"></a>作業の開始  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="setting-up-the-solution"></a>ソリューションのセットアップ  
 最初を VSIX プロジェクトを作成、エディター ビュー表示要素を追加して (のコマンドは、自分が所有する VSPackage を追加) コマンドを追加します。  基本的なアーキテクチャは、次のとおりです。  
  
-   テキスト ビュー作成リスナーを作成する必要がある、`ColumnGuideAdornment`各ビューのオブジェクト。  このオブジェクトがビューの変更に関するイベントをリッスンしたり、必要に応じて、設定の変更、列の更新または再描画案内します。  
  
-   `GuidesSettingsManager` Visual Studio の設定ストレージからの読み書きを処理します。  設定マネージャーにも、ユーザーのコマンドをサポートしている設定を更新するための操作 (列を追加、列の削除、色を変更する)。  
  
-   ユーザー コマンドがある場合は、必要である VSIP パッケージがあるが、コマンドの実装オブジェクトを初期化する定型コードのみです。  
  
-   `ColumnGuideCommands` .Vsct ファイルで宣言されているユーザーのコマンドを実装して、コマンドに対するコマンド ハンドラーをフックするオブジェクト。  
  
 **VSIX**します。  使用する**ファイル |新機能。。。** プロジェクトを作成するコマンドです。  左側のナビゲーション ウィンドウで [c# 機能拡張] ノードを選択して、 **VSIX プロジェクト**右側のウィンドウでします。  ColumnGuides の名前を入力して、 **OK**プロジェクトを作成します。  
  
 **装飾の表示**します。  ソリューション エクスプ ローラーでプロジェクト ノードを右のポインター ボタンを押します。  選択、**追加 |新しい項目.** 新しいビューの表示要素項目を追加するコマンドです。  選択**拡張 |エディター**左側のナビゲーション ウィンドウで選択および**エディターのビューポートの表示要素**右側のウィンドウでします。  項目の名前として「name ColumnGuideAdornment とを**追加**に追加します。  
  
 この項目テンプレート プロジェクト (だけでなく参照となど) に&2; つのファイルを追加するを参照してください: ColumnGuideAdornment.cs と ColumnGuideAdornmentTextViewCreationListener.cs です。  テンプレートは、ビューにだけ紫色の四角形を描画します。  以下をいくつかのビューの作成リスナー内の行の変更され、ColumnGuideAdornment.cs の内容に置き換えます。  
  
 **コマンド**します。  ソリューション エクスプ ローラーでプロジェクト ノードを右のポインター ボタンを押します。  選択、**追加 |新しい項目.** 新しいビューの表示要素項目を追加するコマンドです。  選択**拡張 |VSPackage**左側のナビゲーション ウィンドウで選択および**にカスタム コマンド**右側のウィンドウでします。  項目の名前として「name ColumnGuideCommands とを**追加**に追加します。  ColumnGuideCommands.cs、ColumnGuideCommandsPackage.cs、および ColumnGuideCommandsPackage.vsct、だけでなく、複数の参照は追加コマンドおよびパッケージの追加されます。  以下を定義し、コマンドの実装の最初と最後のファイルの内容が置き換わります。  
  
## <a name="setting-up-the-text-view-creation-listener"></a>テキスト ビューの作成のリスナーを設定します。  
 ColumnGuideAdornmentTextViewCreationListener.cs をエディターで開きます。  このコードは、for Visual Studio でのテキスト ビューを作成するときに、ハンドラーを実装します。  ビューの特徴に応じて、ハンドラーが呼び出されるタイミングを制御する属性があります。  
  
 コードは、adornment レイヤーも宣言する必要があります。  更新すると、エディターのビュー、そのビューの表示要素のレイヤーを取得しから表示要素の要素を取得します。  属性を持つ他と比較した、レイヤーの順序を宣言することができます。  次の行を置き換えます。  
  
```c#  
[Order(After = PredefinedAdornmentLayers.Caret)]  
```  
  
 次の&2; 行。  
  
```c#  
[Order(Before = PredefinedAdornmentLayers.Text)]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
```  
  
 交換した行は adornment 層を宣言する属性のグループです。   列ガイド線が表示される場所の変更のみを変更した最初の行。  線の描画「前」をビュー内のテキストは、の背後にある、またはテキストの下に表示されることを意味に、します。  2 行目では、列ガイドの表示要素は、概念のドキュメントに合わせてテキスト エンティティに適用されますが、編集可能なテキストにのみ動作するなど、表示要素を宣言できますを宣言します。  詳細については[言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)  
  
## <a name="implementing-the-settings-manager"></a>設定マネージャーの実装  
 次のコード (下記参照)、GuidesSettingsManager.cs の内容に置き換えます。  
  
```c#  
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
  
 このコードのほとんどはだけを作成し、設定の形式の解析:"RGB (\<int >、\<int >、\<int >) \<int >、 \<int >,..."です。  最後に整数は、段組ガイドとなる&1; から始まる列です。  列ガイド拡張機能では、1 つの設定値の文字列内のすべての設定をキャプチャします。  
  
 注目すべきコードの一部があります。  次のコード行では、設定の保存用 Visual Studio のマネージ ラッパーを取得します。  ほとんどの場合、Windows レジストリにこれを抽象化が、この API は、ストレージ メカニズムに依存しません。  
  
```c#  
internal static SettingsManager VsManagedSettingsManager =  
    new ShellSettingsManager(ServiceProvider.GlobalProvider);  
```  
  
 Visual Studio の設定の保存は、すべての設定を一意に識別するために、カテゴリ識別子と設定の識別子を使用します。  
  
```c#  
private const string _collectionSettingsName = "Text Editor";  
private const string _settingName = "Guides";  
```  
  
 使用する必要はありません`“Text Editor”`カテゴリ名、およびするを選択できますでもかまいません。  
  
 最初のいくつかの関数とは、設定を変更するエントリ ポイントです。  許可されたガイドの最大数のような高度な制約を確認します。  呼び出すことが、`WriteSettings`設定文字列を作成し、プロパティを設定する`GuideLinesConfiguration`です。  Visual Studio 設定ストアと起動に設定値を保存するこのプロパティを設定、`SettingsChanged`をすべて更新するイベント、`ColumnGuideAdornment`テキスト ビューに関連付けられている各オブジェクトです。  
  
 など、いくつかのエントリ ポイント関数がある`CanAddGuideline`設定を変更するコマンドを実装するために使用されます。  Visual Studio には、メニューが表示されている場合は、かどうかのコマンドは、有効では、名前とは何を表示するコマンドの実装などを照会します。次のコマンドの実装に対してこれらのエントリ ポイントをフックする方法が表示されます。  参照してください[拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)コマンドの詳細についてです。  
  
## <a name="implementing-the-columnguideadornment-class"></a>ColumnGuideAdornment クラスを実装します。  
 `ColumnGuideAdornment`修飾ことのあるテキスト ビューごとにクラスをインスタンス化します。  このクラスは、ビューの変更に関するイベントをリッスンしたり、必要に応じて、設定の変更、列の更新または再描画案内します。  
  
 次のコード (下記参照)、ColumnGuideAdornment.cs の内容に置き換えます。  
  
```c#  
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
  
 このクラスのインスタンスを関連付けられている保持<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>と一連の`Line`ビューに描画されるオブジェクト</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。  
  
 コンス トラクター (から呼び出される`ColumnGuideAdornmentTextViewCreationListener`Visual Studio が新しいビューを作成すると) 列ガイドを作成`Line`オブジェクトです。  コンス トラクターものハンドラーを追加、`SettingsChanged`イベント (で定義されている`GuidesSettingsManager`) とイベントの表示`LayoutChanged`と`Closed`です。  
  
 `LayoutChanged`いくつかの種類の Visual Studio は、ビューを作成するときを含め、ビュー内で変更のためのイベントが発生します。  `OnViewLayoutChanged`ハンドラー呼び出し`AddGuidelinesToAdornmentLayer`を実行します。  内のコード`OnViewLayoutChanged`フォント サイズを変更、ビューのとじしろ、水平方向にスクロールなどのなどの変更に基づく行位置を更新することが必要と判断します。  内のコード`UpdatePositions`文字または行のテキスト内の指定した文字オフセットに含まれるテキストの列の直後に描画するガイドラインが発生します。  
  
 設定を変更するたびに、`SettingsChanged`関数だけ再作成すべて、`Line`はどのような新しい設定を持つオブジェクト。  行の位置を設定した後、コードを以前のすべて削除`Line`オブジェクトから、 `ColumnGuideAdornment` adornment レイヤーし、新しいファイルを追加します。  
  
## <a name="defining-the-commands-menus-and-menu-placements"></a>コマンド、メニューのおよびメニューの配置を定義します。  
 場合も多くコマンドおよびメニューを宣言すること、その他の各種のメニュー コマンドやメニューのグループを配置すること、およびコマンド ハンドラーをフックします。  このチュートリアルより深いについてですが、この拡張機能でのコマンドの機能が強調表示は、「[拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)します。  
  
### <a name="introduction-to-the-code"></a>コードの概要  
 列ガイド拡張機能が&1; つのコマンドのグループを宣言することを示しています (列を追加、列の削除、線の色を変更) し、エディターのコンテキスト メニューのサブメニューにそのグループを配置します。  列ガイド拡張機能は、コマンドをメインも追加**編集**メニューが遅れること、非表示として次の一般的なパターンについて説明します。  
  
 コマンドの実装は次の&3; つの部分で構成されます: ColumnGuideCommandsPackage.cs、ColumnGuideCommandsPackage.vsct、および ColumnGuideCommands.cs です。  テンプレートによって生成されたコードでは、コマンドに、**ツール**実装とダイアログ ボックスが表示されるメニューです。  どのようにするためには実装 .vsct と ColumnGuideCommands.cs ファイルはかなり単純です確認することができます。  これらのファイルは次のコードが置き換えられます。  
  
 パッケージのコードは、Visual Studio では、拡張機能によりコマンドとコマンドを配置する場所を検出するために必要な定型宣言です。  パッケージは、初期化時に、コマンドの実装クラスがインスタンス化します。  コマンドの詳細については、パッケージ コマンドに関連するリンクを参照してください。  
  
### <a name="a-common-commands-pattern"></a>コマンドの一般的なパターン  
 列ガイド拡張機能のコマンドは、Visual Studio での非常に一般的なパターンの例です。  グループに関連するコマンドを入力し、そのグループに置きますメイン メニューでは、多くの場合と"`<CommandFlag>CommandWellOnly</CommandFlag>`"コマンドを非表示にする に設定します。  メイン メニューのコマンドを配置すること (など**編集**) この方法によって、優れた名前 (など**Edit.AddColumnGuide**) のショートカット キーの再割り当てするときにコマンドを検索するために便利である**ツール オプション**およびからコマンドを呼び出すときに、入力候補を取得するため、**コマンド ウィンドウ**です。  
  
 コンテキスト メニューにコマンドのグループを追加またはサブ メニュー コマンドを使用するユーザーを想定します。  Visual Studio 取り扱う`CommandWellOnly`メイン メニューの場合のみ、非表示フラグ。  コンテキスト メニューやサブメニューに同じグループのコマンドを配置するコマンドが表示されます。  
  
 一般的なパターンの一部として、段組ガイド拡張機能は&1; つのサブメニューを保持する&2; 番目のグループを作成します。  さらに、サブメニューには、4 つの列ガイド コマンドを使用して最初のグループが含まれています。  サブメニューを保持する&2; 番目のグループは、再利用可能な資産さまざまなコンテキスト メニューに配置されたコンテキスト メニューのサブメニューをかけるです。  
  
### <a name="the-vsct-file"></a>.Vsct ファイル  
 .Vsct ファイルは、コマンドと、どこで、アイコンと共になどを宣言します。  .Vsct ファイルの内容を次のコード (下記参照) に置き換えます。  
  
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
  
 **GUID**します。  コマンド ハンドラーを検索し、呼び出すことを Visual Studio は、GUID は、(プロジェクト項目テンプレートから生成された) ColumnGuideCommandsPackage.cs ファイルで宣言されているパッケージには、GUID は、(上記のコピー) .vsct ファイルで宣言されているパッケージと一致することを確認する必要があります。  このサンプル コードを再利用する場合は他のユーザーにこのコードをコピーした場合と競合しないように、異なる GUID があることを確認する必要があります。  
  
 ColumnGuideCommandsPackage.cs で次の行を見つけ、引用符の間から GUID をコピーします。  
  
```c#  
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";  
```  
  
 次の行があるように .vsct ファイルの GUID を貼り付け、`Symbols`宣言します。  
  
```xml  
<GuidSymbol name="guidColumnGuideCommandsPkg"   
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />  
```  
  
 コマンドの Guid を設定し、ビットマップ イメージ ファイルは一意である、拡張機能にもします。  
  
```xml  
<GuidSymbol name="guidColumnGuidesCommandSet"   
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">  
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">  
```  
  
 ただし、コマンド セットを変更し、ビットマップのイメージの Guid このチュートリアルで動作するコードを取得する必要はありません。  コマンドは、設定 ColumnGuideCommands.cs ファイル内の宣言と一致する GUID の必要がありますが、です。 そのファイルの内容を置き換えられますそのため、Guid が一致します。  
  
 .Vsct ファイル内の他の Guid を変更しないように列ガイド コマンドを追加する、既存のメニューを特定します。  
  
 **ファイルのセクションでは**です。  .Vsct が&3; つのセクションでは外部: コマンド、配置、およびシンボルです。  コマンドでは、コマンド グループをメニューのボタンやメニュー項目、およびアイコンのビットマップを定義します。  配置のセクションでは、メニューまたは既存のメニューに追加の配置をどこでグループを宣言します。  Symbols セクションでは、見やすく .vsct コードの Guid と&16; 進数のすべての場所でない場合に比べて .vsct ファイルで別の場所で使用される識別子を宣言します。  
  
 **セクションのコマンドについては、グループ定義**します。  コマンドのセクションは、最初のコマンド グループを定義します。  コマンドのグループは、グループを区切るわずかの灰色の線でメニューに表示されるコマンドです。  グループは、この例のように、全体の sub メニューを入力も可能性があり、灰色の線をここで分離することが表示されないします。  .Vsct ファイルは、2 つのグループを宣言して、`GuidesMenuItemsGroup`親になれること、 `IDM_VS_MENU_EDIT` (メイン**編集**メニュー) と`GuidesContextMenuGroup`親になれること、 `IDM_VS_CTXT_CODEWIN` (コード エディターのコンテキスト メニュー)。  
  
 2 番目のグループの宣言は、`0x0600`優先順位。  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"   
             priority="0x0600">  
```  
  
 考え方としては、列の挿入ガイドを sub] メニューの [グループのショートカット メニューの追加の end sub メニュー。  ただし、考えないでのメリットについてし、強制的に常に最後の優先順位を使用して、サブメニュー`0xFFFF`します。  どこ sub メニューに配置するコンテキスト メニューにあるを表示するには、この数に対処する必要があります。  ここで`0x0600`は十分なサイズがわかりますが、それが望ましい場合に、列ガイド拡張機能よりも減少する、拡張機能を設計する別のユーザー用の領域は確保できるだけ遠くまでは、メニューの末尾に配置します。  
  
 **コマンドのセクションでは、メニュー定義**します。  次に、サブメニューの定義 command セクション`GuidesSubMenu`に親が設定、`GuidesContextMenuGroup`です。  `GuidesContextMenuGroup`グループのすべての関連するコンテキスト メニューに追加します。  配置のセクションでは、コードは、このサブ メニューの&4; つの列ガイド コマンドを使用してグループを配置します。  
  
 **セクションのコマンドについては、ボタンの定義**します。  ボタンがあります。&4; つの列ガイド コマンドまたはコマンド セクションは、メニュー項目を定義します。  `CommandWellOnly`、上で説明した、コマンドがメイン メニューに配置した場合に表示されないことを意味します。  宣言をボタンのメニュー項目の&2; つ (ガイドを追加およびガイドを削除する) 必要も、`AllowParams`フラグ。  
  
```xml  
<CommandFlag>AllowParams</CommandFlag>  
```  
  
 このフラグによりに持つメイン メニューに配置された、Visual Studio は、コマンド ハンドラーを呼び出すとき、引数を受け取るコマンドを使用できます。  場合は、ユーザーは、コマンド ウィンドウからコマンドを呼び出します引数が、イベント引数のコマンド ハンドラーに渡されるを取得します。  
  
 **コマンドのセクションでは、ビットマップ定義**します。  最後にコマンドのセクションでは、コマンドは、使用されるアイコン、ビットマップを宣言します。  これは、単純な宣言をプロジェクトのリソースを識別し、使用するアイコンの&1; から始まるインデックスを一覧表示します。  .Vsct ファイルの symbols セクションでは、インデックスとして使用される識別子の値を宣言します。  このチュートリアルでは、プロジェクトに追加されたカスタム コマンド項目テンプレートで提供されるビットマップ ストリップを使用します。  
  
 **配置セクション**です。  コマンドの後は、セクションは、配置のセクションを示します。  1 つは、ここで、コードを追加する前に説明した最初のグループを保持して、4 つの列ガイド sub メニューにコマンド コマンドが表示されます。  
  
```xml  
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"   
                  priority="0x0100">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />  
</CommandPlacement>  
```  
  
 その他の配置のすべての追加、 `GuidesContextMenuGroup` (を含む、 `GuidesSubMenu`) 他のエディター コンテキスト メニューにします。  コード宣言されている場合、 `GuidesContextMenuGroup`、し、コード エディターのコンテキスト メニューを親でした。  コード エディターのコンテキスト メニューの配置が表示されないためにです。  
  
 **記号は、セクション**です。  前述のように、シンボルのセクションでは、見やすく .vsct コードの Guid と&16; 進数のすべての場所でない場合に比べて .vsct ファイルで別の場所で使用される識別子を宣言します。  ここで重要な点は、パッケージの GUID が、パッケージのクラスと、コマンド セットで、宣言の GUID が、コマンドの実装クラスの宣言と一致する必要があります同意する必要があります。  
  
## <a name="implementing-the-commands"></a>コマンドの実装  
 ColumnGuideCommands.cs ファイルは、コマンドを実装し、ハンドラーをフックします。  Visual Studio では、パッケージを読み込みますして初期化し、ときに、パッケージを呼び出して`Initialize`コマンドの実装クラスにします。  コマンドの初期化は単に、クラスをインスタンス化し、コンス トラクターは、すべてのコマンド ハンドラーをフックします。  
  
 ColumnGuideCommands.cs ファイルの内容を次のコード (下記参照) に置き換えます。  
  
```c#  
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
  
 **参照を修正**します。  この時点での参照をありませんが。  ソリューション エクスプ ローラーで [参照] ノードの右のポインター ボタンを押します。  選択、**を追加しています.** コマンドです。  **参照の追加**ダイアログに、右上隅の [検索] ボックスがあります。  「エディター」(引用符なしで二重) を入力します。  選択、 **Microsoft.VisualStudio.Editor**項目 (必要がありますアイテムをチェックする項目を選択すれば済むの左側のボックス) を選択し、 **OK**参照を追加します。  
  
 **初期化**します。  パッケージ クラスが初期化されるときに呼び出す`Initialize`コマンドの実装クラスにします。  `ColumnGuideCommands`初期化は、クラスをインスタンス化し、クラスのインスタンスおよびパッケージの参照クラスのメンバーに保存します。  
  
 クラスのコンス トラクターから、コマンド ハンドラーのフック ups のいずれかを見てみましょう。  
  
```c#  
_addGuidelineCommand =   
    new OleMenuCommand(AddColumnGuideExecuted, null,  
                       AddColumnGuideBeforeQueryStatus,  
                       new CommandID(ColumnGuideCommands.CommandSet,  
                                     cmdidAddColumnGuide));  
  
```  
  
 作成する、`OleMenuCommand`です。  Visual Studio では、Microsoft Office コマンドのシステムで使用します。  コマンドを実装する関数には、OleMenuCommand をインスタンス化するときに、キーの引数 (`AddColumnGuideExecuted`)、Visual Studio コマンドを使用してメニューを表示するときに呼び出す関数 (`AddColumnGuideBeforeQueryStatus`)、およびコマンド id。  Visual studio では、クエリの状態関数を呼び出すコマンドは、非表示またはメニューの特定のディスプレイされなかったり薄くし自体ができるように、メニューのコマンドを表示する前に (たとえば、無効にすると**コピー**が選択されていない場合) のアイコンを変更またはも (たとえばから追加しておきたいものを削除)、その名前を変更に表示され、します。  コマンド ID は、.vsct ファイルで宣言されたコマンド ID と一致する必要があります。  コマンドの文字列を設定し、列ガイドは、コマンドが .vsct ファイルと、ColumnGuideCommands.cs 間で一致する必要がありますを追加します。  
  
 次の行はユーザーが (下記参照)、コマンド ウィンドウを使用してコマンドを起動した場合のサポートが提供します。  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
```  
  
 **状態を問い合わせる**します。  状態のクエリ機能`AddColumnGuideBeforeQueryStatus`と`RemoveColumnGuideBeforeQueryStatus`(ガイドまたは最大の列の最大数) などのいくつかの設定を確認または削除する列ガイドがある場合。  条件が適切である場合、コマンドが有効にします。  状態のクエリ関数では、Visual Studio メニューでコマンドごとに、メニューに表示するたびに実行されるため非常に効率的である必要があります。  
  
 **AddColumnGuideExecuted 関数**します。  追加的なガイドの興味深い部分は、現在のエディターのビューおよびキャレット位置を考えることです。  最初にこの関数を呼び出した`GetApplicableColumn`かどうかは、コマンド ハンドラーのイベントの引数であるユーザーが指定した引数がない場合し、関数は、チェックとエディターのビューを確認します。  
  
```c#  
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
  
 `GetCurrentEditorColumn`少し詳細に分析が、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>コードのビュー</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> 。  トレースする場合`GetActiveTextView`、 `GetActiveView`、および`GetTextViewFromVsTextView`を実行する方法を確認できます。  次は、抽象化すると、関連するコード以降では、現在の選択、選択範囲のフレームを取得し、フレームの DocView としてを取得する、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>、取得してから、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>、IVsTextView から取得してからホストを表示し、最後にれた:</xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
```c#  
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
  
 れたをした後、カーソルが置かれている列を取得できます。  
  
```c#  
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
  
 現在の列に取り掛かる、ユーザーがクリックすると、ここで、コードだけでを呼び出します設定マネージャーを追加または列を削除します。  設定マネージャーがすべてにイベントを発生させる`ColumnGuideAdornment`オブジェクトをリッスンします。  イベントが発生したとき、これらのオブジェクトは、列ガイドは新しい設定でそれに関連付けられたテキスト ビューを更新します。  
  
## <a name="invoking-command-from-the-command-window"></a>コマンド ウィンドウから起動コマンド  
 列ガイドの例では、形式の拡張としてコマンド ウィンドウから次の&2; つのコマンドを呼び出すことができます。  使用する場合、**表示 |その他の Windows |コマンド ウィンドウ**コマンドをコマンド ウィンドウを確認できます。  コマンド ウィンドウをやりとりするには、「編集」を入力して、コマンド名の補完機能と 120 の引数を指定することにより、次があります。  
  
```  
> Edit.AddColumnGuide 120  
>  
```  
  
 .Vsct ファイル宣言内でこのは有効にするサンプルの部分、`ColumnGuideCommands`クラスのコンス トラクターとコマンド ハンドラー、およびイベントの引数をチェックするコマンド ハンドラーの実装をフックしています。  
  
 確認した"`<CommandFlag>CommandWellOnly</CommandFlag>`".vsct ファイルと編集のメイン メニューに配置された場合でも表示しないコマンドでは、**編集**メニュー UI です。  ような名前によって、メインの編集 メニューに**Edit.AddColumnGuide**します。  コマンドは、4 つのコマンドのグループから [編集] メニューの直接配置を保持する宣言をグループ化します。  
  
```xml  
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"  
             priority="0xB801">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />  
      </Group>  
  
```  
  
 ボタン セクションには、コマンドは、後で宣言されている`CommandWellOnly`メイン メニューで非表示にして、これらを宣言`AllowParams`:  
  
```xml  
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"   
        priority="0x0100" type="Button">  
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />  
  <Icon guid="guidImages" id="bmpPicAddGuide" />  
  <CommandFlag>CommandWellOnly</CommandFlag>  
  <CommandFlag>AllowParams</CommandFlag>  
  
```  
  
 内のコードをフックするコマンド ハンドラーを確認した、`ColumnGuideCommands`クラスのコンス トラクターは、使用可能なパラメーターの説明を入力します。  
  
```c#  
_addGuidelineCommand.ParametersDescription = "<column>";  
  
```  
  
 確認した、`GetApplicableColumn`機能チェック`OleMenuCmdEventArgs`の現在の列のエディターのビューをチェックする前に値。  
  
```c#  
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
  
## <a name="trying-your-extension"></a>拡張機能をしようとしています。  
 ここで押す**f5 キーを押して**列ガイド拡張機能を実行します。  テキスト ファイルを開き、エディターのコンテキスト メニューを使用して、ガイド線を追加、削除を行ったり、および色を変更します。  テキスト内をクリックする必要があります (空白文字以外は、行の末尾を越えた) 列を追加するガイド、または、エディターに追加の行の最後の列です。  コマンド ウィンドウを使用して引数を指定してコマンドを呼び出す場合は、列ガイドを任意の場所を追加できます。  
  
 さまざまなコマンドの配置を実行してください、名前変更、アイコン、およびを変更するメニューに最新のコードを示す Visual Studio で問題がある場合は、デバッグしている実験用ハイブをリセットできます。  表示、 **Windows [スタート] メニュー** 「リセット」を入力します。  確認し、コマンドを呼び出す**次 Visual Studio の実験用インスタンスをリセット**します。  これは、すべての拡張コンポーネントの実験用のレジストリ ハイブをクリーンアップします。  そうでないコンポーネントからの設定をクリーンアップように Visual Studio の実験用ハイブをシャット ダウンするときに設定した任意のガイドは削除されません次回の起動時に、設定ストアを読み取ろうとします。  
  
## <a name="finished-code-project"></a>完成したコード プロジェクト  
 すぐに、Visual Studio 機能拡張のサンプルの github プロジェクトなり、完成したプロジェクトがあります。  このような場合にあるポイントに、このトピックは更新されます。  完成したサンプル プロジェクトでは、異なる guid があります。 され、コマンドのアイコンの異なるビットマップ ストリップがあります。  
  
 この Visual Studio ギャラリーで列のガイド機能のバージョンを試すことができます[拡張子](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home)します。  
  
## <a name="see-also"></a>関連項目  
 [エディター内](../extensibility/inside-the-editor.md)   
 [エディターと言語サービスの拡張](../extensibility/extending-the-editor-and-language-services.md)   
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)   
 [拡張メニューとコマンド](../extensibility/extending-menus-and-commands.md)   
 [メニューのサブメニューの追加](../extensibility/adding-a-submenu-to-a-menu.md)   
 [エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)
