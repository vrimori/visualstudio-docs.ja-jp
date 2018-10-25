---
title: '[プロパティ] ウィンドウにプロパティを公開する |Microsoft Docs'
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
ms.openlocfilehash: 1a37dcac9d75cbd773894b3d708dd4931f77b4ce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888412"
---
# <a name="expose-properties-to-the-properties-window"></a>[プロパティ] ウィンドウにプロパティを公開します。
このチュートリアルは、オブジェクトのパブリック プロパティを公開、**プロパティ**ウィンドウ。 これらのプロパティに加えた変更に反映されます、**プロパティ**ウィンドウ。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="expose-properties-to-the-properties-window"></a>[プロパティ] ウィンドウにプロパティを公開します。  
 このセクションでカスタム ツール ウィンドウの作成し、の関連するウィンドウ ペインのオブジェクトのパブリック プロパティを表示、**プロパティ**ウィンドウ。  
  
### <a name="to-expose-properties-to-the-properties-window"></a>[プロパティ] ウィンドウにプロパティを公開するには  
  
1. すべての Visual Studio 拡張機能は、拡張機能資産が含まれる VSIX 配置プロジェクトで開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`MyObjectPropertiesExtension`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** > **Extensibility**します。  
  
2. ツール ウィンドウを追加するには、という名前のカスタム ツール ウィンドウの項目テンプレートを追加`MyToolWindow`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 **新しい項目の追加 ダイアログ**に移動して、 **Visual c# アイテム** > **拡張**選択**カスタム ツール ウィンドウ**。 **名前**ダイアログの下部にあるフィールドに、ファイル名を変更して*MyToolWindow.cs*します。 カスタム ツール ウィンドウを作成する方法の詳細については、次を参照してください。[ツール ウィンドウで拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
3. オープン*MyToolWindow.cs*し、次を追加ステートメントを使用します。  
  
   ```csharp  
   using System.Collections;  
   using System.ComponentModel;  
   using Microsoft.VisualStudio.Shell.Interop;  
   ```  
  
4. 次のフィールドを追加、`MyToolWindow`クラス。  
  
   ```csharp  
   private ITrackSelection trackSel;  
   private SelectionContainer selContainer;  
  
   ```  
  
5. `MyToolWindow` クラスに次のコードを追加します。  
  
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
  
    `TrackSelection`プロパティで使用`GetService`を取得する、`STrackSelection`提供するサービスを<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>インターフェイス。 `OnToolWindowCreated`イベント ハンドラーと`SelectList`メソッドが一緒にのみ、ツール ウィンドウ ペイン オブジェクト自体を含む、選択したオブジェクトのリストを作成します。 `UpdateSelection`方法では、**プロパティ**ツール ウィンドウ ペインのパブリック プロパティを表示するウィンドウ。  
  
6. プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
7. 場合、**プロパティ**ウィンドウが表示されない、キーを押して開きます**F4**します。  
  
8. 開く、 **MyToolWindow**ウィンドウ。 見つかります**ビュー** > **その他の Windows**します。  
  
    ウィンドウが開き、ウィンドウ ペインのパブリック プロパティに表示されます、**プロパティ**ウィンドウ。  
  
9. 変更、**キャプション**プロパティ、**プロパティ**ウィンドウ**My のオブジェクト プロパティ**します。  
  
     MyToolWindow ウィンドウのキャプションを適宜変更します。  
  
## <a name="expose-tool-window-properties"></a>ツール ウィンドウのプロパティを公開します。  
 このセクションでは、ツール ウィンドウを追加し、そのプロパティを公開します。 プロパティに加えた変更に反映されます、**プロパティ**ウィンドウ。  
  
### <a name="to-expose-tool-window-properties"></a>ツール ウィンドウのプロパティを公開するには  
  
1.  開いている*MyToolWindow.cs*、IsChecked のパブリックのブール型プロパティを追加する、`MyToolWindow`クラス。  
  
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
  
     このプロパティは、後で作成した WPF のチェック ボックスからの状態を取得します。  
  
2.  開いている*MyToolWindowControl.xaml.cs* MyToolWindowControl コンス トラクターを次のコードに置き換えます。  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     これにより、`MyToolWindowControl`へのアクセス、`MyToolWindow`ウィンドウ。  
  
3.  *MyToolWindow.cs*、変更、`MyToolWindow`次のようにコンス トラクター。  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  MyToolWindowControl のデザイン ビューに変更します。  
  
5.  ボタンを削除してから、チェック ボックスを追加、**ツールボックス**左上隅にします。  
  
6.  Checked と Unchecked イベントを追加します。 デザイン ビューで、チェック ボックスを選択します。 **プロパティ**ウィンドウで、イベント ハンドラー ボタンをクリックします (上部の右、**プロパティ**ウィンドウ)。 検索**Checked**と種類**checkbox_Checked** 、テキスト ボックス内を検索し、**未チェック**と種類**checkbox_Unchecked**テキスト ボックスに。  
  
7.  チェック ボックスのイベント ハンドラーを追加します。  
  
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
  
9. 実験用インスタンスの開く、 **MyToolWindow**ウィンドウ。  
  
     ウィンドウのプロパティを探して、**プロパティ**ウィンドウ。 **IsChecked**プロパティが ウィンドウの下に表示される、**マイ プロパティ**カテゴリ。  
  
10. チェック ボックスをオンに、 **MyToolWindow**ウィンドウ。 **IsChecked**で、**プロパティ**にウィンドウが変更された**True**します。 チェック ボックスをオフ、 **MyToolWindow**ウィンドウ。 **IsChecked**で、**プロパティ**にウィンドウが変更された**False**します。 値を変更**IsChecked**で、**プロパティ**ウィンドウ。 チェック ボックス、 **MyToolWindow**ウィンドウが、新しい値に一致するように変更します。  
  
    > [!NOTE]
    >  かどうかに表示されるオブジェクトを破棄する必要があります、**プロパティ**ウィンドウで、呼び出し`OnSelectChange`で、`null`選択コンテナー最初。 プロパティまたはオブジェクトを破棄して、後に更新されている選択コンテナーに変更できます<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A>と<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A>を一覧表示します。  
  
## <a name="change-selection-lists"></a>選択リストを変更します。  
 このセクションでは、プロパティの基本クラスの選択リストを追加し、ツール ウィンドウ インターフェイスを使用して表示する選択リストを選択します。  
  
### <a name="to-change-selection-lists"></a>選択リストを変更するには  
  
1.  開いている*MyToolWindow.cs*という名前のパブリック クラスを追加および`Simple`します。  
  
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
  
2.  追加、`SimpleObject`プロパティを`MyToolWindow`を切り替える 2 つのメソッドとクラスを**プロパティ**ウィンドウ ペインの間でウィンドウの選択と`Simple`オブジェクト。  
  
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
  
3.  *MyToolWindowControl.cs*、チェック ボックスをオンのハンドラーを次の行のコードに置き換えます。  
  
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
  
5.  実験用インスタンスの開く、 **MyToolWindow**ウィンドウ。  
  
6.  チェック ボックスをオン、 **MyToolWindow**ウィンドウ。 **プロパティ**ウィンドウが表示されます、`Simple`オブジェクトのプロパティ、**しれません**と**ReadOnly**します。 チェック ボックスをオフにします。 ウィンドウのパブリック プロパティに表示されます、**プロパティ**ウィンドウ。  
  
    > [!NOTE]
    >  表示名**しれません**は**マイ テキスト**します。  
  
## <a name="best-practice"></a>ベスト プラクティス  
 このチュートリアルで<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>は選択可能なオブジェクトのコレクションと、選択したオブジェクトのコレクションが、同じコレクションになるように実装されます。 プロパティ ブラウザーの一覧で選択したオブジェクトのみが表示されます。 詳細な ISelectionContainer 実装、Reference.ToolWindow のサンプルを参照してください。  
  
 Visual Studio のツール ウィンドウは、Visual Studio セッション間で保持します。 ツール ウィンドウの状態を永続化の詳細については、次を参照してください。<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティと、[プロパティ] ウィンドウを拡張します。](../extensibility/extending-properties-and-the-property-window.md)