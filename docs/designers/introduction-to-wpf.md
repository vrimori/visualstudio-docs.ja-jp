---
title: "WPF の概要 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 3d56a56e4008cecd9fa506ba76425a75618b6a28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="introduction-to-wpf"></a>WPF の概要
Windows Presentation Foundation (WPF) を使用して、視覚的に美しいユーザー エクスペリエンスを持つ Windows 用のデスクトップ クライアント アプリケーションを作成できます。  
  
 ![Contoso Healthcare UI のサンプル](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")  
  
 WPF の中核を成すのは、解像度に依存しない、ベクター ベースのレンダリング エンジンであり、これは最新のグラフィックス ハードウェアを活用できるように構築されています。 この中核を拡張するため、WPF では、Extensible Application Markup Language (XAML)、コントロール、データ バインディング、レイアウト、2-D および 3-D グラフィックス、アニメーション、スタイル、テンプレート、ドキュメント、メディア、テキスト、タイポグラフィなどの、アプリケーション開発機能の包括的なセットを使用します。 WPF は .NET Framework に含まれるので、.NET Framework クラス ライブラリの他の要素を組み込んだアプリケーションを構築できます。  
  
 この概要は初めての方を対象としており、WPF の主要な機能と概念を説明します。  
  
##  <a name="Programming_with_WPF"></a> WPF によるプログラミング  
 WPF は、ほとんどの部分が <xref:System.Windows> 名前空間に格納されている .NET Framework 型のサブセットとして存在します。 ASP.NET や Windows フォームのようなマネージ テクノロジを使用して .NET Framework で以前にアプリケーションを構築したことがあるユーザーは、基本的な WPF のプログラミングの経験には慣れているはずです。クラスのインスタンス化、プロパティの設定、メソッドの呼び出し、イベントの処理など、すべての操作は C# または Visual Basic などの使い慣れた .NET プログラミング言語を使用して行うことができます。  
  
 WPF には、プロパティとイベントを拡張する追加のプログラミング構成要素である、 [依存関係プロパティ](https://msdn.microsoft.com/en-us/library/ms752914\(v=vs.100\).aspx) と [ルーティング イベント](https://msdn.microsoft.com/en-us/library/ms742806\(v=vs.100\).aspx)が含まれています。  
  
##  <a name="Markup_And_Codebehind"></a> マークアップおよび分離コード  
 WPF では *マークアップ* と *分離コード*の両方を使用したアプリケーションを開発できます。これは ASP.NET 開発者にとってなじみ深いエクスペリエンスに違いありません。 一般に、アプリケーションの外観を実装するには XAML マークアップを使用し、一方、その動作を実装するには、マネージ プログラミング言語 (分離コード) を使用します。 外観と動作の実装を別々に行うことには、次の利点があります。  
  
-   外観固有のマークアップが動作固有のコードと密接に結び付いていないので、開発と保守のコストが削減されます。  
  
-   デザイナーがアプリケーションの外観を実装しているとき同時に、開発者はアプリケーションの動作を実装できるため、開発がより効率的に進みます。  
  
-   WPF アプリケーションの[グローバリゼーションとローカリゼーション](https://msdn.microsoft.com/en-us/library/ms788718\(v=vs.100\).aspx) が簡略化します。  
  
 WPF のマークアップおよび分離コードの簡単な概要を次に示します。  
  
### <a name="markup"></a>マークアップ  
 XAML は、アプリケーションの外観を宣言的に実装するために使用される XML ベースのマークアップ言語です。 一般的に、ウィンドウ、ダイアログ ボックス、ページ、ユーザー コントロールの作成と、これらにコントロール、図形、グラフィックスを入れるために使用されます。  
  
 次の例では XAML を使用して、1 つのボタンが入っているウィンドウの外観を実装しています。  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button">Click Me!</Button>  
  
</Window>  
```  
  
 具体的には、この XAML は `Window` エレメントと `Button` エレメントを使用して、ウィンドウとボタンをそれぞれ定義しています。 各エレメントは属性で構成されます。たとえば `Window` エレメントの `Title` 属性はウィンドウのタイトルバーのテキストを指定します。 マークアップで定義されている要素と属性は、実行時に WPF により、WPF クラスのインスタンスに変換されます。 たとえば、 `Window` エレメントは、 <xref:System.Windows.Window> プロパティが <xref:System.Windows.Window.Title%2A> 属性の値である `Title` クラスのインスタンスに変換されます。  
  
 次の図は、前記の例の XAML で定義されたユーザー インターフェイス (UI) を示しています。  
  
 ![ボタンを含むウィンドウ](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")  
  
 XAML は XML ベースなので、XAML を使用して作成する UI は [要素ツリー](https://msdn.microsoft.com/en-us/library/ms753391\(v=vs.100\).aspx)と呼ばれるネストされた要素の階層で組み立てられます。 要素ツリーは UI を作成し、管理するための論理的かつ直感的な方法を提供します。  
  
### <a name="code-behind"></a>分離コード  
 アプリケーションの主な動作は、ユーザー インタラクションに対して応答する機能を実装することです。これにはイベントの処理 (メニュー、ツールバー、またはボタンをクリックする、など) および応答のビジネス ロジックやデータ アクセス ロジックの呼び出しなどが含まれます。 WPF では、この動作が一般に、マークアップと関連付けられたコードで実装されます。 このタイプのコードは分離コードと呼ばれています。 次の例は、前記の例の更新されたマークアップと分離コードです。  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Class="SDKSample.AWindow"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button" Click="button_Click">Click Me!</Button>  
  
</Window>  
```  
  
```csharp  
using System.Windows; // Window, RoutedEventArgs, MessageBox   
  
namespace SDKSample  
{  
    public partial class AWindow : Window  
    {  
        public AWindow()  
        {  
            // InitializeComponent call is required to merge the UI   
            // that is defined in markup with this class, including    
            // setting properties and registering event handlers  
            InitializeComponent();  
        }  
  
        void button_Click(object sender, RoutedEventArgs e)  
        {  
            // Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!");  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
  
    Partial Public Class AWindow  
        Inherits System.Windows.Window  
  
        Public Sub New()  
  
            ' InitializeComponent call is required to merge the UI   
            ' that is defined in markup with this class, including    
            ' setting properties and registering event handlers  
            InitializeComponent()  
  
        End Sub   
  
        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
  
            ' Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!")  
  
        End Sub   
  
    End Class   
  
End Namespace  
  
```  
  
 この例では、 <xref:System.Windows.Window> クラスから派生したクラスを分離コードが実装しています。 マークアップを分離コード クラスと関連付けるために `x:Class` 属性が使用されます。 分離コード クラスのコンストラクターから `InitializeComponent` が呼び出されて、マークアップで定義された UI を分離コード クラスとマージします。 (`InitializeComponent` は、アプリケーションがビルドされるときに生成されます。手動で実装する必要がないのは、このためです。)`x:Class` と `InitializeComponent` を組み合わせることにより、実装が作成されるときはいつでも必ず正しく初期化されることが保証されます。 分離コード クラスはボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントのイベント ハンドラーも実装します。 ボタンがクリックされると、イベント ハンドラーは <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> メソッドを呼び出して、メッセージ ボックスを表示します。  
  
 次の図は、ボタンがクリックされたときの結果を示しています。  
  
 ![MessageBox](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")  
  
##  <a name="Controls"></a> コントロール  
 アプリケーション モデルにより提供されるユーザー エクスペリエンスは、構築済みのコントロールです。 WPF において、「コントロール」とはウィンドウまたはページによりホストされ、ユーザー インターフェイスを持ち、何らかの動作を実装する WPF クラスのカテゴリに適用される総称です。  
  
 詳しくは、「 [コントロール](/dotnet/framework/wpf/controls/index)」をご覧ください。  
  
### <a name="wpf-controls-by-function"></a>WPF コントロールの機能別一覧  
 組み込まれた WPF コントロールを次に挙げます。  
  
-   **ボタン類**: <xref:System.Windows.Controls.Button> および <xref:System.Windows.Controls.Primitives.RepeatButton>。  
  
-   **データの表示**: <xref:System.Windows.Controls.DataGrid>、 <xref:System.Windows.Controls.ListView>、 <xref:System.Windows.Controls.TreeView>。  
  
-   **日付表示と選択**: <xref:System.Windows.Controls.Calendar> および <xref:System.Windows.Controls.DatePicker>。  
  
-   **ダイアログ ボックス**: <xref:Microsoft.Win32.OpenFileDialog>、 <xref:System.Windows.Controls.PrintDialog>、 <xref:Microsoft.Win32.SaveFileDialog>。  
  
-   **デジタル インク**: <xref:System.Windows.Controls.InkCanvas> および <xref:System.Windows.Controls.InkPresenter>。  
  
-   **ドキュメント**: <xref:System.Windows.Controls.DocumentViewer>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、 <xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentScrollViewer>、 <xref:System.Windows.Controls.StickyNoteControl>。  
  
-   **入力**: <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、 <xref:System.Windows.Controls.PasswordBox>。  
  
-   **レイアウト**: <xref:System.Windows.Controls.Border>、 <xref:System.Windows.Controls.Primitives.BulletDecorator>、 <xref:System.Windows.Controls.Canvas>、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Expander>、 <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.GridView>、 <xref:System.Windows.Controls.GridSplitter>、 <xref:System.Windows.Controls.GroupBox>、 <xref:System.Windows.Controls.Panel>、 <xref:System.Windows.Controls.Primitives.ResizeGrip>、 <xref:System.Windows.Controls.Separator>、 <xref:System.Windows.Controls.Primitives.ScrollBar>、 <xref:System.Windows.Controls.ScrollViewer>、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.Primitives.Thumb>、 <xref:System.Windows.Controls.Viewbox>、 <xref:System.Windows.Controls.VirtualizingStackPanel>、 <xref:System.Windows.Window>、 <xref:System.Windows.Controls.WrapPanel>。  
  
-   **メディア**: <xref:System.Windows.Controls.Image>、 <xref:System.Windows.Controls.MediaElement>、 <xref:System.Windows.Controls.SoundPlayerAction>。  
  
-   **メニュー類**: <xref:System.Windows.Controls.ContextMenu>、 <xref:System.Windows.Controls.Menu>、 <xref:System.Windows.Controls.ToolBar>。  
  
-   **ナビゲーション**: <xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Documents.Hyperlink>、 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.TabControl>。  
  
-   **選択**: <xref:System.Windows.Controls.CheckBox>、 <xref:System.Windows.Controls.ComboBox>、 <xref:System.Windows.Controls.ListBox>、 <xref:System.Windows.Controls.RadioButton>、 <xref:System.Windows.Controls.Slider>。  
  
-   **ユーザー情報**: <xref:System.Windows.Controls.AccessText>、 <xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Primitives.Popup>、 <xref:System.Windows.Controls.ProgressBar>、 <xref:System.Windows.Controls.Primitives.StatusBar>、 <xref:System.Windows.Controls.TextBlock>、 <xref:System.Windows.Controls.ToolTip>。  
  
##  <a name="Input_And_Commanding"></a> 入力とコマンド実行  
 コントロールはほとんどの場合、ユーザー入力の検出と応答に使用されます。 [WPF 入力システム](https://msdn.microsoft.com/en-us/library/ms754010\(v=vs.100\).aspx) では直接イベントとルーティング イベントの両方を使用して、テキスト入力、フォーカス管理、マウス位置指定をサポートしています。  
  
 アプリケーションにはたいてい、複雑な入力要件があります。 WPF には、ユーザー入力動作と、それらの動作に応答するコードを分離する [コマンド システム](https://msdn.microsoft.com/en-us/library/ms752308\(v=vs.100\).aspx) があります。  
  
##  <a name="Layout"></a> レイアウト  
 ユーザー インターフェイスを作成すると、場所とサイズによりコントロール類を配置して、レイアウトを決めます。 すべてのレイアウトの重要な要件は、ウィンドウ サイズと表示設定の変更に適応させることです。 こうした状況でレイアウトを適応させるために開発者にコードを作成させるのではなく、WPF では最上級の拡張可能なレイアウト システムを提供します。  
  
 レイアウト システムの要となるのは、相対的な位置指定です。これにより、ウィンドウや表示条件の変化への適応性が高まります。 さらに、レイアウト システムは各コントロール間のネゴシエーションを管理して、レイアウトを決定します。 このネゴシエーションは 2 段階のプロセスで行われます。まず、コントロールがその親に対して、必要な場所とサイズを伝えます。次に、親コントロールはどれぐらいの空間を持てるかを子コントロールに伝えます。  
  
 レイアウト システムは基本の WPF クラスを介して子コントロールに公開されます。 グリッド、スタック、ドックなどの一般的なレイアウトについて、WPF には複数のレイアウト コントロールが組み込まれています。  
  
-   <xref:System.Windows.Controls.Canvas>: 子コントロールは独自のレイアウトを提供します。  
  
-   <xref:System.Windows.Controls.DockPanel>: 子コントロールはパネルの縁に並べられます。  
  
-   <xref:System.Windows.Controls.Grid>: 子コントロールは行ごと、列ごとに位置指定されます。  
  
-   <xref:System.Windows.Controls.StackPanel>: 子コントロールは垂直方向または水平方向に積み上げられます。  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>: 子コントロールは仮想化され、水平方向または垂直方向の 1 本の線上に配置されます。  
  
-   <xref:System.Windows.Controls.WrapPanel>: 子コントロールは左から右への順序に配置され、現在の行に納まらない場合は、次の行に折り返されます。  
  
 次の例では <xref:System.Windows.Controls.DockPanel> を使用して複数の <xref:System.Windows.Controls.TextBox> コントロールを配置しています。  
  
 [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]  
  
 <xref:System.Windows.Controls.DockPanel> により、子 <xref:System.Windows.Controls.TextBox> コントロールはどのように配置するかを伝えることができます。 このために、 <xref:System.Windows.Controls.DockPanel> は <xref:System.Windows.Controls.DockPanel.Dock%2A> プロパティを実装しています。このプロパティが子コントロールに公開されて、それぞれのコントロールがドック スタイルを指定できるようになります。  
  
> [!NOTE]
>  子コントロールが使うために、親コントロールにより実装されるプロパティは、 [添付プロパティ](https://msdn.microsoft.com/en-us/library/ms749011\(v=vs.100\).aspx)と呼ばれる WPF 構成要素です。  
  
 次の図に、前の例の XAML マークアップの結果を示します。  
  
 ![DockPanel ページ](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")  
  
##  <a name="Data_Binding"></a> データ バインディング  
 ほとんどのアプリケーションは、データの表示と編集の手段をユーザーに提供するために作成されます。 WPF アプリケーションの場合、データ格納とアクセスの機能は、SQL Server や ADO .NET などのテクノロジにより、すでに提供されています。 データがアクセスされ、アプリケーションの管理対象オブジェクトに読み込まれると、WPF アプリケーションの処理が開始します。 基本的に、これには 2 つの処理が伴います。  
  
1.  管理対象のオブジェクトからコントロールにデータをコピーします。これらのコントロールで、データを表示および編集できます。  
  
2.  コントロールを使用してデータに対して行う変更が、必ず管理対象オブジェクトにもう一度コピーされるようにしてください。  
  
 アプリケーションの開発を簡素化するために、WPF にはこれらの手順を自動的に実行する、データ バインディング エンジンが用意されています。 データ バインディング エンジンの中核となる単位は <xref:System.Windows.Data.Binding> クラスであり、その仕事はコントロール (バインディング ターゲット) をデータ オブジェクト (バインディング ソース) にバインドすることです。 この関係を次の図に示します。  
  
 ![基本的なデータ バインディング ダイアグラム](../designers/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 次の例は、<xref:System.Windows.Controls.TextBox> をカスタム `Person` オブジェクトのインスタンスにバインドする方法を示しています。 `Person` の実装を次のコードに示します。  
  
 [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)] [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]  
  
 次のマークアップは <xref:System.Windows.Controls.TextBox> をカスタム `Person` オブジェクトのインスタンスにバインドします。  
  
 [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_3.xaml)]  
[!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_4.xaml)]  
[!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../designers/codesnippet/Xaml/introduction-to-wpf_5.xaml)]  
  
 [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_6.vb)] [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_6.cs)]  
  
 この例で、 `Person` クラスは、分離コードでインスタンス化され、 `DataBindingWindow`のデータ コンテキストとして設定されます。 マークアップでは、 <xref:System.Windows.Controls.TextBox.Text%2A> の <xref:System.Windows.Controls.TextBox> プロパティが、 `Person.Name` プロパティにバインドされます ("`{Binding ... }`" XAML 構文を使用)。 この XAML は WPF に対して、ウィンドウの <xref:System.Windows.Controls.TextBox> プロパティに格納されている `Person` オブジェクトに、 <xref:System.Windows.FrameworkElement.DataContext%2A> コントロールをバインドするよう、指示します。  
  
 WPF データ バインディング エンジンは、検証、並べ替え、フィルター処理、グループ化などのその他のサポートを提供します。 さらにデータ バインディングでは、標準の WPF コントロールによって表示されたユーザー インターフェイスが適切ではない場合に、バインドされたデータを操作するためのカスタム ユーザー インターフェイスをデータ テンプレートで作成することをサポートしています。  
  
 詳しくは、「 [データ バインディングの概要](https://msdn.microsoft.com/en-us/library/ms752347\(v=vs.100\).aspx)」をご覧ください。  
  
##  <a name="Graphics"></a> グラフィックス  
 WPF では次の利点を備えた、広範囲にわたるスケーラブルで柔軟なグラフィックス機能セットが導入されています。  
  
-   **解像度にもデバイスにも依存しないグラフィックス**。 WPF グラフィックス システムでの測定値の基本単位は、デバイスに依存しないピクセル、すなわち 1 インチの 1/96 であり、実際の画面解像度には関係ありません。このため、解像度にもデバイスにも依存しないレンダリングの基盤が提供されます。 デバイスに依存しない各ピクセルは、レンダリングを行うシステムのドット/インチ (dpi) 設定に合うように、自動的にスケーリングされます。  
  
-   **精度の向上**。 WPF の座標系は、単精度ではなく、倍精度浮動小数点数で測定されます。 変換および不透明度の値も倍精度で表現されます。 また、WPF は、広色域 (scRGB) に対応しており、異なる色空間からの入力を管理する統合サポートを提供します。  
  
-   **高度なグラフィックスおよびアニメーションのサポート**。 WPF はアニメーションのシーンを管理してグラフィックスのプログラミングを簡略化します。シーンの処理、レンダリング ループ、バイリニア補間について心配する必要はありません。 WPF はさらに、ヒット テストのサポートとアルファ合成の完全なサポートを提供しています。  
  
-   **ハードウェアの高速化** WPF グラフィックス システムでは、CPU 使用率を最小限に抑えるためにグラフィックス ハードウェアを利用します。  
  
### <a name="2-d-shapes"></a>2-D 図形  
 WPF には、次の図に示す四角形や楕円のような、一般的なベクター描画による 2-D 図形のライブラリが用意されています。  
  
 ![楕円と四角形](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 図形の興味深い機能は、単に表示するだけのものではないところです。図形はコントロールに期待される多くの機能 (キーボード入力とマウス入力を含む) を実装します。 次の例は、<xref:System.Windows.Shapes.Ellipse> の <xref:System.Windows.UIElement.MouseUp> イベント処理を示しています。  
  
 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]  
  
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)] [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]  
  
 次の図では、前のコードによって生成される内容を示しています。  
  
 !["you clicked the ellipse&#33;" というテキストを含むウィンドウ](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 詳しくは、「 [WPF での図形と基本描画の概要](https://msdn.microsoft.com/en-us/library/ms747393\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="2-d-geometries"></a>2-D ジオメトリ  
 WPF で提供される 2-D 図形では、基本的な図形の標準セットが網羅されています。 ただし、カスタマイズされたユーザー インターフェイスを容易に設計するには、カスタム図形を作成しなければならない場合があります。 このため、WPF ではジオメトリが用意されています。 次の図では、直接描画、ブラシとして使用、または他の図形やコントロールをクリップするために使用できるカスタム図形を作成するジオメトリの使用法を示します。  
  
 <xref:System.Windows.Shapes.Path> オブジェクトは、閉じているまたは開いている図形、複数の図形、さらに曲線図形の描画に使用できます。  
  
 <xref:System.Windows.Media.Geometry> オブジェクトは、クリップ、ヒット テスト、2-D グラフィック データのレンダリングに使用できます。  
  
 ![パスのさまざまな使用方法](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 詳しくは、「 [ジオメトリの概要](https://msdn.microsoft.com/en-us/library/ms751808\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="2-d-effects"></a>2-D 効果  
 WPF の 2-D 機能のサブセットには、グラデーション、ビットマップ、描画、ビデオによる塗りつぶし、回転、拡大縮小、傾斜などの視覚効果が含まれています。 これらはすべてブラシによって実現します。次の図に、例をいくつか示します。  
  
 ![さまざまなブラシの図](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 詳しくは、「 [WPF のブラシの概要](https://msdn.microsoft.com/en-us/library/aa970904\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="3-d-rendering"></a>3-D レンダリング  
 WPF には 2-D グラフィックスと統合し、より魅力的で興味深いユーザー インターフェイスを作成できる 3-D レンダリング機能も含まれています。 たとえば、次の図では 3-D 図形上にレンダリングされる 2-D イメージを示しています。  
  
 ![Visual3D サンプルのスクリーンショット](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 詳しくは、「 [3-D グラフィックスの概要](https://msdn.microsoft.com/en-us/library/ms747437\(v=vs.100\).aspx)」をご覧ください。  
  
##  <a name="Animation"></a> アニメーション  
 WPF のアニメーション サポートを使用すると、コントロールを拡大、振動、スピン、フェードさせることができ、魅力的なページ遷移などを作成できです。 カスタム クラスも含めて、ほとんどの WPF クラスをアニメーション表示できます。 次の図に、実行中の単純なアニメーションを示します。  
  
 ![アニメーション キューブのイメージ](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 詳しくは、「 [アニメーションの概要](https://msdn.microsoft.com/en-us/library/ms752312\(v=vs.100\).aspx)」をご覧ください。  
  
##  <a name="Media"></a> メディア  
 リッチ コンテンツを伝達するための 1 つの方法は、オーディオビジュアル メディアを使用することです。 WPF では、イメージ、ビデオ、オーディオに対して特別なサポートを提供しています。  
  
### <a name="images"></a>イメージ  
 イメージは、ほとんどのアプリケーションに共通していますが、WPF にはイメージを使用するための、いくつかの方法が用意されています。 次の図に、サムネイル イメージが含まれているリスト ボックスがある、ユーザー インターフェイスを示します。 サムネイルを選ぶと、そのイメージがフル サイズで表示されます。  
  
 ![サムネイル イメージとフルサイズ イメージ](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")  
  
 詳しくは、「 [イメージングの概要](https://msdn.microsoft.com/en-us/library/ms748873\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="video-and-audio"></a>ビデオとオーディオ  
 <xref:System.Windows.Controls.MediaElement> コントロールは、オーディオとビデオの両方を再生でき、カスタム メディア プレーヤーの土台となれる柔軟性を備えています。 次の XAML マークアップは、メディア プレーヤーを実装します。  
  
 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]  
  
 次の図のウィンドウは、動作中の <xref:System.Windows.Controls.MediaElement> コントロールを示しています。  
  
 ![オーディオおよびビデオを含む MediaElement コントロール](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")  
  
 詳しくは、「 [WPF のグラフィックス、アニメーション、およびメディアの概要](https://msdn.microsoft.com/en-us/library/ms742562\(v=vs.100\).aspx)」をご覧ください。  
  
##  <a name="Text_and_Typography"></a> テキストとタイポグラフィ  
 高品質のテキスト レンダリングを容易に行うために、WPF では次の機能が提供されています。  
  
-   OpenType フォントのサポート。  
  
-   ClearType 機能拡張。  
  
-   ハードウェアの高速化を利用する高パフォーマンス。  
  
-   テキストと、メディア、グラフィックス、アニメーションとの統合。  
  
-   国際対応フォントのサポートとフォールバック メカニズム。  
  
 テキストとグラフィックスの統合のデモとして、次の図に文字の装飾の適用を示します。  
  
 ![さまざまなテキスト装飾を含むテキスト](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")  
  
 詳しくは、「 [Windows Presentation Foundation のタイポグラフィ](https://msdn.microsoft.com/en-us/library/ms742190\(v=vs.100\).aspx)」をご覧ください。  
  
##  <a name="WPF_Customization"></a> WPF アプリケーションのカスタマイズ  
 ここまで、アプリケーションを開発するための中核となる WPF 構成要素を説明してきました。 主にコントロールから成るアプリケーション コンテンツをホストして提供するには、アプリケーション モデルを使用します。 ユーザー インターフェイスでのコントロールの配置を簡素化して、ウィンドウ サイズや表示設定に変更が発生した場合にも配置を維持するには、WPF レイアウト システムを使用します。 ほとんどのアプリケーションでは、ユーザーがデータと対話できるようになっているため、データ バインディングを使用すればユーザー インターフェイスとデータの統合作業を削減できます。 アプリケーションの外観を向上させるには、WPF が提供する幅広いグラフィックス、アニメーション、メディアのサポートを使用します。  
  
 ただし多くの場合、基本要素だけでは、真に個性的で視覚的に美しいユーザー エクスペリエンスを作成し、管理するには不十分です。 標準の WPF コントロールでは、アプリケーションの目的の外観にはそぐわない場合があります。 最も効果的な方法でデータを表示できない可能性があります。 アプリケーションの全体的なユーザー エクスペリエンスが、Windows のテーマの既定のルック アンド フィールに適合しない場合があります。 多くの点で、プレゼンテーション技術には他の機能拡張と同様、視覚的な機能拡張性が必要です。  
  
 このため、WPF には独自のユーザー エクスペリエンスを作成するためのさまざまなメカニズムが用意されています。コントロール、トリガー、コントロールとデータのテンプレート、スタイル、ユーザー インターフェイスのリソース、テーマとスキン用の豊富なコンテンツ モデルがあります。  
  
### <a name="content-model"></a>コンテンツ モデル  
 大半の WPF コントロールの主な目的はコンテンツを表示することです。 WPF では、コントロールのコンテンツを構成するアイテムの種類と数を、コントロールの *コンテンツ モデル*と呼びます。 一部のコントロールには、1 つのアイテムと種類のコンテンツを含めることができます。たとえば、 <xref:System.Windows.Controls.TextBox> のコンテンツは <xref:System.Windows.Controls.TextBox.Text%2A> プロパティに割り当てられている文字列値です。 次の例では <xref:System.Windows.Controls.TextBox> のコンテンツを設定します。  
  
 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_10.xaml)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_11.xaml)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../designers/codesnippet/Xaml/introduction-to-wpf_12.xaml)]  
  
 次の図に、結果を示します。  
  
 ![テキストを含む TextBox コントロール](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")  
  
 しかし、さまざまな種類の複数のアイテムのコンテンツを含めることができるコントロールもあります。<xref:System.Windows.Controls.ContentControl.Content%2A> プロパティで指定された <xref:System.Windows.Controls.Button> のコンテンツには、レイアウト コントロール、テキスト、画像、図形などのさまざまなアイテムを含めることができます。 次の例に、<xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.Border>、<xref:System.Windows.Controls.MediaElement> を含むコンテンツを備えた <xref:System.Windows.Controls.Button> を示します。  
  
 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_13.xaml)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_14.xaml)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../designers/codesnippet/Xaml/introduction-to-wpf_15.xaml)]  
  
 次の図はこのボタンのコンテンツを示しています。  
  
 ![複数の種類の内容を含むボタン](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")  
  
 さまざまなコントロールでサポートされているコンテンツの種類について詳しくは、「 [WPF コンテンツ モデル](https://msdn.microsoft.com/en-us/library/bb613548\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="triggers"></a>トリガー  
 XAML マークアップの主な目的はアプリケーションの外観を実装することですが、XAML を使用してアプリケーションの動作の一部の機能を実装することもできます。 その一例として、ユーザーの操作に基づいて、アプリケーションの外観を変更するトリガーの使用があります。 詳しくは、「 [スタイルとテンプレート](https://msdn.microsoft.com/en-us/library/ms745683\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="control-templates"></a>コントロール テンプレート  
 WPF コントロールの既定のユーザー インターフェイスは、通常、他のコントロールと図形で構成されます。 たとえば、 <xref:System.Windows.Controls.Button> は <xref:Microsoft.Windows.Themes.ButtonChrome> コントロールと <xref:System.Windows.Controls.ContentPresenter> コントロールの両方で構成されます。 <xref:Microsoft.Windows.Themes.ButtonChrome> は標準的なボタンの外観を提供するのに対し、 <xref:System.Windows.Controls.ContentPresenter> は <xref:System.Windows.Controls.ContentControl.Content%2A> プロパティで指定したボタンのコンテンツを表示します。  
  
 コントロールの既定の外観が、アプリケーションの全体的な外観と調和しない場合もあります。 そのような場合は、 <xref:System.Windows.Controls.ControlTemplate> を使用すれば、コンテンツと動作を変更することなく、コントロールのユーザー インターフェイスの外観を変更できます。  
  
 たとえば、次の例は <xref:System.Windows.Controls.ControlTemplate> を使用して <xref:System.Windows.Controls.Button> の外観を変更する方法を示しています。  
  
 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]  
  
 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)] [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]  
  
 この例では、既定のボタン ユーザー インターフェイスが、濃い青の枠線を持ち、<xref:System.Windows.Media.RadialGradientBrush> で塗りつぶされた <xref:System.Windows.Shapes.Ellipse> に置き換えられています。 <xref:System.Windows.Controls.ContentPresenter> コントロールは <xref:System.Windows.Controls.Button>のコンテンツである "Click Me!" を表示します。 <xref:System.Windows.Controls.Button> がクリックされると、 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> コントロールの既定の動作の一部として <xref:System.Windows.Controls.Button> イベントが発生します。 結果を次の例に示します。  
  
 ![省略記号ボタンと 2 番目のウィンドウ](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")  
  
### <a name="data-templates"></a>データ テンプレート  
 コントロール テンプレートを使用すると、コントロールの外観を指定できますが、データ テンプレートではコントロールのコンテンツの外観を指定できます。 データ テンプレートはたいてい、バインドされたデータの表示方法を多様化するために使用されます。 次の図では、`Task` オブジェクトのコレクションにバインドされた <xref:System.Windows.Controls.ListBox> の既定の外観を示しています。各タスクは名前、説明、優先順位を持ちます。  
  
 ![既定の外観を使用したリスト ボックス](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")  
  
 既定の外観は <xref:System.Windows.Controls.ListBox> に期待されるものです。 ただし、各タスクの既定の外観にはタスク名しか含まれていません。 タスク名、説明、優先度の既定の外観を表示するには、 <xref:System.Windows.Controls.ListBox> コントロールのバインドされたリスト項目の既定の外観を、 <xref:System.Windows.DataTemplate>を使用して変更する必要があります。 次の XAML はこのような <xref:System.Windows.DataTemplate> を定義しています。これが、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 属性を使用して各タスクに適用されます。  
  
 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_18.xaml)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_19.xaml)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../designers/codesnippet/Xaml/introduction-to-wpf_20.xaml)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../designers/codesnippet/Xaml/introduction-to-wpf_21.xaml)]  
  
 次の図にこのコードの効果を示します。  
  
 ![データ テンプレートを使用するリスト ボックス](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")  
  
 <xref:System.Windows.Controls.ListBox> の動作と全体的な外観は保持されていることにご注意ください。リスト ボックスにより表示されるコンテンツの外観のみが変更されています。  
  
 詳しくは「 [データ テンプレートの概要](https://msdn.microsoft.com/en-us/library/ms742521\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="styles"></a>スタイル  
 スタイルを使うと、開発者とデザイナーは製品の特定の外観を標準化できます。 WPF には強力なスタイル モデルが用意されており、この基盤となるのが <xref:System.Windows.Style> 要素です。 次の例では、ウィンドウ上の各 <xref:System.Windows.Controls.Button> の背景色を `Orange` に設定するスタイルを作成しています。  
  
 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_22.xaml)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_23.xaml)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../designers/codesnippet/Xaml/introduction-to-wpf_24.xaml)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../designers/codesnippet/Xaml/introduction-to-wpf_25.xaml)]  
  
 このスタイルでは、すべての <xref:System.Windows.Controls.Button> コントロールを対象としているため、次の図に示すように、スタイルがウィンドウのすべてのボタンに自動的に適用されます。  
  
 ![2 つのオレンジ色のボタン](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")  
  
 詳しくは、「 [スタイルとテンプレート](https://msdn.microsoft.com/en-us/library/ms745683\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="resources"></a>リソース  
 アプリケーションのコントロール類は、同じ外観を持つ必要があります。こうした外観はフォントや背景色からコントロール テンプレート、データ テンプレート、スタイルまで、多岐にわたります。 ユーザー インターフェイスのリソースに対する WPF のサポートを使用すれば、こうした各種リソースを 1 つの場所でカプセル化して、再利用することができます。  
  
 次の例は <xref:System.Windows.Controls.Button> と <xref:System.Windows.Controls.Label> で共有される共通の背景色を定義しています。  
  
 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_26.xaml)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_27.xaml)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../designers/codesnippet/Xaml/introduction-to-wpf_28.xaml)]  
  
 この例では `Window.Resources` プロパティ要素を使用して、背景色リソースを実装しています。 このリソースは <xref:System.Windows.Window>のすべての子に使用できます。 次のように、リソースのスコープは多様です。この一覧では、解決される順序で各スコープが並べられています。  
  
1.  個々のコントロール (継承された <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> プロパティを使用)。  
  
2.  <xref:System.Windows.Window> または <xref:System.Windows.Controls.Page> (これも、継承された <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> プロパティを使用)。  
  
3.  <xref:System.Windows.Application> ( <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> プロパティを使用)。  
  
 このようなスコープの多様さのおかげで、リソースを柔軟に定義して共有できるようになります。  
  
 リソースを特定のスコープに直接関連付ける代わりに、アプリケーションの他の部分で参照できる別個の <xref:System.Windows.ResourceDictionary> を使用して、1 つ以上のリソースをパッケージ化することができます。 たとえば、次の例ではリソース ディクショナリに既定の背景色を定義しています。  
  
 [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_29.xaml)]  
[!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_30.xaml)]  
  
 次の例では、前の例で定義したリソース ディクショナリを参照し、アプリケーション全体で共有されるようにしています。  
  
 [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_31.xaml)]  
[!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../designers/codesnippet/Xaml/introduction-to-wpf_32.xaml)]  
  
 リソースおよびリソース ディクショナリは、テーマとスキンに対する WPF サポートの基礎です。  
  
 詳しくは、「 [リソースの概要](https://msdn.microsoft.com/en-us/library/ms750613\(v=vs.100\).aspx)」をご覧ください。  
  
### <a name="custom-controls"></a>カスタム コントロール  
 WPF にはカスタマイズに対する多くのサポートが用意されていますが、状況によっては既存の WPF コントロールではアプリケーションやそのユーザーのニーズを満たせない場合があります。 次のような状況が考えられます。  
  
-   WPF の既存の実装のルックアンドフィールをカスタマイズしても、必要とするユーザー インターフェイスを作成できない。  
  
-   WPF の既存の実装が、必要とする動作をサポートしない (または簡単にはサポートできない)。  
  
 ただし現時点では、3 つの WPF モデルのいずれかを利用して、新しいコントロールを作成できます。 各モデルは固有のシナリオを対象としており、カスタム コントロールは特定の WPF 基底クラスから派生するものでなければなりません。 この 3 つのモデルは次のとおりです。  
  
-   **ユーザー コントロール モデル** カスタム コントロールは <xref:System.Windows.Controls.UserControl> から派生し、他の 1 つ以上のコントロールで構成されます。  
  
-   **コントロール モデル** カスタム コントロールは <xref:System.Windows.Controls.Control> から派生し、大半の WPF コントロール同様、テンプレートを使用して、動作を外観から分離する実装を構築するために使用されます。 <xref:System.Windows.Controls.Control> から派生することにより、ユーザー コントロールよりも自由度の高いカスタム ユーザー インターフェイスを作成できますが、これにはより多くの労力が必要です。  
  
-   **フレームワーク要素モデル** カスタム コントロールは、カスタム レンダリング ロジック (テンプレートではなく) によって外観が定義されるときに、 <xref:System.Windows.FrameworkElement> から派生します。  
  
 次の例に <xref:System.Windows.Controls.UserControl> から派生するカスタムの数値のアップダウン コントロールを示します。  
  
 [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]  
  
 [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)] [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]  
  
 次の例は、ユーザー コントロールを <xref:System.Windows.Window> に組み込むために必要な XAML を示しています。  
  
 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]  
  
 次の図に <xref:System.Windows.Window> でホストされる `NumericUpDown` コントロールを示します。  
  
 ![カスタム UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")  
  
 カスタム コントロールについて詳しくは、「 [コントロールの作成の概要](https://msdn.microsoft.com/en-us/library/ms745025\(v=vs.100\).aspx)」をご覧ください。  
  
##  <a name="WPF_Best_Practices"></a> WPF のベスト プラクティス  
 WPF はすべての開発プラットフォームと同様、目的の結果を得るために、さまざまな方法で使用できます。 必要なユーザー エクスペリエンスを WPF アプリケーションが確実に提供し、オーディエンス一般の需要に応える 1 つの方法として、アクセシビリティ、グローバリゼーションとローカリゼーション、パフォーマンスに関するお勧めのベスト プラクティスがあります。 詳しくは、次のトピックをご覧ください。  
  
-   [ユーザー補助のベスト プラクティス](https://msdn.microsoft.com/en-us/library/aa350483\(v=vs.100\).aspx)ユーザー補助のベスト プラクティス  
  
-   [WPF のグローバリゼーションおよびローカリゼーションの概要](https://msdn.microsoft.com/en-us/library/ms788718\(v=vs.100\).aspx)  
  
-   [WPF アプリケーションのパフォーマンスの最適化](https://msdn.microsoft.com/en-us/library/aa970683\(v=vs.100\).aspx)  
  
-   [Windows Presentation Foundation のセキュリティ](https://msdn.microsoft.com/en-us/library/aa970906\(v=vs.100\).aspx)  
  
##  <a name="Summary"></a> まとめ  
 WPF とは、視覚的に美しいさまざまなクライアント アプリケーションを構築するための包括的なプレゼンテーション テクノロジです。 この概要では、WPF の主な機能を紹介しました。  
  
 次の手順では、WPF アプリケーションを構築します。  
  
 アプリケーションを作成する際に、この概要に立ち戻って主要な機能を思い出し、ここで取り上げられている機能をより詳しく説明したページへの参照を見つけることができます。  
  
## <a name="see-also"></a>関連項目  
 [WPF の概要](../designers/getting-started-with-wpf.md)   
 [Windows Presentation Foundation での最新のデスクトップ アプリケーションの作成](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)   
 [Windows Presentation Foundation](https://msdn.microsoft.com/en-us/library/ms754130\(v=vs.100\).aspx)
