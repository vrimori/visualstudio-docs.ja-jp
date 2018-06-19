---
title: '[プロパティ] ウィンドウにプロパティを公開する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12dcb30374250ca7aa917cf19b3a01ba57862c6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134263"
---
# <a name="exposing-properties-to-the-properties-window"></a>[プロパティ] ウィンドウにプロパティを公開します。
このチュートリアルは、オブジェクトのパブリック プロパティを公開、**プロパティ**ウィンドウです。 これらのプロパティに加えた変更に反映されます、**プロパティ**ウィンドウです。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="exposing-properties-to-the-properties-window"></a>[プロパティ] ウィンドウにプロパティを公開します。  
 このセクションでカスタム ツール ウィンドウを作成し、関連付けられたウィンドウ ペイン内のオブジェクトのパブリック プロパティを表示、**プロパティ**ウィンドウです。  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>[プロパティ] ウィンドウにプロパティを公開するには  
  
1.  すべての Visual Studio 拡張機能は、資産を拡張機能を含んでいる VSIX 配置プロジェクトを開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`MyObjectPropertiesExtension`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  という名前のカスタムのツール ウィンドウの項目テンプレートを追加することで、ツール ウィンドウを追加`MyToolWindow`です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加 ダイアログ**には、 **Visual c# アイテム/機能拡張**選択**カスタムのツール ウィンドウ**します。 **名前**ダイアログの下部にあるフィールドに、ファイル名に変更`MyToolWindow.cs`です。 カスタムのツール ウィンドウを作成する方法の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
3.  MyToolWindow.cs を開き、次を追加するステートメントを使用します。  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  ここで、次のフィールドを追加、`MyToolWindow`クラスです。  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  MyToolWindow クラスに次のコードを追加します。  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection`プロパティ使用`GetService`を取得する、`STrackSelection`が提供するサービス、<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>インターフェイスです。 `OnToolWindowCreated`イベント ハンドラーと`SelectList`メソッドが一緒にのみ、ツール ウィンドウ ペイン オブジェクト自体を含む選択されたオブジェクトのリストを作成します。 `UpdateSelection`方法では、**プロパティ**ツール ウィンドウ ペインのパブリック プロパティを表示するウィンドウです。  
  
6.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
7.  場合、**プロパティ**ウィンドウが表示されない、F4 キーを押して開きます。  
  
8.  開く、 **MyToolWindow**ウィンドウです。 検索できる**ビュー/その他のウィンドウ**します。  
  
     ウィンドウが開き、ウィンドウ ペインのパブリック プロパティに表示されます、**プロパティ**ウィンドウです。  
  
9. 変更、**キャプション**プロパティに、**プロパティ**ウィンドウ**My のオブジェクト プロパティ**です。  
  
     MyToolWindow ウィンドウのキャプションを適宜変更します。  
  
## <a name="exposing-tool-window-properties"></a>ツール ウィンドウのプロパティを公開します。  
 このセクションでは、ツール ウィンドウを追加し、そのプロパティを公開します。 プロパティに対して行った変更に反映されます、**プロパティ**ウィンドウです。  
  
#### <a name="to-expose-tool-window-properties"></a>ツール ウィンドウのプロパティを公開するには  
  
1.  MyToolWindow.cs を開き、MyToolWindow クラスにパブリックのブール型プロパティ IsChecked を追加します。  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     このプロパティは、後ほど作成する WPF のチェック ボックスからの状態を取得します。  
  
2.  MyToolWindowControl.xaml.cs を開き、MyToolWindowControl コンス トラクターを次のコードに置き換えます。  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     これにより、`MyToolWindowControl`へのアクセス、`MyToolWindow`ウィンドウです。  
  
3.  MyToolWindow.cs、変更、`MyToolWindow`次のようにコンス トラクター。  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  MyToolWindowControl のデザイン ビューに変更します。  
  
5.  ボタンを削除してから、チェック ボックスを追加、**ツールボックス**左上隅にします。  
  
6.  オンおよびオフにした場合のイベントを追加します。 デザイン ビューで、チェック ボックスを選択します。 **プロパティ**ウィンドウで、イベント ハンドラー ボタンをクリックして (上部の右、**プロパティ**ウィンドウ)。 検索**Checked**および種類**checkbox_Checked** 、テキスト ボックス内を検索し、**オフにした場合**と型**checkbox_Unchecked**テキスト ボックスにします。  
  
7.  チェック ボックスをイベント ハンドラーを追加します。  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  プロジェクトをビルドし、デバッグを開始します。  
  
9. 実験用インスタンスの開く、 **MyToolWindow**ウィンドウです。  
  
     ウィンドウのプロパティを検索、**プロパティ**ウィンドウです。 **IsChecked**プロパティが ウィンドウの下に表示される、**マイ プロパティ**カテゴリ。  
  
10. チェック ボックスを確認してください。、 **MyToolWindow**ウィンドウです。 **IsChecked**で、**プロパティ**にウィンドウが変更された**True**です。 チェック ボックスをオフに、 **MyToolWindow**ウィンドウです。 **IsChecked**で、**プロパティ**にウィンドウが変更された**False**です。 値を変更**IsChecked**で、**プロパティ**ウィンドウです。 チェック ボックスを**MyToolWindow**ウィンドウが新しい値を一致するように変更します。  
  
    > [!NOTE]
    >  表示されるオブジェクトを破棄しなければならないかどうか、**プロパティ**ウィンドウで、呼び出し`OnSelectChange`で、`null`選択コンテナー最初。 プロパティまたはオブジェクトを破棄した後に更新されている選択コンテナーに変更することができます<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A>と<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A>を一覧表示します。  
  
## <a name="changing-selection-lists"></a>選択リストの変更  
 このセクションでは、プロパティの基本クラスの選択リストを追加およびインターフェイスを使用して、ツール ウィンドウを表示するには、どの選択リストを選択します。  
  
#### <a name="to-change-selection-lists"></a>選択リストを変更するには  
  
1.  MyToolWindow.cs を開き、という名前のパブリック クラスを追加`Simple`です。  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  SimpleObject プロパティ MyToolWindow クラスとを切り替える 2 つのメソッドを追加する、**プロパティ**ウィンドウ ペインの間でウィンドウの選択と`Simple`オブジェクト。  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  MyToolWindowControl.cs では、チェック ボックスをハンドラーに次のコード行を置き換えます。  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。  
  
5.  実験用インスタンスの開く、 **MyToolWindow**ウィンドウです。  
  
6.  チェック ボックスをオン、 **MyToolWindow**ウィンドウです。 **プロパティ**ウィンドウが表示されます、`Simple`オブジェクト プロパティ、**しれません**と**ReadOnly**です。 チェック ボックスをオフにします。 ウィンドウのパブリック プロパティに表示されます、**プロパティ**ウィンドウです。  
  
    > [!NOTE]
    >  表示名**しれません**は**マイ テキスト**です。  
  
## <a name="best-practice"></a>ベスト プラクティス  
 このチュートリアルで<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>は選択可能オブジェクトのコレクションや選択したオブジェクトのコレクションは、同じコレクションには実装されています。 プロパティ ブラウザーの一覧で選択したオブジェクトのみが表示されます。 詳細な ISelectionContainer 実装、Reference.ToolWindow のサンプルを参照してください。  
  
 Visual Studio のツール ウィンドウは、Visual Studio セッション間で保持されます。 ツール ウィンドウの状態を永続化の詳細については、次を参照してください。<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>です。  
  
## <a name="see-also"></a>関連項目  
 [プロパティとプロパティ ウィンドウの拡張](../extensibility/extending-properties-and-the-property-window.md)