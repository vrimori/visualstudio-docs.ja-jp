---
title: ソース管理構成の詳細 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55e2364ca096b5329369e51ccdadf07f191720e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753711"
---
# <a name="source-control-configuration-details"></a>ソース管理構成の詳細
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理を実装するために、プロジェクト システムやには、次のエディターを適切に構成する必要があります。  
  
-   変更された状態に遷移するアクセス許可を要求します。  
  
-   ファイルを保存するアクセス許可を要求します。  
  
-   追加、削除、またはプロジェクト内のファイルの名前を変更する許可を要求します。  
  
## <a name="request-permission-to-transition-to-changed-state"></a>変更された状態に遷移するアクセス許可を要求します。  
 プロジェクトまたはエディターを呼び出すことによって変更された (ダーティ) 状態に遷移するためのアクセス許可を要求する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>します。 実装する各エディター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>呼び出す必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>を返す前に、環境からドキュメントの変更の承認を得ると`True`の`M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`します。 プロジェクトでは、プロジェクト ファイルは、エディターでは基本的をその結果、そのファイルはテキスト エディターのようにプロジェクト ファイルの変更状態の追跡を実装するための同じの責任を持ちます。 環境は、ソリューションの変更の状態を処理しますが、任意のオブジェクトを参照していては格納されません、プロジェクト ファイルやその項目のように、ソリューションの変更の状態を処理する必要があります。 一般に、プロジェクトまたはエディターがアイテムの永続化を管理する場合、られます変更状態の追跡を実装する責任を負います。  
  
 応答、`IVsQueryEditQuerySave2::QueryEditFiles`を呼び出すには、環境は、次を実行できます。  
  
- ケース エディターまたはプロジェクトがいなければ、unchanged (クリーン) 状態を変更する呼び出しを拒否します。  
  
- ドキュメント データを再読み込みするかを示します。 プロジェクトの場合、環境はプロジェクトのデータを再読み込みは。 エディターは、使用したディスクからデータを再読み込みする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>実装します。 どちらの場合、データの再読み込み時、プロジェクトまたはエディターのコンテキストは変更できます。  
  
  複雑で困難なタスクに組み込む適切な`IVsQueryEditQuerySave2::QueryEditFiles`呼び出し、既存のコード ベースにします。 その結果、これらの呼び出しは、プロジェクトまたはエディターの作成時に統合する必要があります。  
  
## <a name="request-permission-to-save-a-file"></a>ファイルを保存するアクセス許可を要求します。  
 プロジェクトまたはエディターは、ファイルを保存して、前に呼び出す必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>します。 プロジェクト ファイルのこれらの呼び出しは、プロジェクト ファイルを保存するタイミングを認識しているソリューションによって自動的に完了します。 しない限り、これらの呼び出しを行うためのエディターは、エディターの実装の`IVsPersistDocData2`ヘルパー関数を使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>します。 エディターを実装する場合`IVsPersistDocData2`への呼び出し、この方法で`IVsQueryEditQuerySave2::QuerySaveFile`または`IVsQueryEditQuerySave2::QuerySaveFiles`が行われます。  
  
> [!NOTE]
>  必ずこれらの呼び出しを事前-これは、エディターが、[キャンセル] を受信できないときにします。  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>追加、削除、またはプロジェクト内のファイルの名前を変更する許可を要求します。  
 プロジェクトを追加、名前の変更、またはファイルまたはディレクトリを削除、前に呼び出す必要があります、適切な`IVsTrackProjectDocuments2::OnQuery*`環境からの許可を要求するメソッド。 アクセス許可が付与されるかどうか、プロジェクトが、操作を完了する必要があります、呼び出して、適切な`IVsTrackProjectDocuments2::OnAfter*`操作が完了した環境に通知するメソッド。 プロジェクトでのメソッドを呼び出す必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>のすべてのファイル (たとえば、特別なファイル) と親のファイルだけでなくインターフェイスです。 ファイルの呼び出しが必須ですには、ディレクトリの呼び出しは省略可能です。 かどうかは、プロジェクトには、ディレクトリ情報が、適切なを呼び出す必要がある<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>メソッドが、この情報がないかどうかは、環境では、ディレクトリ情報を推論します。  
  
 プロジェクトのメソッドを呼び出さないでください`IVsTrackProjectDocuments2`プロジェクトを開くまたは閉じる。 スタートアップ時に、この情報をリスナーで待機できる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>イベント必要な情報を検索するソリューションを反復処理します。 シャット ダウン時、この情報は必要ありません。 `IVsTrackProjectDocuments2` 提供されている場合は、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>します。  
  
 各追加、名前の変更、および削除アクションは、`OnQuery*`メソッドと`OnAfter*`メソッド。 呼び出す、`OnQuery*`を追加するためのアクセス許可を要求するメソッドの名前変更、またはファイルまたはディレクトリを削除します。 呼び出す、`OnAfter*`後に、プロジェクトの状態が新しい状態を反映し、ファイルまたはディレクトリが追加、名前の変更、または削除されました。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)

