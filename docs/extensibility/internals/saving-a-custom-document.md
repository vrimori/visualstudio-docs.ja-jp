---
title: "図面を保存するカスタム |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3cd6f5f45736a7b2578bc9df80a8472d3b50c3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="saving-a-custom-document"></a>カスタム ドキュメントの保存
環境ハンドル、**保存**、**名前を付けて保存**、および**すべて保存**コマンド。 ユーザーがクリックしたとき**保存**、**名前を付けて保存**、**すべてを保存または**上、**ファイル**メニューまたはすべてを保存、次の結果として得られる、ソリューションを閉じる処理が行われます。  
  
 ![カスタマー エディター保存](../../extensibility/internals/media/private.gif "プライベート")  
保存、名前を付けて保存、および処理のカスタム エディターをすべて保存 コマンド  
  
 このプロセスは、次の手順の詳細を示します。  
  
1.  **保存**と**名前を付けて保存**コマンド、環境を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービスのアクティブなドキュメント ウィンドウを特定して、どのような項目を保存するためです。 アクティブなドキュメント ウィンドウが判明すると、環境は、実行中のドキュメント テーブル内のドキュメントの階層のポインターとアイテム識別子 (itemID) を検索します。 詳細については、次を参照してください。[を実行しているドキュメント テーブル](../../extensibility/internals/running-document-table.md)です。  
  
     すべて保存 コマンドの環境情報を使用して実行中のドキュメント テーブルで保存するすべての項目の一覧をコンパイルします。  
  
2.  ソリューションが受信すると、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>呼び出し、選択した項目のセットを反復処理 (によって公開されている複数の選択は、<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>サービス)。  
  
3.  選択範囲内の各項目に、ソリューション ポインターを使用して階層を呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>  メニューの 保存 コマンドを有効にするかどうかを調べます。 1 つまたは複数の項目がダーティの場合は、[保存] コマンドは有効です。 場合は、階層は、標準のエディターを使用して、し、クエリを実行する階層デリゲート ダーティ状態、エディターを呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>メソッドです。  
  
4.  各選択したアイテムでダーティである、ソリューション ポインターを使用して階層を呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>適切な階層のメソッドです。  
  
     カスタムのエディターの場合は、ドキュメント データ オブジェクトと、プロジェクト間の通信はプライベートです。 したがって、任意の特殊な永続化に関する注意事項は、これら 2 つのオブジェクト間で処理されます。  
  
    > [!NOTE]
    >  独自の永続化を実装する場合を呼び出すことを確認する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>時間を節約するメソッド。 このメソッドは、ファイルを保存しても安全であるかどうかを確認するチェック (たとえば、ファイルは読み取り専用)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [プロジェクト項目のオープンと保存](../../extensibility/internals/opening-and-saving-project-items.md)