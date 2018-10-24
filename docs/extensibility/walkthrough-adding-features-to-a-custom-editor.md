---
title: 'チュートリアル: カスタム エディターの機能の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7062f44fe119858e579a53325deca0ea04b46475
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873020"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>チュートリアル: カスタム エディターへの機能を追加します。
カスタム エディターを作成した後より多くの機能を追加できます。  
  
## <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage のエディターを作成するには  
  
1.  カスタム エディターを作成するには、Visual Studio パッケージ プロジェクト テンプレートを使用します。  
  
     詳細については、次を参照してください。[チュートリアル: カスタム エディターを作成する](../extensibility/walkthrough-creating-a-custom-editor.md)します。  
  
2.  エディター ビューを 1 つまたは複数のビューをサポートするかどうかを決定します。  
  
     サポートしている、**新しいウィンドウ**コマンド、またはフォーム ビューとコード ビューには、個別のドキュメント データ オブジェクトとドキュメント ビュー オブジェクトが必要です。 1 つのビューのみをサポートするエディターで、ドキュメント データ オブジェクトと、ドキュメント ビュー オブジェクトを同じオブジェクトで実装することができます。  
  
     複数のビューの例は、次を参照してください。[ドキュメントの複数のビューをサポートして](../extensibility/supporting-multiple-document-views.md)します。  
  
3.  設定することで、エディター ファクトリの実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイス。  
  
     詳細については、次を参照してください。[エディター ファクトリ](../extensibility/editor-factories.md)します。  
  
4.  インプレース アクティブ化を使用するエディターで、または、簡略化された埋め込みドキュメント ビュー オブジェクト ウィンドウを管理するかどうかを決定します。  
  
     ActiveX コントロールまたはそのドキュメントのビューとその他のアクティブなオブジェクトをホストする、インプレース アクティブ化エディター ウィンドウ中に、簡略化された埋め込みエディター ウィンドウは、標準のドキュメント ビューをホストします。 詳細については、次を参照してください。[簡略化された埋め込み](../extensibility/simplified-embedding.md)と[インプレース アクティブ化](../extensibility/in-place-activation.md)します。  
  
5.  実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンドを処理するインターフェイス。  
  
6.  ドキュメントの永続化と外部ファイルの変更に応答を提供します。  
  
    1.  ファイルを永続化する実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>と<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>エディターのドキュメント データ オブジェクトにします。  
  
    2.  外部ファイルの変更に応答すると、実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>エディターのドキュメント データ オブジェクトにします。  
  
        > [!NOTE]
        >  呼び出す`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>へのポインターを取得する`IVsFileChangeEx`します。  
  
7.  ソース コード コントロールとドキュメント編集のイベントを調整します。 この場合は、以下の手順に従ってください。  
  
    1.  ポインターを取得`IVsQueryEditQuerySave2`呼び出して`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>します。  
  
    2.  編集の最初のイベントが発生したときに呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>メソッド。  
  
         このメソッドは、ユーザー、ファイルをチェック アウトされていない場合は、チェック アウトを求めます。エラーを回避するための「ファイルがチェック アウトされていない」条件を処理することを確認します。  
  
    3.  同様に、ファイルを保存する前に呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>メソッド。  
  
         このメソッドは、保存されていない場合、または最後に保存してから変更されている場合は、ファイルを保存するユーザーに求めます。  
  
8.  有効にする、**プロパティ**ウィンドウ、エディターで選択したテキストのプロパティを表示します。 この場合は、以下の手順に従ってください。  
  
    1.  呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>各時間テキスト選択変更、受け渡しの実装で<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>します。  
  
    2.  呼び出す`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>サービスへのポインターを取得する<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>します。  
  
9. ユーザーがドラッグ アンド ドロップ、エディターの間でアイテムを有効にして、**ツールボックス**、または外部のエディター (Microsoft Word の場合) などの間、**ツールボックス**します。 この場合は、以下の手順に従ってください。  
  
    1.  実装`IDropTarget`エディター、エディターがドロップ先である IDE のアラートを生成します。  
  
    2.  実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 、ビュー、エディターが有効にするなどの項目を無効にするためのインターフェイス、**ツールボックス**します。  
  
    3.  実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>を呼び出すと`QueryService`で<xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>へのポインターを取得するサービス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>インターフェイス。  
  
         次の手順は、新しい項目を追加するために VSPackage を有効にする、**ツールボックス**します。  
  
10. エディターの他の省略可能な機能をするかどうかを決定します。  
  
    -   サポートするために、エディターの場合は、検索、およびコマンドを置き換える実装<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>します。  
  
    -   エディターでドキュメント出力ツール ウィンドウを使用する場合は、実装`IVsDocOutlineProvider`します。  
  
    -   エディターでステータス バーを使用する場合は、実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>を呼び出すと`QueryService`の<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>へのポインターを取得する`IVsStatusBar`します。  
  
         たとえば、エディターが行を表示できます/列の情報、選択モード (ストリーミング/ボックス) と挿入モード (挿入/overstrike)。  
  
    -   サポートするために、エディターの場合、`Undo`コマンドを OLE 元に戻すマネージャー モデルの使用はお勧めします。 代わりに、エディターのハンドルができる、`Undo`直接コマンドします。  
  
11. レジストリを VSPackage、メニューのエディター、およびその他の機能の Guid を含む情報を作成します。  
  
     記述するコードの汎用例を次に、 *.rgs*ファイルのスクリプト エディターが正しく登録する方法を示します。  
  
    ```csharp  
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
  
     F1 ヘルプおよびダイナミック ヘルプ ウィンドウは、エディター内の項目のサポートを提供することができます。 詳細については、次を参照してください。[方法: エディターのコンテキストを提供](../extensibility/how-to-provide-context-for-editors.md)します。  
  
13. 実装することで、エディターからのオートメーション オブジェクト モデルを公開、`IDispatch`インターフェイス。  
  
     詳細については、「 [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md)」を参照してください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
- IDE を呼び出すと、エディター インスタンスが作成された、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド。 エディターは、複数のビューをサポートしている場合`CreateEditorInstance`ドキュメント データとドキュメント ビュー オブジェクトの両方を作成します。 ドキュメント データ オブジェクトが既にある場合を開く、null でない`punkDocDataExisting`に値が渡される`IVsEditorFactory::CreateEditorInstance`します。 エディター ファクトリの実装に適切なインターフェイスを照会して、既存のドキュメント データ オブジェクトが互換性のあるかどうかを判断する必要があります。 詳細については、次を参照してください。 [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md)します。  
  
- 簡略化された埋め込み方法を使用する場合は、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイス。  
  
- インプレース アクティブ化を使用する場合は、次のインターフェイスを実装します。  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
  > [!NOTE]
  >  `IOleInPlaceComponent`インターフェイスは、OLE 2 メニューのマージを回避するために使用されます。  
  
   `IOleCommandTarget`の実装などのコマンドは処理**切り取り**、**コピー**、および**貼り付け**します。 実装する場合`IOleCommandTarget`、エディターが必要独自かどうかを決定 *.vsct*コマンド メニュー構造を定義するファイルで定義されている標準のコマンドを実装している場合、または[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 通常、エディター、IDE のメニューを拡張し、使用、独自のツールバーを定義します。、 ただし、エディター、IDE の標準のコマンド セットを使用するだけでなく、独自の特定のコマンドを定義する必要があります。 エディターを使用して標準のコマンドを宣言し、新しいコマンド、コンテキスト メニューのトップレベルのメニューおよびツールバーを定義、 *.vsct*ファイル。 インプレース アクティブ化エディターを作成する場合は、実装<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>のエディターにメニューおよびツールバーを定義し、 *.vsct* OLE 2 メニューのマージを使用してではなくファイル。  
  
- UI で大将メニュー コマンドを防ぐためには、新しいコマンドを開発する前に、IDE で既存のコマンドを使用する必要があります。 共有コマンドが定義されている*SharedCmdDef.vsct*と*ShellCmdDef.vsct*します。 既定の VisualStudioIntegration\Common\Inc サブディレクトリでこれらのファイルがインストールされている、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]インストールします。  
  
- `ISelectionContainer` オプションの 1 つまたは複数の両方を表現できます。 選択した各オブジェクトは、`IDispatch`オブジェクト。  
  
- IDE を実装して`IOleUndoManager`からアクセスできるサービスとして、<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>またはを通じてインスタンス化できるオブジェクトとして<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>します。 エディターの実装、`IOleUndoUnit`各インターフェイス`Undo`アクション。  
  
- 2 つの場所があるカスタム エディターは、オートメーション オブジェクトを公開できます。  
  
  -   `Document.Object`  
  
  -   `Window.Object`  
  
## <a name="see-also"></a>関連項目  
 [オートメーション モデルに貢献します。](../extensibility/internals/contributing-to-the-automation-model.md)   
 [方法: エディターのコンテキストを提供](../extensibility/how-to-provide-context-for-editors.md)