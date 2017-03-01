---
title: "イベントにサブスクライブする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6bd1dd320ad5366ef494a8db958614d837529320
ms.lasthandoff: 02/22/2017

---
# <a name="subscribing-to-an-event"></a>イベントのサブスクライブ
このチュートリアルでは、実行中のドキュメント テーブル (RDT) 内のイベントに応答するツール ウィンドウを作成する方法について説明します。 ツール ウィンドウ<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>を実装するユーザー コントロールをホストします。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>メソッドは、イベントに、インターフェイスを接続します</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="subscribing-to-rdt-events"></a>RDT イベントにサブスクライブします。  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>ツール ウィンドウで、拡張機能を作成するには  
  
1.  という名前のプロジェクトを作成する**RDTExplorer** VSIX のテンプレートを使用し、という名前のカスタム ツール ウィンドウの項目テンプレートを追加**RDTExplorerWindow**します。  
  
     ツール ウィンドウで拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
#### <a name="to-subscribe-to-rdt-events"></a>RDT イベントをサブスクライブするには  
  
1.  RDTExplorerWindowControl.xaml ファイルを開き、という名前のボタンを削除`button1`します。 追加、<xref:System.Windows.Forms.ListBox>を制御し、既定の名前をそのまま使用します</xref:System.Windows.Forms.ListBox>。 グリッド要素は、次のようになります。  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  コード ビューで RDTExplorerWindow.cs ファイルを開きます。 次の追加、ファイルの先頭に using ステートメントです。  
  
    ```c#  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  変更、`RDTExplorerWindow`ためクラスから派生するだけでなくを<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスが実装して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents></xref:Microsoft.VisualStudio.Shell.ToolWindowPane>。  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>  
  
    -   インターフェイスを実装します。 IVsRunningDocTableEvents 名の上にカーソルを置きます。 左の余白に電球が表示されます。 電球の右側に、矢印をクリックして選択**インターフェイスの実装**します。  
  
5.  インターフェイス内の各メソッドで行を置き換えます`throw new NotImplementedException();`この。  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  RDTExplorerWindow クラスには、cookie フィールドを追加します。  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     これによって返されるクッキーを保持して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>。  
  
7.  RDT イベントを登録する RDTExplorerWindow の Initialize() メソッドをオーバーライドします。 コンス トラクターではなく、ToolWindowPane の Initialize() メソッドで常にサービスを取得する必要があります。  
  
    ```c#  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>を取得するサービスが呼び出されると、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable></xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>RDT イベントを実装するオブジェクトに接続<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>、ここでは、RDTExplorer オブジェクト</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>。  
  
8.  RDTExplorerWindow の Dispose() メソッドを更新します。  
  
    ```c#  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>メソッド間の接続を削除する`RDTExplorer`とイベント通知を RDT</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> 。  
  
9. 本体に次の行を追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>ハンドラー、直前に、`return`ステートメント</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>。  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. 本文に同じような行を追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>ハンドラーと、リスト ボックスに表示するその他のイベント</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>。  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
12. 開いている、 **RDTExplorerWindow** (**ビュー/その他の Windows/RDTExplorerWindow**)。  
  
     **RDTExplorerWindow**空のイベント一覧のウィンドウが開きます。  
  
13. 開くか、ソリューションを作成します。  
  
     として`OnBeforeLastDocument`と`OnAfterFirstDocument`イベントが発生した、イベントの一覧が表示されますの各イベントの通知。
