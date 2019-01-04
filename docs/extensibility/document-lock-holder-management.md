---
title: ドキュメントのロック所有者の管理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f2f2da0e351f8444ef9966b00551b941830dda3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986441"
---
# <a name="document-lock-holder-management"></a>ドキュメント ロック ホルダーの管理
実行中の document テーブル (RDT) は、開いているドキュメントと、編集のロックがあるのカウントを保持します。 バック グラウンドで、ユーザーがドキュメント ウィンドウで、開いているドキュメントが表示される編集がプログラムを使用する際に、RDT のドキュメントで、編集のロックを配置できます。 この機能をグラフィカル ユーザー インターフェイスから複数のファイルを変更する、デザイナーによって使用されます。

## <a name="document-lock-holder-scenarios"></a>ドキュメント ロック ホルダー シナリオ

### <a name="file-a-has-a-dependence-on-file-b"></a>ファイル"a"が"b"のファイルへの依存
 ファイルの種類の標準エディター"の A"を実装する状況を検討してください"a"、および各ファイルの種類への参照 (または依存)、"a"が"b"の種類のファイル。 ファイルの種類"b"の標準エディターの"B"が存在します。 エディター"の A"がファイルを開いたときに、"a"は"b"の対応するファイルへの参照を取得します。 ファイル"b"は表示されませんが、"A"のエディターで変更できます。 エディター"A"から取得するファイルのドキュメント データへの参照を"b"、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>メソッドとも"b"のファイルを編集のロックを保持します。 エディター"の A"が完了した後呼び出すことによってファイル"b"をカウント ファイル"b"の編集のロックをデクリメントできますを変更、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>メソッド。 呼び出した場合、この手順を省略できます、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 、パラメーターを持つメソッド`dwRDTLockType`に設定<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>します。

### <a name="file-b-is-opened-by-a-different-editor"></a>"B"のファイルを別のエディターで開く
 ファイル"b"は"B"のエディターで既に開かれてエディター"A"は、それを開こうとすると、ある 2 つの独立したシナリオを処理するにがあります。

- ファイル"b"が互換性のあるエディターで開いている場合は、エディター「を」登録"b"のファイルを使用してドキュメント編集のロックが必要、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>メソッド。 ロックを使用して、エディターの"A"には、変更ファイル"b"が完了したら、ドキュメントの登録を解除の編集、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A>メソッド。

- ファイル"b"が、互換性のない方法で開いている場合は、"A"は、部分的に開くし、適切なエラー メッセージが表示のエディターに関連付けられているビューをさせることができます"A"の失敗、またはエディターでファイル"b"の試行開始させるかことができます。 互換性のないエディターでファイル"b"を閉じるし、"a"を使用してファイルを開いたりするユーザーに指示する必要がありますには、エラー メッセージ"A"のエディター。 実装することも、[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A>"b"のファイルを閉じるには、互換性のないエディターで開いているユーザーに確認します。 ユーザーが"b"、ファイルを開くファイルを閉じる場合の"a"エディター"A"が正常に続行されます。

## <a name="additional-document-edit-lock-considerations"></a>追加のドキュメントの編集のロックに関する考慮事項
 エディター"の A"はエディター"B"には、ドキュメントも保持している場合よりも、"b"のファイルのロックを編集、ドキュメントのある唯一のエディターはファイル"b"のロックを編集する場合は、異なる動作を取得します。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、**クラス デザイナー**関連付けられたコード ファイルで、編集のロックを保持していないビジュアルなデザイナーの例を示します。 これは、ユーザーが、クラス図をデザイン ビューで開くし、同時に、関連付けられたコード ファイルを開く、ユーザーは、コード ファイルを変更しますが、変更を保存できない場合は、変更は失わクラス ダイアグラム (.cd) ファイルにもします。 場合、**クラス デザイナー**が専用のドキュメントでは、コード ファイルのロックを編集、ユーザーは求められませんコード ファイルを閉じるときに変更を保存します。 IDE には、ユーザーが閉じた後にのみ、変更を保存を求める、**クラス デザイナー**します。 両方のファイルには、保存された変更が反映されます。 どちらの場合、**クラス デザイナー**コード ファイルのエディターでは、ユーザーは、コード ファイルまたはフォームを閉じるときに保存するように求められますし、コード ファイルで、ドキュメント編集のロックを保持します。 その時点で、保存された変更は、フォームと、コード ファイルの両方に反映されます。 クラス ダイアグラムの詳細については、次を参照してください。[クラス ダイアグラム (クラス デザイナー) の使用](../ide/class-designer/designing-and-viewing-classes-and-types.md)します。

 ドキュメントをエディター以外で、編集のロックを配置する場合は、する必要がありますを実装することに注意してください、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>インターフェイス。

 何度も UI デザイナー コード ファイルをプログラムで変更するは、1 つ以上のファイルに変更を加えます。 このような場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A>メソッド処理の方法では、1 つまたは複数のドキュメントの保存、 **、次のものに変更を保存するか。**  ダイアログ ボックス。

## <a name="see-also"></a>関連項目

- [実行中の document テーブル](../extensibility/internals/running-document-table.md)
- [永続化と実行中のドキュメント テーブル](../extensibility/internals/persistence-and-the-running-document-table.md)