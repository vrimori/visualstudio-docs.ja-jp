---
title: 標準ドキュメントの保存 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b7f9b650c0d355d83137e302fc716f343d47b57d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868892"
---
# <a name="saving-a-standard-document"></a>標準ドキュメントの保存
環境では、保存、名前を付けて保存および すべて保存コマンドを処理します。 ユーザーが選択すると**保存**、**名前を付けて保存**、または**すべて保存**から、**ファイル**メニューまたはその結果、ソリューションを閉じる、 **すべて保存**、次の処理が行われます。  
  
 ![標準エディター](../../extensibility/internals/media/public.gif "パブリック")  
保存、名前を付けて保存および処理の標準エディターのすべて保存 コマンド  
  
 このプロセスの詳細については、次の手順。  
  
1. ときに、**保存**と**名前を付けて保存**コマンドが選択されている場合、環境を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービスのアクティブなドキュメント ウィンドウを確認して、どのような項目を保存するためです。 アクティブなドキュメント ウィンドウがわかったら、環境は、実行中の document テーブル内のドキュメントの階層のポインターと項目の識別子 (itemID) を検索します。 詳細については、次を参照してください。[を実行しているドキュメント テーブル](../../extensibility/internals/running-document-table.md)します。  
  
    ときに、**すべて保存**コマンドが選択されている場合、環境では、実行中の document テーブルの情報を使用して保存するすべての項目の一覧をコンパイルします。  
  
2. ソリューションが受信すると、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼び出し、選択した項目のセットを反復処理 (によって公開されている複数の選択は、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービス)。  
  
3. ソリューションの選択範囲の各項目を呼び出す階層ポインターを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>メソッドを決定するかどうか、**保存**メニュー コマンドを有効にする必要があります。 1 つまたは複数の項目がダーティな場合は、**保存**コマンドが有効にします。 階層は、標準のエディターを使用している場合のクエリを実行する階層デリゲート ダーティ状態、エディターを呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>メソッド。  
  
4. ソリューションがダーティ選択項目ごとに呼び出す階層ポインターを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>メソッドを適切な階層。  
  
    標準のエディターを使用して、ドキュメントを編集する階層が一般的です。 そのエディターがサポートする必要がありますにドキュメントのデータがここでは、オブジェクト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>インターフェイス。 受信すると、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>メソッドの呼び出し、呼び出すことによって、ドキュメントが保存されているエディターがプロジェクトに知らせる必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>ドキュメント データ オブジェクトのメソッド。 エディターが処理するために環境を許可することができます、**名前を付けて保存** ダイアログ ボックスで、呼び出して`Query Service`の<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>インターフェイス。 ポインターが返されます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>インターフェイス。 エディターを呼び出す必要がありますし、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>にエディターのポインターを渡すメソッド<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>の実装、`pPersistFile`パラメーター。 環境は、保存操作を実行し、提供、**付けて**エディターのダイアログ ボックス。 エディターを環境をバックアップし呼び出します<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>します。  
  
5. ユーザーが無題のドキュメント (つまり、以前に保存されていないドキュメント) を保存しようとして、し、名前を付けて保存コマンドは実際に実行します。  
  
6. 名前を付けて保存コマンドは、環境には、名前を付けて保存 ダイアログ ボックス、ファイル名をユーザーに確認が表示されます。  
  
    ファイルの名前を変更したかどうかは、階層は、呼び出すことによって、キャッシュされた情報をドキュメント フレームの更新に対して責任<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument)。  
  
   場合、**付けて**コマンドは、ドキュメントの場所を移動し、階層が機密性の高いドキュメントの場所を階層が別の階層に、開いているドキュメント ウィンドウの所有権を渡す責任を負います。 たとえば、これは、プロジェクト ファイルが内部または外部ファイル (その他のファイル) で、プロジェクトに関連するかどうかを追跡する場合に発生します。 次の手順を使用すると、その他のファイル プロジェクトにファイルの所有権を変更できます。  
  
## <a name="changing-file-ownership"></a>ファイルの所有権を変更します。  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>その他のファイル プロジェクトにファイルの所有権を変更するには  
  
1.  サービスにクエリ、<xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>インターフェイス。  
  
     ポインター<xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>が返されます。  
  
2.  呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`、 `punkWindowFrame`) ドキュメントを新しい階層に転送する方法。 名前を付けて保存コマンドを実行する階層では、このメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [プロジェクト項目のオープンと保存](../../extensibility/internals/opening-and-saving-project-items.md)