---
title: "ソース コントロールの構成の詳細 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2f8a2cc2f1c13c46b3ac4838d95ce588d0461347
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-configuration-details"></a>ソース コントロールの構成の詳細
ソース管理を実装するためには、エディターは、次に、プロジェクト システムを適切に構成する必要があります。  
  
-   変更された状態に遷移するアクセス許可を要求します。  
  
-   ファイルを保存するアクセス許可を要求します。  
  
-   追加、削除、またはプロジェクト内のファイルの名前を変更するアクセス許可を要求します。  
  
## <a name="request-permission-to-transition-to-changed-state"></a>変更された状態に遷移するアクセス許可を要求します。  
 プロジェクトまたはエディターは、呼び出すことによって変更 (ダーティ) 状態に遷移するアクセス許可を要求する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>です。 実装する各エディター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>呼び出す必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>を返す前に、環境からのドキュメントの変更に承認を得ると`True`の`M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`します。 プロジェクトは、プロジェクト ファイルをエディターでは基本的には、その結果、担当しています、同じテキスト エディターはそのファイルのようにプロジェクト ファイルの状態変更の追跡を実装するためです。 環境が、このソリューションの変更後の状態を処理しますが、任意のオブジェクトを参照しますが、格納しません、プロジェクト ファイルまたはその項目と同様に、ソリューションの変更の状態を処理する必要があります。 一般に、プロジェクトまたはエディターがアイテムを持続性の管理を担当する場合、なります状態変更の追跡の実装を担当します。  
  
 応答、`IVsQueryEditQuerySave2::QueryEditFiles`を呼び出すには、環境は、次を実行できます。  
  
-   (クリーン) 状態は変更されないまま必要がありますケース エディターまたはプロジェクトを変更する呼び出しを拒否します。  
  
-   ドキュメント データを再読み込みすることを示してください。 プロジェクトの場合、環境は、プロジェクトのデータを再読み込みします。 エディターが使用したディスクからデータを再読み込みする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>実装します。 いずれの場合、データが再読み込みされるときに、プロジェクトまたはエディターでは、コンテキストは変更できます。  
  
 適切な英語複雑かつタスク`IVsQueryEditQuerySave2::QueryEditFiles`既存のコード ベースへの呼び出しです。 その結果、これらの呼び出しは、プロジェクトまたはエディターの作成中に統合する必要があります。  
  
## <a name="request-permission-to-save-a-file"></a>ファイルを保存するアクセス許可を要求します。  
 プロジェクトまたはエディターは、ファイルを保存して、前に呼び出す必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>です。 プロジェクト ファイルのこれらの呼び出しがあり、プロジェクト ファイルを保存するときに認識しているソリューションによって自動的に完了します。 エディターは、しない限り、これらの呼び出しを行うためのエディターの実装`IVsPersistDocData2`ヘルパー関数を使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>です。 エディターを実装する場合`IVsPersistDocData2`し、このようにへの呼び出しで`IVsQueryEditQuerySave2::QuerySaveFile`または`IVsQueryEditQuerySave2::QuerySaveFiles`が行われます。  
  
> [!NOTE]
>  必ずこれらの呼び出しをプリエンプティブ: つまり、エディターは、[キャンセル] を受信できない場合にします。  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>追加、削除、またはプロジェクト内のファイルの名前を変更するアクセス許可を要求します。  
 プロジェクトは追加、名前の変更、またはファイルまたはディレクトリを削除することができます、前に呼び出す必要があります、適切な`IVsTrackProjectDocuments2::OnQuery*`環境からの許可を要求するメソッド。 アクセス許可が付与されるかどうか、プロジェクトの操作を完了して、適切なを呼び出す必要があります`IVsTrackProjectDocuments2::OnAfter*`環境、操作が完了したことを通知するメソッド。 プロジェクトのメソッドを呼び出す必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>すべてのファイル (たとえば、特別なファイル) と親のファイルだけでなくインターフェイスです。 ファイルの呼び出しは必須ですが、ディレクトリの呼び出しは省略可能です。 かどうかは、ディレクトリ情報がプロジェクトに、適切なに呼び出す必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>メソッドが、この情報がないかどうかは、環境は、ディレクトリ情報が推測されます。  
  
 プロジェクトがのメソッドを呼び出す必要がありますいない`IVsTrackProjectDocuments2`プロジェクトを開くまたは閉じる。 スタートアップ時に、この情報をリスナーで待機できる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>イベントで必要な情報を検索するようにソリューションを反復処理します。 シャット ダウン時、この情報は必要ありません。 `IVsTrackProjectDocuments2`提供される、<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>です。  
  
 各追加、名前変更、および削除アクションがある、`OnQuery*`メソッドおよび`OnAfter*`メソッドです。 呼び出す、`OnQuery*`を追加する許可を得るためのメソッドは、名前変更、または、ファイルまたはディレクトリを削除します。 呼び出す、`OnAfter*`プロジェクトの状態が新しい状態を反映し、ファイルまたはディレクトリが追加、変更、または削除された後にします。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)