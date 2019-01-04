---
title: クエリの編集とクエリの保存 (ソース管理 VSPackage) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3129fe384dc434f10024336a3e53864babcd5eb4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917411"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>クエリの編集とクエリの保存 (ソース管理 VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] エディターでは、クエリ編集クエリの保存 (QEQS) イベントをブロードキャストできます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] QEQS イベントの受信者をあるように、ソース コントロールのスタブは、QEQS サービスを実装します。 これらのイベントは、現在アクティブなソース管理 VSPackage に委任しされます。 VSPackage の実装、アクティブなソース コントロール、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>とそのメソッド。 メソッド、`IVsQueryEditQuerySave2`文書を編集して、文書を保存する直前に、最初にする直前に、インターフェイスは通常と呼ばれます。  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave イベント  
 ソース管理 VSPackage は、実装することによって、QEQS イベントを処理する必要があります、`IVsQueryEditQuerySave2`インターフェイスと、必要なメソッドです。 少なくとも、VSPackage を実装する必要がある 2 つの方法の簡単な説明を次に示します。 ソース管理モデルのロジックに従って実際の実装があります。  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles メソッド  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>任意のプロジェクトまたはエディターがファイルを変更するときに呼び出されます。 理想的には、このメソッドが呼び出されます*する前に*ファイルが変更され、ファイルが保存されます。 呼び出されると、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドかどうか、指定されたファイルは、ソース管理下、かどうかがチェック アウトする必要があり、再読み込みすることができるかどうかを確認します。 状況が原因で、ファイルが編集されている場合、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドを編集をキャンセルする呼び出し元プログラムに指示します。 呼び出し元が、呼び出しモードを指定することもできます。 「サイレント」モードでは、このメソッドは、任意の UI に表示されるは実行されない場合にのみアクションを受け取ります。 UI が避けられない場合は、問題を示すフラグを返す必要があります。  
  
 メソッドのトランザクション的に動作します。1 つのファイルの編集が取り消された場合は、すべてのファイルの編集が取り消されました。 逆に、編集が許可されている場合、すべてのファイルのことができます。 このメソッドは、特定の一連のファイルの 1 回の編集を許可している場合、同じ一連のファイルの後続の呼び出しで編集ことを常に許可する必要があります。 許可する編集ループは、ファイルが閉じられた、保存、および再読み込みするまで続きますそれらの属性 (プロパティ) を変更; までまたは、ソース管理パッケージが変更されるまでです。 実装で考慮すべきケース、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドが特別なファイル、複数のファイルが含まれて、ユーザー、およびメモリ内の編集をキャンセルします。  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles メソッド  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>任意のプロジェクトまたはエディターは、一連のファイルを保存する必要があるときに呼び出されます。 呼び出されると、`IVsQueryEditQuerySave2::QuerySaveFiles`メソッドは、特定のファイルは読み取り専用の場合、ソース管理の対象であるかどうかを確認します。 ファイルは、チェック アウトする場合に、呼び出しは、ソース管理パッケージに委任されます。 状況が原因で、ファイルが保存されている場合、`IVsQueryEditQuerySave2::QuerySaveFiles`メソッドは、保存を取り消すをエディターに通知する必要があります。 同様、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドを呼び出し元が、呼び出しモードを指定することができます。 「サイレント」モードでは、このメソッドは、任意の UI に表示されるは実行されない場合にのみアクションを受け取ります。 UI が避けられない場合は、問題を示すフラグを返す必要があります。  
  
 このメソッドは、トランザクション的に動作する必要があります。1 つのファイルの保存が取り消された場合は、すべてのファイルの保存が取り消されました。 逆に、保存が許可されている場合、すべてのファイルを許可する必要があります。 同様、`IVsQueryEditQuerySave2::QueryEditFiles`メソッドは、実装で考慮すべきケース、`IVsQueryEditQuerySave2::QuerySaveFiles`メソッドが特別なファイル、複数のファイルが含まれて、ユーザー、およびメモリ内の編集をキャンセルします。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>