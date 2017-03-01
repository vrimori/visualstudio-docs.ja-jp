---
title: "ドキュメント ロック所有者の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a78ee74a210f544ad4f9d97a9d2457bdf9d70988
ms.lasthandoff: 02/22/2017

---
# <a name="document-lock-holder-management"></a>ドキュメントのロック所有者の管理
実行しているドキュメント テーブル (RDT) は、開いているドキュメントとある編集ロックのカウントを保持します。 プログラムを使用してユーザーがドキュメント ウィンドウで、開いているドキュメントが表示されることがなく、バック グラウンドで編集の場合は、ドキュメント、RDT の編集ロックを配置できます。 この機能は、グラフィカル ユーザー インターフェイスでの複数のファイルを変更する、デザイナーでよく使用されます。  
  
## <a name="document-lock-holder-scenarios"></a>ドキュメントのロック所有者のシナリオ  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>ファイル"a"がファイルへの依存"b"  
 ファイルの種類の標準エディター"A"を実装する場合を考えてみましょう"a"、および各ファイルの種類への参照 (またはへの依存度)、"a"が"b"の種類のファイルです。 標準エディター"B"では、ファイルの種類"b"が存在します。 エディターの"A"は、ファイルを開いた場合に、"a"は、対応するファイルの"b"への参照を取得します。 ファイル"b"が表示されませんが、"A"のエディターで変更できます。 エディター"A"から取得するファイルのドキュメント データへの参照を"b"、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>メソッドも、"b"のファイルの編集ロックを保持しています</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>。 呼び出して、ファイル"b"でのカウントをファイル"b"の編集のロックをデクリメントするを変更するかエディター"A"が完了したら、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>。 呼び出した場合は、この手順を省略することができます、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>、パラメーターを持つメソッド`dwRDTLockType`<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS></xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>設定</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>。  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>ファイル"b"が別のエディターによって開かれて  
 エディター"A"は、それを開こうとすると、エディターの"B"、"b"ファイルが既に開いて、ことは、2 つの独立したシナリオを処理するにがあります。  
  
-   ファイル"b"が互換性のあるエディターで開いている場合は、エディター"A"ドキュメント編集のロックを使用してファイルの"b"の登録が必要、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>。 ドキュメントの登録を解除では、ロックを使用して編集、エディターの"A"には、変更するファイル"b"が完了したら、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>。  
  
-   ファイル"b"が互換性のない方法で開いている場合は、させてファイル"b"を実行しようとした開くエディターの"A"失敗するかは、"A"は、部分的に開かれ、適切なエラー メッセージが表示エディターに関連付けられているビューをさせることができます。 互換性のないエディターでファイル"b"を閉じるし、"a"を使用してファイルを再度開きますをユーザーに指示するエラー メッセージが必要があります"A"のエディターです。 実装することも、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>"b"のファイルを閉じるには、互換性のないエディターで開いているユーザー入力を求める</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>。 ユーザーが"b"、ファイルを開くファイルを閉じるの"a"エディター"A"は通常どおり続行されます。  
  
## <a name="additional-document-edit-lock-considerations"></a>追加のドキュメントの編集のロックに関する考慮事項  
 エディターの"A"が"B"をエディターには、ドキュメントも保持している場合よりも、"b"のファイルのロックを編集、ドキュメントのある唯一のエディターで編集ファイル"b"のロックの場合は、異なる動作を取得します。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、**クラス デザイナー**関連付けられたコード ファイルで編集ロックを保持しないビジュアルなデザイナーの例に示します。 ユーザーは、クラス図をデザイン ビューで開くし、関連付けられたコード ファイルを同時に、開く、ユーザーは、コード ファイルは変更が、変更を保存しない場合は、変更は失われますにクラス ダイアグラム (.cd) ファイルにします。 場合、**クラス デザイナー**が専用のドキュメントでは、コード ファイルのロックを編集するユーザーは求められませんコード ファイルを閉じるときに、変更を保存します。 IDE がユーザーの終了後にのみ、変更を保存するユーザーを要求、**クラス デザイナー**します。 両方のファイルには、保存された変更が反映されます。 どちらの場合、**クラス デザイナー**コード ファイル エディターでは、コード ファイルまたはフォームを閉じるときに保存するよう求められますし、コード ファイルにドキュメント編集のロックを保持します。 この時点で保存された変更は、フォームとコード ファイルの両方に反映されます。 クラス ダイアグラムでの詳細については、次を参照してください。[クラス ダイアグラム (クラス デザイナー) の使用](../ide/working-with-class-diagrams-class-designer.md)します。  
  
 エディター以外のドキュメントに対して編集ロックを配置する場合は、必要がありますを実装することに注意してください、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>。  
  
 何度も UI デザイナー コード ファイルをプログラムで変更するは、1 つ以上のファイルに変更を加えます。 このような場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>の&1; つまたは複数のドキュメントの保存を処理するメソッド、**を次の項目への変更を保存するか** ダイアログ ボックス。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> 。  
  
## <a name="see-also"></a>関連項目  
 [実行中のドキュメント テーブル](../extensibility/internals/running-document-table.md)   
 [永続化と実行中の Document テーブル](../extensibility/internals/persistence-and-the-running-document-table.md)
