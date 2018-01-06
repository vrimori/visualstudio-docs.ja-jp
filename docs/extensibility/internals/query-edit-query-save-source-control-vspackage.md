---
title: "保存 (ソース コントロール VSPackage) クエリの編集を照会 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e3428e51dda2f8cc8410b6ac67f5779f7c2300ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="query-edit-query-save-source-control-vspackage"></a>クエリ (ソース コントロール VSPackage) 保存クエリの編集
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]エディターには、クエリの編集のクエリを保存 (QEQS) イベントをブロードキャストできます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース コントロールのスタブを QEQS イベントを受け取ることができるように、QEQS サービスを実装します。 これらのイベントは、現在アクティブなソース管理 VSPackage にし、委任されます。 VSPackage の実装、アクティブなソース管理、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>とそのメソッドです。 メソッド、`IVsQueryEditQuerySave2`文書を編集すると、最初に、ドキュメントを保存する直前に直前に、インターフェイスが通常呼び出されます。  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave イベント  
 ソース管理 VSPackage は、実装することによって QEQS イベントを処理する必要があります、`IVsQueryEditQuerySave2`インターフェイスと、必要なメソッドです。 VSPackage を実装する必要がありますには、少なくとも 2 つの方法の簡単な説明を次に示します。 実際の実装は、ソース管理モデルのロジックに従ってする必要があります。  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles メソッド  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>プロジェクトやエディターがファイルを変更するときに呼び出されます。 理想的には、このメソッドが呼び出されます*する前に*ファイルが変更され、ファイルを保存します。 呼び出されると、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドは、与えられたファイル ソース管理下にあるかどうか、チェック アウトすべきかどうかおよび再度かどうかをチェックします。 状況が原因でファイルが編集されている場合、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドが、編集をキャンセルする呼び出し元のプログラムに指示します。 呼び出し元が呼び出しモードを指定することもできます。 「サイレント」モードでは、このメソッドは、表示する UI は行われません場合にのみにアクションを受け取ります。 UI を回避できない場合は、問題を示すためにフラグを返す必要があります。  
  
 トランザクション的に、メソッドを動作します。1 つのファイルの編集がキャンセルされた場合は、すべてのファイルの編集が取り消されました。 逆に、編集が許可された場合、すべてのファイルのことができます。 このメソッドは、ファイルの指定されたセットの 1 回の編集を許可している場合常に同じファイルのセットの後続の呼び出しでを編集することが必要があります。 編集する許可ループまで、ファイルが閉じ、保存、および再読み込みします。それらの属性 (プロパティ) は、次の変更; までまたは、ソース管理パッケージが変更されるまでです。 実装する際に考慮する場合、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドは特別なファイル、複数のファイルが含まれて、ユーザー、およびメモリ内編集をキャンセルします。  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles メソッド  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>プロジェクトやエディターが一連のファイルを保存する必要があるときに呼び出されます。 呼び出されると、`IVsQueryEditQuerySave2::QuerySaveFiles`メソッドは、指定されたファイルは読み取り専用の場合、およびソース管理の対象であるかどうかをチェックします。 ファイルは、チェック アウトする必要があります、呼び出しはソース管理パッケージを委任します。 状況によって、ファイルが保存されているようにする場合、`IVsQueryEditQuerySave2::QuerySaveFiles`メソッドは、保存をキャンセルするエディターを伝える必要があります。 同様、`IVsQueryEditQuerySave2::QueryEditFiles`メソッド、呼び出し元が呼び出しモードを指定することができます。 「サイレント」モードでは、このメソッドは、表示する UI は行われません場合にのみにアクションを受け取ります。 UI を回避できない場合は、問題を示すためにフラグを返す必要があります。  
  
 このメソッドは、トランザクション的に動作する必要があります。つまり、1 つのファイルの保存が取り消されると場合のすべてのファイルの保存が取り消されました。 逆に、保存が許可された場合、すべてのファイルの許可する必要があります。 同様、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドを実装する際に考慮する場合、`IVsQueryEditQuerySave2::QuerySaveFiles`メソッドは特別なファイル、複数のファイルが含まれて、ユーザー、およびメモリ内編集をキャンセルします。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>