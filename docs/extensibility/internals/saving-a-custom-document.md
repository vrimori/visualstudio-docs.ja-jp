---
title: 図面を保存するカスタム |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5425a1c35816fd85847915029e3b6f2da1ed75a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132549"
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