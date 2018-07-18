---
title: イベントのサブスクライブ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41ed19cb31924e90ef9326aad5c8cad117996793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141904"
---
# <a name="subscribing-to-an-event"></a>イベントのサブスクライブ
このチュートリアルでは、実行中のドキュメント テーブル (RDT) 内のイベントに応答するツール ウィンドウを作成する方法について説明します。 ツール ウィンドウを実装するユーザー コントロールをホストする<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>メソッドは、イベントに、インターフェイスを接続します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="subscribing-to-rdt-events"></a>RDT イベントにサブスクライブします。  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>ツール ウィンドウで、拡張機能を作成するには  
  
1.  という名前のプロジェクトを作成する**RDTExplorer** VSIX テンプレートを使用して、という名前のカスタム ツール ウィンドウの項目テンプレートの追加**RDTExplorerWindow**です。  
  
     ツール ウィンドウで、拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
#### <a name="to-subscribe-to-rdt-events"></a>RDT イベントをサブスクライブするには  
  
1.  RDTExplorerWindowControl.xaml ファイルを開き、という名前のボタンを削除`button1`です。 追加、<xref:System.Windows.Forms.ListBox>を制御し、既定の名前をそのまま使用します。 グリッド要素は、次のようになります。  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  コード ビューで、RDTExplorerWindow.cs ファイルを開きます。 次の追加、ファイルの先頭にステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  変更、`RDTExplorerWindow`ためクラスから派生するだけでなくを<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>を実装するクラス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>インターフェイスです。  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> を実装します。  
  
    -   インターフェイスを実装します。 IVsRunningDocTableEvents 名の上にカーソルを置きます。 左側の余白に電球が表示されます。 電球の右側の矢印をクリックし、選択**インターフェイスの実装**です。  
  
5.  インターフェイス内の各メソッドで行を置き換えます。`throw new NotImplementedException();`に置き換えます。  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  RDTExplorerWindow クラスに cookie のフィールドを追加します。  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     によって返されるクッキーを保持してこの、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>メソッドです。  
  
7.  RDT イベントを登録する RDTExplorerWindow の Initialize() メソッドをオーバーライドします。 コンス トラクターではなく、ToolWindowPane の Initialize() メソッドでサービスを常に取得する必要があります。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>を取得するサービスが呼び出される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>インターフェイスです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> RDT イベントを実装するオブジェクトに接続<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>、ここでは、RDTExplorer オブジェクト。  
  
8.  RDTExplorerWindow の Dispose() メソッドを更新します。  
  
    ```csharp  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>メソッド間の接続を削除する`RDTExplorer`RDT イベント通知します。  
  
9. 本文に次の行を追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>ハンドラー、直前に、`return`ステートメントです。  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. 本文に同じような行を追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>ハンドラーと、リスト ボックスに表示する他のイベントにします。  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
12. 開く、 **RDTExplorerWindow** (**ビュー/その他の Windows/RDTExplorerWindow**)。  
  
     **RDTExplorerWindow**空のイベント一覧のウィンドウが開きます。  
  
13. 開くか、ソリューションを作成します。  
  
     として`OnBeforeLastDocument`と`OnAfterFirstDocument`イベントが発生した、イベントの一覧が表示されますの各イベントの通知です。