---
title: "チュートリアル: カスタム エディターの機能の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - カスタムの機能を追加します。"
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
caps.handback.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
---
# チュートリアル: カスタム エディターの機能の追加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

カスタム エディターを作成した後は、それにより多くの機能を追加できます。  
  
### VSPackage のエディターを作成するには  
  
1.  Visual Studio パッケージ プロジェクト テンプレートを使用してカスタム エディターを作成します。  
  
     詳細については、「[チュートリアル: カスタム エディターの作成](../extensibility/walkthrough-creating-a-custom-editor.md)」を参照してください。  
  
2.  1 つのビューまたは複数のビューをサポートするエディターとして使用するかどうかを決定します。  
  
     サポートしている、 **新しいウィンドウ** コマンド、またはフォーム ビューとコード ビューには、データ オブジェクトの個別のドキュメントおよびドキュメント ビューのオブジェクトが必要です。 エディターで 1 つのビューのみをサポートする、ドキュメント データ オブジェクトとドキュメント ビューのオブジェクトに実装できます、同じオブジェクトです。  
  
     複数のビューの例は、次を参照してください。 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)します。  
  
3.  エディター ファクトリを実装することによって実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> インターフェイスです。  
  
     詳細については、「[エディター ファクトリ](../extensibility/editor-factories.md)」を参照してください。  
  
4.  インプレース アクティブ化を使用するエディターで、または、簡略化された埋め込みドキュメント ビューのオブジェクト\] ウィンドウを管理するかどうかを決定します。  
  
     簡略化された埋め込みエディター ウィンドウは、埋め込みエディター ウィンドウは、ActiveX コントロールまたはそのドキュメント ビューとその他のアクティブなオブジェクトをホストしている間に、標準のドキュメント ビューをホストします。 詳細については、次のトピックを参照してください。[簡略化された埋め込み](../extensibility/simplified-embedding.md) および[埋め込み先編集の有効化](../misc/in-place-activation.md).  
  
5.  実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> コマンドを処理するインターフェイスです。  
  
6.  次の手順に従って、ドキュメントの持続性および外部ファイルの変更に応答を提供します。  
  
    1.  ファイルを保持するため実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> と <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> エディターのドキュメントのデータ オブジェクトにします。  
  
    2.  外部ファイルの変更に応答して、実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> エディターのドキュメントのデータ オブジェクトにします。  
  
        > [!NOTE]
        >  呼び出す `QueryService` に <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> へのポインターを取得する `IVsFileChangeEx`です。  
  
7.  ソース コード管理とドキュメント編集のイベントを調整します。 この操作を行うには、次の手順を実行します。  
  
    1.  ポインターを取得 `IVsQueryEditQuerySave2` を呼び出して `QueryService` に <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>します。  
  
    2.  最初の編集イベントが発生したときに呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> メソッドです。  
  
         これには、ユーザーが、既にチェック アウトされていない場合に、ファイルをチェック\_アウトように求められます。 エラーを回避する「ファイルがチェック アウトされていない」状態に対処することを確認します。  
  
    3.  同様に、ファイルを保存する前に呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> メソッドです。  
  
         このメソッドは、保存されていない場合、または最後に保存してから変更された場合は、ファイルを保存するユーザーに求めます。  
  
8.  有効にする、 **プロパティ** をエディターで選択したテキストのプロパティを表示するウィンドウです。 この操作を行うには、次の手順を実行します。  
  
    1.  呼び出す <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 各時刻のテキストの選択が変更、受け渡しの実装で <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>します。  
  
    2.  呼び出す `QueryService` に <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> サービスへのポインターを取得する <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>です。  
  
9. 項目エディターの間でドラッグ アンド ドロップできるようにして、 **ツールボックス**, 、または Microsoft Word などの外部エディターの間で、 **ツールボックス**します。 この操作を行うには、次の手順を実行します。  
  
    1.  実装 `IDropTarget` 、エディターに、エディターがドロップ先である IDE のアラートを生成します。  
  
    2.  実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> ビューのエディターが有効にして内の項目を無効にするためのインターフェイス、 **ツールボックス**します。  
  
    3.  実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> を呼び出すと `QueryService` に <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> サービスへのポインターを取得する、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> インターフェイスです。  
  
         これにより、新しい項目を追加する、VSPackage、 **ツールボックス**します。  
  
10. エディターの他の省略可能な機能をするかどうかを決定します。  
  
    -   サポートするために、エディターの場合は、検索、およびコマンドは置き換え実装 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>します。  
  
    -   エディターでドキュメントのアウトライン ツール ウィンドウを使用する場合は、実装 `IVsDocOutlineProvider`します。  
  
    -   エディターでステータス バーを使用する場合は、実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> を呼び出すと `QueryService` の <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> へのポインターを取得する `IVsStatusBar`です。  
  
         たとえば、エディターは行を表示できます\/列については、選択モード \(ストリーム\/ボックス\) や挿入モード \(挿入\/overstrike\)。  
  
    -   サポートするエディターとして使用する場合、 `Undo` コマンドを OLE 元に戻すマネージャー モデルの使用はお勧めします。 代わりに、エディターのハンドルを持つことができます、 `Undo` コマンドを直接します。  
  
11. レジストリ VSPackage、メニューのエディター、およびその他の機能の Guid をなどの情報を作成します。  
  
     コード エディターを適切に登録する方法を示す、.rgs ファイルのスクリプトを配置することはの汎用例を次に示します。  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. 状況依存のヘルプのサポートを実装します。  
  
     これにより、F1 ヘルプおよびダイナミック ヘルプ\] ウィンドウは、エディター内の項目のサポートを提供することができます。 詳細については、「[方法: エディターのコンテキストの提供](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md)」を参照してください。  
  
13. 実装することによって、エディターからオートメーション オブジェクト モデルを公開、 `IDispatch` インターフェイスです。  
  
     詳細については、「[オートメーション モデルに貢献しています。](../extensibility/internals/contributing-to-the-automation-model.md)」を参照してください。  
  
## 信頼性の高いプログラミング  
  
-   IDE を呼び出すと、エディターのインスタンスが作成された、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> メソッドです。 エディターは、複数のビューをサポートしている場合 `CreateEditorInstance` ドキュメント データとドキュメント ビューのオブジェクトの両方を作成します。 ドキュメント データ オブジェクトが既にある場合は、開くには、null でない `punkDocDataExisting` に値が渡される `IVsEditorFactory::CreateEditorInstance`です。 エディター ファクトリの実装に適切なインターフェイスを照会して、既存のドキュメント データ オブジェクトが互換性があるかどうかを判断する必要があります。 詳細については、「[複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)」を参照してください。  
  
-   簡略化した埋め込み方法を使用する場合は、実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> インターフェイスです。  
  
-   インプレースでライセンス認証を使用する場合は、次のインターフェイスを実装します。  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` インターフェイスは OLE 2 メニューの結合を避けるために使用します。  
  
     `IOleCommandTarget` の実装などのコマンドを処理 **切り取り**, 、**コピー**, 、および **貼り付け**します。 実装するときに `IOleCommandTarget`, で定義されている標準のコマンドを実装できるかどうか、エディターに独自のコマンドのメニュー構造を定義する、独自の .vsct ファイルが必要かどうか設定したり、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 一般に、エディターを使用して IDE のメニューを拡張し、それぞれ独自のツールバーを定義します。 ただし、多くの場合、必要がある、エディターを IDE の標準的なコマンド セットを使用するだけでなく、独自の特定のコマンドを定義します。 これを行うには、エディターは標準のコマンドを使用し、.vsct ファイルで、新しいコマンド、コンテキスト メニューのトップレベルのメニューおよびツールバーを定義を宣言する必要があります。 エディターで、インプレース アクティブ化を作成する場合、実装 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> し OLE 2 メニューのマージを使用する代わりに .vsct ファイルのエディターのメニューおよびツールバーを定義します。  
  
-   UI に増やし、メニュー コマンドを防ぐためには、新しいコマンドを開発する前に、IDE で既存のコマンドを使用する必要があります。 共有のコマンドは、SharedCmdDef.vsct および ShellCmdDef.vsct で定義されます。 既定の VisualStudioIntegration\\Common\\Inc サブディレクトリでこれらのファイルがインストールされている、 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] インストールします。  
  
-   `ISelectionContainer` 単一および複数の両方の選択内容を表すことができます。 選択した各オブジェクトは、 `IDispatch` オブジェクトです。  
  
-   IDE を実装して `IOleUndoManager` からアクセス可能なサービスとして、 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> またはインスタンス化するとき使用されるオブジェクトとして <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>します。 エディターが実装する、 `IOleUndoUnit` ごとにインターフェイス `Undo` アクション。  
  
-   2 つの場所のカスタム エディターは、オートメーション オブジェクトを公開できます。  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## 参照  
 [オートメーション モデルに貢献しています。](../extensibility/internals/contributing-to-the-automation-model.md)   
 [方法: エディターのコンテキストの提供](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md)