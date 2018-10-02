---
title: イベントのサブスクライブ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 77f277a63d08752ddbcb7e25bae4aa82867d280e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536458"
---
# <a name="subscribing-to-an-event"></a>イベントのサブスクライブ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[イベントのサブスクライブ](https://docs.microsoft.com/visualstudio/extensibility/subscribing-to-an-event)します。  
  
このチュートリアルでは、実行中のドキュメント テーブル (RDT) 内のイベントに応答するツール ウィンドウを作成する方法について説明します。 ツール ウィンドウを実装するユーザー コントロールをホストする<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>メソッドは、イベントに、インターフェイスを接続します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="subscribing-to-rdt-events"></a>RDT のイベントにサブスクライブします。  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>ツール ウィンドウで、拡張機能を作成するには  
  
1.  という名前のプロジェクトを作成する**RDTExplorer** VSIX のテンプレートを使用して、という名前のカスタム ツール ウィンドウの項目テンプレートを追加**RDTExplorerWindow**します。  
  
     ツール ウィンドウで拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
#### <a name="to-subscribe-to-rdt-events"></a>RDT のイベントをサブスクライブするには  
  
1.  RDTExplorerWindowControl.xaml ファイルを開き、という名前のボタンを削除`button1`します。 追加、<xref:System.Windows.Forms.ListBox>を制御し、既定の名前をそのまま使用します。 このようグリッド要素になります。  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  コード ビューで RDTExplorerWindow.cs ファイルを開きます。 次の追加、ファイルの先頭にステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  変更、`RDTExplorerWindow`ためクラスから派生するだけでなくを<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスは実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>インターフェイス。  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> を実装します。  
  
    -   インターフェイスを実装します。 IVsRunningDocTableEvents 名にカーソルを置きます。 左の余白に電球が表示されます。 電球の右側の下矢印をクリックして選択します**インターフェイスの実装**します。  
  
5.  インターフェイスの各メソッドでは、行を置き換えます`throw new NotImplementedException();`この。  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  RDTExplorerWindow クラスには、cookie フィールドを追加します。  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     これは、によって返されるクッキー、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>メソッド。  
  
7.  RDT のイベントを登録する RDTExplorerWindow の Initialize() メソッドをオーバーライドします。 サービスは、コンス トラクターではなく、ToolWindowPane の Initialize() メソッドで常に表示されます。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>サービスを呼び出して取得する<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>インターフェイス。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>メソッド RDT イベントを実装するオブジェクトには接続<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>、ここでは、RDTExplorer オブジェクト。  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>メソッド間の接続を削除する`RDTExplorer`と RDT のイベント通知。  
  
9. 本文に次の行を追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>ハンドラー、直前に、`return`ステートメント。  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. 本体に似た行を追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>ハンドラーと、リスト ボックスに表示する他のイベントにします。  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
12. 開く、 **RDTExplorerWindow** (**ビュー/その他の Windows/RDTExplorerWindow**)。  
  
     **RDTExplorerWindow**空のイベントのリストを持つウィンドウを開きます。  
  
13. 開くか、ソリューションを作成します。  
  
     として`OnBeforeLastDocument`と`OnAfterFirstDocument`イベントが発生した、イベントの一覧が表示されますの各イベントの通知。

