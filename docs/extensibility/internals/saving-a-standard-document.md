---
title: "図面を保存する標準的な |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73ef7f1b347dc2fdcfe2904ef19a2d52036d927e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="saving-a-standard-document"></a>標準的なドキュメントの保存
環境では、保存、名前を付けて保存、および [すべて保存] コマンドを処理します。 ユーザーが選択すると**保存**、**名前を付けて保存**、または**すべて保存**から、**ファイル**メニューまたはその結果、ソリューションを閉じる、 **Save All**、次の処理が行われます。  
  
 ![標準エディター](../../extensibility/internals/media/public.gif "パブリック")  
保存、名前を付けて保存、および処理を標準のエディターに対してすべて保存 コマンド  
  
 このプロセスは、次の手順の詳細を示します。  
  
1.  ときに、**保存**と**名前を付けて保存**コマンドが選択されている場合、環境を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービスのアクティブなドキュメント ウィンドウを特定して、どのような項目を保存するためです。 アクティブなドキュメント ウィンドウが判明すると、環境は、実行中のドキュメント テーブル内のドキュメントの階層のポインターとアイテム識別子 (itemID) を検索します。 詳細については、次を参照してください。[を実行しているドキュメント テーブル](../../extensibility/internals/running-document-table.md)です。  
  
     ときに、**すべて保存**コマンドが選択されている場合、環境情報を使用して、実行中のドキュメント テーブルに保存するすべての項目の一覧をコンパイルします。  
  
2.  ソリューションが受信すると、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼び出し、選択した項目のセットを反復処理 (によって公開されている複数の選択は、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービス)。  
  
3.  選択範囲内の各項目に、ソリューション ポインターを使用して階層を呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>メソッドを呼び出せば確認するかどうか、**保存**メニュー コマンドを有効にする必要があります。 1 つまたは複数の項目は、ダーティの場合、**保存**コマンドが有効になっています。 場合は、階層は、標準のエディターを使用して、し、クエリを実行する階層デリゲート ダーティ状態、エディターを呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>メソッドです。  
  
4.  各選択したアイテムでダーティである、ソリューション ポインターを使用して階層を呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>適切な階層のメソッドです。  
  
     標準のエディターを使用して、ドキュメントを編集する階層一般的なことです。 この例では、ドキュメント データ オブジェクトそのエディターをサポートする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>インターフェイスです。 受信した、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>メソッドの呼び出し、プロジェクトは、エディターを呼び出して、ドキュメントが保存されていることを知らせる必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>ドキュメント データ オブジェクトのメソッドです。 エディターが処理するための環境を許可することができます、**名前を付けて保存**ダイアログ ボックスで、呼び出すことによって`Query Service`の<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>インターフェイスです。 ポインターが返されます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイスです。 エディターを呼び出す必要がありますし、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>メソッド、エディターにポインターを渡す<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>の実装、`pPersistFile`パラメーター。 環境は、保存操作を実行し、提供、**名前を付けて保存**エディターのダイアログ ボックス。 環境し返信をエディターに<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>です。  
  
5.  場合は、ユーザーが無題のドキュメント (つまり、まだ保存されていないドキュメント) を保存しようとして、し、名前を付けて保存コマンドは実際に実行されます。  
  
6.  名前を付けて保存 コマンドで、環境を付けて保存 ダイアログ ボックス、ファイル名をユーザーに通知が表示されます。  
  
     ファイルの名前を変更したかどうかは、階層に対しては責任を呼び出すことによって、キャッシュされた情報を更新、ドキュメント フレームの<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument)。  
  
 場合、**名前を付けて保存**コマンドは、ドキュメントの場所を移動し、階層が機密性の高いドキュメントの場所を階層は別の階層に、開いているドキュメント ウィンドウの所有権を渡すを担当します。 たとえばは、プロジェクト ファイルが内部または外部ファイル (その他のファイル) で、プロジェクトに関連しているかどうかを追跡する場合に発生します。 次の手順を使用すると、その他のファイル プロジェクトにファイルの所有権を変更できます。  
  
## <a name="changing-file-ownership"></a>ファイルの所有権を変更します。  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>その他のファイル プロジェクトにファイルの所有権を変更するには  
  
1.  サービスのクエリ、<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>インターフェイスです。  
  
     ポインター<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>が返されます。  
  
2.  呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`、 `punkWindowFrame`) ドキュメントを新しい階層に転送する方法です。 名前を付けて保存コマンドを実行する階層では、このメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [プロジェクト項目のオープンと保存](../../extensibility/internals/opening-and-saving-project-items.md)