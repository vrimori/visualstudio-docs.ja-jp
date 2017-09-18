---
title: "[プロパティ] ウィンドウにプロパティを公開します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロパティ ブラウザーで公開するプロパティ [Visual Studio SDK]"
  - "プロパティ [Visual Studio SDK]"
  - "プロパティ ブラウザーでプロパティを公開します。"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# [プロパティ] ウィンドウにプロパティを公開します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルは、オブジェクトのパブリック プロパティを公開、 **プロパティ** ウィンドウです。 これらのプロパティに加えた変更が反映されて、 **プロパティ** ウィンドウです。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## \[プロパティ\] ウィンドウにプロパティを公開します。  
 ここでカスタム ツール ウィンドウを作成し、関連するウィンドウ ペイン内のオブジェクトのパブリック プロパティを表示、 **プロパティ** ウィンドウです。  
  
#### \[プロパティ\] ウィンドウにプロパティを公開するには  
  
1.  すべての Visual Studio 拡張機能は、拡張機能の資産を格納する VSIX 配置プロジェクトから開始します。 作成、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] という名前の VSIX プロジェクト `MyObjectPropertiesExtension`します。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#\/機能拡張**します。  
  
2.  ツール ウィンドウを追加するには、という名前のカスタム ツール ウィンドウの項目テンプレートを追加 `MyToolWindow`します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加\] ダイアログ ボックス**, には、 **Visual c\# アイテム\/機能拡張** 選択 **カスタム ツール ウィンドウ**します。**名** ダイアログの下部にあるフィールドに、ファイルの名前を変更する `MyToolWindow.cs`です。 カスタム ツール ウィンドウを作成する方法の詳細については、次を参照してください。 [ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
3.  MyToolWindow.cs を開き、次を追加するステートメントを使用します。  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  今すぐに次のフィールドを追加、 `MyToolWindow` クラスです。  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  MyToolWindow クラスに次のコードを追加します。  
  
    ```c#  
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
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection` プロパティで使用 `GetService` させることが、 `STrackSelection` が提供するサービス、 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> インターフェイスです。`OnToolWindowCreated` イベント ハンドラーと `SelectList` メソッドが一緒にのみ、ツール ウィンドウ ペイン オブジェクト自体を含む選択したオブジェクトのリストを作成します。`UpdateSelection` 方法では、 **プロパティ** ツール ウィンドウのペインのパブリック プロパティを表示するウィンドウです。  
  
6.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
7.  場合、 **プロパティ** ウィンドウが表示されない、F4 キーを押して開きます。  
  
8.  開いている、 **MyToolWindow** ウィンドウです。 これが見つかります **ビュー\/その他のウィンドウ**します。  
  
     ウィンドウが開き、ウィンドウ ペインのパブリック プロパティに表示されます、 **プロパティ** ウィンドウです。  
  
9. 変更、 **キャプション** プロパティに、 **プロパティ** ウィンドウ **My のオブジェクト プロパティ**します。  
  
     MyToolWindow ウィンドウのキャプションが適宜変更されます。  
  
## ツール ウィンドウのプロパティを公開します。  
 このセクションでは、ツール ウィンドウを追加し、そのプロパティを公開します。 プロパティに加えた変更が反映されて、 **プロパティ** ウィンドウです。  
  
#### ツール ウィンドウのプロパティを公開するには  
  
1.  MyToolWindow.cs を開き、MyToolWindow クラスにパブリック IsChecked ブール型のプロパティを追加します。  
  
    ```c#  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
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
  
     これにより、 `MyToolWindowControl` へのアクセスを `MyToolWindow` ウィンドウです。  
  
3.  MyToolWindow.cs、変更、 `MyToolWindow` 次のようにコンス トラクター。  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  MyToolWindowControl のデザイン ビューに変更します。  
  
5.  ボタンを削除してからチェック ボックスを追加、 **ツールボックス** 左上隅にします。  
  
6.  オンおよびオフにした場合のイベントを追加します。 デザイン ビューで、チェック ボックスを選択します。**プロパティ** ウィンドウで、イベント ハンドラー\] ボタンをクリックして \(上部の右、 **プロパティ** ウィンドウ\)。 検索 **Checked** と種類 **checkbox\_Checked** テキスト ボックス内を検索し、 **オフにした場合** と種類 **checkbox\_Unchecked** 、テキスト ボックスにします。  
  
7.  チェック ボックスをイベント ハンドラーを追加します。  
  
    ```c#  
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
  
9. 実験用インスタンスで開き、 **MyToolWindow** ウィンドウです。  
  
     ウィンドウのプロパティを検索、 **プロパティ** ウィンドウです。**IsChecked** プロパティが \[ウィンドウの下に表示される、 **マイ プロパティ** カテゴリ。  
  
10. チェック ボックスをオン、 **MyToolWindow** ウィンドウです。**IsChecked** で、 **プロパティ** にウィンドウが変更された **True**します。 チェック ボックスをオフに、 **MyToolWindow** ウィンドウです。**IsChecked** で、 **プロパティ** にウィンドウが変更された **False**します。 値を変更 **IsChecked** で、 **プロパティ** ウィンドウです。 チェック ボックス、 **MyToolWindow** ウィンドウが新しい値に一致するように変更します。  
  
    > [!NOTE]
    >  かどうかに表示されるオブジェクトを破棄する必要があります、 **プロパティ** ウィンドウで、呼び出し `OnSelectChange` で、 `null` 選択コンテナー最初です。 プロパティまたはオブジェクトを破棄した後に、更新の選択のコンテナーに変更できます <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> と <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> 一覧が表示されます。  
  
## 選択リストの変更  
 このセクションでは、基本的なプロパティのクラスの選択リストを追加しを表示するには、どの選択リストを選択するツール ウィンドウのインターフェイスを使用します。  
  
#### 選択リストを変更するには  
  
1.  MyToolWindow.cs を開き、という名前のパブリック クラスを追加 `Simple`します。  
  
    ```c#  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
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
  
2.  SimpleObject プロパティ MyToolWindow クラスとを切り替える 2 つのメソッドを追加、 **プロパティ** ウィンドウ ペインのどちらかのウィンドウを選択し、 `Simple` オブジェクトです。  
  
    ```c#  
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
  
3.  MyToolWindowControl.cs では、次の行のコードのチェック ボックスのハンドラーを置き換えます。  
  
    ```c#  
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
  
5.  実験用インスタンスで開き、 **MyToolWindow** ウィンドウです。  
  
6.  チェック ボックスをオン、 **MyToolWindow** ウィンドウです。**プロパティ** ウィンドウが表示されます、 `Simple` オブジェクトのプロパティ、 **しれません** と **ReadOnly**します。 チェック ボックスをオフにします。 ウィンドウのパブリック プロパティに表示されます、 **プロパティ** ウィンドウです。  
  
    > [!NOTE]
    >  表示名 **しれません** は **マイ テキスト**します。  
  
## ベスト プラクティス  
 このチュートリアルで <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> は選択可能オブジェクトのコレクションや選択したオブジェクトのコレクションは、同じコレクションに実装します。 プロパティ ブラウザーの一覧で選択したオブジェクトのみが表示されます。 詳細な ISelectionContainer 実装 Reference.ToolWindow サンプルを参照してください。  
  
 Visual Studio のツール ウィンドウは、Visual Studio セッション間で保持します。 ツール ウィンドウの状態を永続化の詳細については、次を参照してください。 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>します。  
  
## 参照  
 [プロパティと \[プロパティ\] ウィンドウの拡張](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md)