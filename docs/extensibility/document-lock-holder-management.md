---
title: "ドキュメントのロック所有者の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4bd487bd3f5a6978af9f79eb9e0a00866b5df52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="document-lock-holder-management"></a>ドキュメントのロック所有者の管理
実行しているドキュメント テーブル (RDT) は、開いているドキュメントとがあるすべての編集ロックの数を保持します。 編集しているときにプログラムでバック グラウンドでユーザーがドキュメント ウィンドウで開いているドキュメントが表示されることがなく、RDT 内のドキュメントに対する編集ロックを配置できます。 この機能はグラフィカル ユーザー インターフェイスからの複数のファイルを変更するデザイナーでよく使用されます。  
  
## <a name="document-lock-holder-scenarios"></a>ドキュメントのロック所有者のシナリオ  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>ファイル"a"がファイルへの依存"b"  
 ファイルの種類の標準エディター"A"を実装する場合を検討"a"、および各ファイルの種類への参照 (または依存)、"a"が"b"の種類のファイルです。 ファイルの種類"b"、"B"の標準のエディターが存在しています。 エディター"A"がファイルを開くと、"a"は"b"の対応するファイルへの参照を取得します。 ファイル"b"が表示されませんが、エディターの"A"を変更できます。 エディター"A"から取得するファイルのドキュメントのデータへの参照を"b"、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>メソッドしも"b"のファイルの編集、ロックを保持します。 呼び出して、ファイル"b"でのカウントをファイル"b"編集ロックは減少することができますを変更するかエディター"A"が完了したら、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>メソッドです。 この手順を省略するには、呼び出されたとしていた場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 、パラメーターを持つメソッド`dwRDTLockType`に設定<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>です。  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>ファイル"b"が別のエディターで開かれる  
 ファイル"b"でが既に開いてエディター"B"エディター"A"は、それを開こうとすると、あるは、処理する 2 つの独立したシナリオがあります。  
  
-   ファイル"b"が互換性のあるエディターで開いている場合は、エディター"A"登録"b"のファイルを使用してドキュメント編集のロックが必要、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>メソッドです。 ロックを使用して、エディターの"A"には、変更ファイル"b"が完了したら、ドキュメントの登録を解除の編集、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>メソッドです。  
  
-   ファイル"b"が互換性のない方法で開いている場合は、「、」失敗するかは、"A"は、部分的を開くし、該当するエラー メッセージを表示するエディターに関連付けられているビューをさせることができますエディターでファイル"b"を実行しようとした、開くか、させることができます。 互換性のないエディターでファイル"b"を閉じるし、"a"を使用してファイルを再度開いてをユーザーに指示するエラー メッセージが必要がありますエディター"A"です。 実装することも、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>"b"のファイルを閉じるには、互換性のないエディターで開いているユーザー入力を求めます。 ユーザーがファイル"b", ファイルのオープンを閉じた場合の"a"エディター"A"は正常に続行します。  
  
## <a name="additional-document-edit-lock-considerations"></a>追加のドキュメントの編集のロックに関する考慮事項  
 エディターの"A"が、唯一のエディターがドキュメント エディター"B"、文書も保持する場合よりも、"b"のファイルのロックを編集するファイル"b"のロックを編集する場合は、異なる動作を取得します。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、**クラス デザイナー**関連付けられたコード ファイルで、編集のロックを保持していない、ビジュアル デザイナーの例に示します。 つまり、ユーザーは、クラス ダイアグラムのデザイン ビューで開くし、関連付けられたコード ファイルを同時に開く場合と、ユーザー コード ファイルを変更しても変更は保存されませんが、変更も失われますクラス ダイアグラム (.cd) ファイルにします。 場合、**クラス デザイナー**が唯一のドキュメントでは、コード ファイルのロックを編集するユーザーは求められませんコード ファイルを閉じるときに、変更を保存します。 IDE、ユーザーが閉じた後にのみ、変更を保存を求める、**クラス デザイナー**です。 両方のファイルには、保存された変更が反映されます。 両方の**クラス デザイナー**コード ファイル エディターでは、ユーザーは、コード ファイル、またはフォームを閉じるときに保存するように求められますし、コード ファイルにドキュメント編集をロックを保持します。 その時点で保存された変更は、フォームとコード ファイルの両方に反映されます。 クラス ダイアグラムでの詳細については、次を参照してください。[クラス図 (クラス デザイナー) で作業する](../ide/working-with-class-diagrams-class-designer.md)です。  
  
 エディター以外のドキュメントに編集ロックを配置する必要がある場合必要がありますを実装することに注意してください、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>インターフェイスです。  
  
 何度も UI デザイナー コード ファイルをプログラムで変更するは、1 つ以上のファイルに変更を加えます。 このような場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>メソッドの 1 つまたは複数のドキュメントの保存を処理する、**を次の項目への変更を保存するか。**  ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目  
 [実行中のドキュメント テーブル](../extensibility/internals/running-document-table.md)   
 [ドキュメント テーブルの保存と実行](../extensibility/internals/persistence-and-the-running-document-table.md)