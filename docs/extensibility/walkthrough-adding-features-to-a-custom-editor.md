---
title: "チュートリアル: カスタム エディターの機能の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df3621d87ae80c0eee105183edbc97a4e7ade62f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>チュートリアル: カスタム エディターの機能の追加
カスタム エディターを作成した後は、それにより多くの機能を追加できます。  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage のエディターを作成するには  
  
1.  カスタム エディターを作成するには、Visual Studio パッケージ プロジェクト テンプレートを使用します。  
  
     詳細については、次を参照してください。[チュートリアル: カスタム エディターを作成する](../extensibility/walkthrough-creating-a-custom-editor.md)です。  
  
2.  1 つのビューまたは複数のビューをサポートするためにエディターとして使用するかどうかを決定します。  
  
     サポートしている、**新しいウィンドウ**コマンド、またはフォーム ビューとコード ビューには、データ オブジェクトの個別のドキュメントおよびドキュメント ビュー オブジェクトが必要です。 1 つのビューのみをサポートする、エディターで、ドキュメント データ オブジェクトと、ドキュメント ビュー オブジェクトに実装できます、同じオブジェクトです。  
  
     複数のビューの例は、次を参照してください。[複数ドキュメントのビューをサポートする](../extensibility/supporting-multiple-document-views.md)です。  
  
3.  エディター ファクトリを実装することによって実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイスです。  
  
     詳細については、次を参照してください。[エディター ファクトリ](../extensibility/editor-factories.md)です。  
  
4.  インプレース アクティブ化を使用するエディターで、または埋め込みドキュメント ビュー オブジェクト ウィンドウの管理を簡略化するかどうかを決定します。  
  
     簡略化された埋め込みエディター ウィンドウは、ActiveX コントロールまたはそのドキュメントのビューとその他のアクティブなオブジェクトをホストする、インプレース アクティブ化エディター ウィンドウに、標準のドキュメント ビューをホストします。 詳細については、次を参照してください。[埋め込み簡](../extensibility/simplified-embedding.md)と[、インプレース アクティブ化](../extensibility/in-place-activation.md)です。  
  
5.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンドを処理するインターフェイスです。  
  
6.  次の手順を実行して、ドキュメントの永続化および外部ファイルの変更に応答を提供します。  
  
    1.  ファイルを保持するための実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>と<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>エディターのドキュメント データ オブジェクトにします。  
  
    2.  外部ファイルの変更に応答して、実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>エディターのドキュメント データ オブジェクトにします。  
  
        > [!NOTE]
        >  呼び出す`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>へのポインターを取得する`IVsFileChangeEx`です。  
  
7.  ソース コード コントロールとドキュメント編集イベントを調整します。 この操作を行うには、次の手順を実行します。  
  
    1.  ポインターを取得`IVsQueryEditQuerySave2`を呼び出して`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>です。  
  
    2.  最初の編集イベントが発生したときに呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッドです。  
  
         これには、ファイルをチェック アウトが既にチェック アウトされていない場合に、ユーザーが求められます。エラーを回避するための「ファイルがチェック アウトされていない」条件を処理することを確認します。  
  
    3.  同様に、ファイルを保存する前に呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>メソッドです。  
  
         このメソッドは、保存されていない場合、または最後に保存されてから変更されている場合は、ファイルを保存するユーザーに求めます。  
  
8.  有効にする、**プロパティ**ウィンドウ、エディターで選択したテキストのプロパティを表示します。 この操作を行うには、次の手順を実行します。  
  
    1.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>各時間テキスト選択が変更された、成功の実装で<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>です。  
  
    2.  呼び出す`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>サービスへのポインターを取得する<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>です。  
  
9. ドラッグし、エディターの間で項目をドロップできるようにする、**ツールボックス**、または異なる Microsoft Word などの外部エディター間で、**ツールボックス**です。 この操作を行うには、次の手順を実行します。  
  
    1.  実装`IDropTarget`エディター、エディターがドロップ ターゲットである IDE にアラートを生成します。  
  
    2.  実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 、エディターは有効にし、内の項目を無効にするために、ビュー上のインターフェイス、**ツールボックス**です。  
  
    3.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>を呼び出すと`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>へのポインターを取得するサービス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>インターフェイスです。  
  
         これにより、新しい項目を追加する VSPackage、**ツールボックス**です。  
  
10. エディターの他の省略可能な機能をするかどうかを決定します。  
  
    -   サポートするために、エディターの場合は、検索、およびコマンドに置き換えるを実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>です。  
  
    -   エディターでドキュメント出力ツール ウィンドウを使用する場合は、実装`IVsDocOutlineProvider`です。  
  
    -   ステータス バーをエディターで使用する場合は、実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>を呼び出すと`QueryService`の<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>へのポインターを取得する`IVsStatusBar`です。  
  
         たとえば、エディターが行を表示できます/列について、選択モード (ストリーム/ボックス) や挿入モード (挿入/上書き)。  
  
    -   サポートするエディターとして使用する場合、`Undo`コマンドを OLE undo マネージャーのモデルを使用するのにはお勧めします。 代わりに、エディターのハンドルを持つことができます、`Undo`直接コマンドします。  
  
11. レジストリ、VSPackage、メニューのエディター、およびその他の機能の Guid をなどの情報を作成します。  
  
     適切なエディターを登録する方法を示す、.rgs ファイルのスクリプトを配置することがコードの汎用例を次に示します。  
  
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
  
     これにより、F1 ヘルプとダイナミック ヘルプ ウィンドウ、エディター内の項目のサポートを提供することができます。 詳細については、次を参照してください。[する方法: エディターのコンテキストを提供](../extensibility/how-to-provide-context-for-editors.md)です。  
  
13. 実装することによって、エディターからのオートメーション オブジェクト モデルを公開、`IDispatch`インターフェイスです。  
  
     詳細については、次を参照してください。[オートメーション モデルに貢献している](../extensibility/internals/contributing-to-the-automation-model.md)です。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
-   IDE を呼び出すと、エディターのインスタンスが作成された、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドです。 エディターは、複数のビューをサポートしている場合`CreateEditorInstance`ドキュメントのデータとドキュメント ビュー オブジェクトの両方を作成します。 ドキュメント データ オブジェクトは、既に場合開くには、null でない`punkDocDataExisting`に値が渡される`IVsEditorFactory::CreateEditorInstance`です。 エディター ファクトリの実装に適切なインターフェイスのクエリを実行して、既存のドキュメント データ オブジェクトが互換性のあるかどうかを決定する必要があります。 詳細については、次を参照してください。[複数ドキュメントのビューをサポートする](../extensibility/supporting-multiple-document-views.md)です。  
  
-   簡略化した埋め込み方法を使用する場合は、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイスです。  
  
-   インプレース アクティブ化を使用する場合は、次のインターフェイスを実装します。  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  `IOleInPlaceComponent` OLE 2 メニューのマージを避けるためにインターフェイスを使用します。  
  
     `IOleCommandTarget`実装などのコマンドを処理**切り取り**、**コピー**、および**貼り付け**です。 実装するときに`IOleCommandTarget`、エディターに独自のコマンドのメニュー構造を定義する、独自の .vsct ファイルが必要かどうか、またはによって定義された標準のコマンドを実装することができるかどうか決定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 通常、エディターを使用して、IDE のメニューを拡張し、それぞれ独自のツールバーを定義します。 ただし、多くの場合は、エディター、IDE の標準的なコマンド セットを使用するだけでなく、独自の特定のコマンドを定義するために必要なです。 これを行うには、エディターは、標準のコマンドを使用し、.vsct ファイルで、新しいコマンド、コンテキスト メニューのトップレベルのメニューおよびツールバーを定義を宣言しなければなりません。 インプレース アクティブ化エディターを作成する場合、実装<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>し OLE 2 メニューのマージを使用する代わりに .vsct ファイルで、エディターのメニューとツールバーを定義します。  
  
-   Ui を増やし、メニュー コマンドを防ぐためには、新しいコマンドを開発する前に、IDE で既存のコマンドを使用する必要があります。 共有のコマンドは、SharedCmdDef.vsct および ShellCmdDef.vsct で定義されます。 既定の VisualStudioIntegration\Common\Inc サブディレクトリでこれらのファイルがインストールされている、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]インストールします。  
  
-   `ISelectionContainer`単一および複数の両方の選択内容を表すことができます。 選択した各オブジェクトは、`IDispatch`オブジェクト。  
  
-   IDE を実装する`IOleUndoManager`からアクセス可能なサービスとして、<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>またはオブジェクトをインスタンス化できる<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>です。 エディターが実装する、`IOleUndoUnit`各インターフェイス`Undo`アクション。  
  
-   2 つの場所があるカスタム エディターは、オートメーション オブジェクトを公開できます。  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>関連項目  
 [オートメーション モデルに貢献しています。](../extensibility/internals/contributing-to-the-automation-model.md)   
 [方法: エディターのコンテキストを指定](../extensibility/how-to-provide-context-for-editors.md)