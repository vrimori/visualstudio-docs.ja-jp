---
title: "Document テーブルを実行している |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 41a9fc5a2b364ecc0c9037980c3ef2804a6808d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="running-document-table"></a>実行中のドキュメント テーブル
IDE では、実行中のドキュメント テーブル (RDT) と呼ばれる内部構造内のすべての現在開いているドキュメントの一覧を保持します。 この一覧には、これらドキュメントの現在編集されているかどうかにかかわらず、メモリ内のすべての開いているドキュメントが含まれます。 ドキュメントは、ファイル、プロジェクトまたはメイン プロジェクト ファイル (.vcxproj ファイルなど) を含めて、保存されている任意の項目です。  
  
## <a name="elements-of-the-running-document-table"></a>実行中の Document テーブルの要素  
 実行中のドキュメント テーブルには、次のエントリが含まれています。  
  
|要素|説明|  
|-------------|-----------------|  
|ドキュメント モニカー|ドキュメント データ オブジェクトを一意に識別する文字列。 ファイル (たとえば、C:\MyProject\MyFile) を管理するプロジェクト システムのファイルの絶対パスになります。 この文字列は、データベース内のストアド プロシージャなどのファイル システム以外のストアに保存されたプロジェクトにも使用されます。 この場合、プロジェクト システムが認識してドキュメントを格納する方法を決定する可能性のある解析できる一意の文字列の在庫のことができます。|  
|階層の所有者|階層オブジェクトによって表されるように、ドキュメントを所有している、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイスです。|  
|項目 ID|階層内で特定の項目の項目の識別子です。 この値は、このドキュメントを所有している階層内のすべてのドキュメント間で一意では、この値は、異なる階層全体で一意であることは保証されません。|  
|ドキュメント データ オブジェクト|これには、少なくとも、`IUnknown`<br /><br /> オブジェクト。 IDE では、特定のインターフェイス以外は必要ありません、`IUnknown`カスタム エディターのドキュメント データ オブジェクトのインターフェイスです。 ただし、標準のエディターについてのエディターの実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>プロジェクトからファイルの永続性の呼び出しを処理するインターフェイスが必要です。 詳細については、次を参照してください。[標準ドキュメントの保存](../../extensibility/internals/saving-a-standard-document.md)です。|  
|フラグ|読み取りまたは編集のロックが適用されるかどうか、ドキュメントの保存されているかどうかを制御するフラグというようは、RDT にエントリを追加指定できます。 詳細については、<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列挙型のページをご覧ください。|  
|ロック カウントを編集します。|編集のロックの数。 編集ロックでは、いくつかのエディターがドキュメントを開いて編集することを示します。 遷移したときの編集のロックの数を 0 に、ユーザーは、ドキュメントを保存するように求めが変更された場合。 たとえばを使用して、エディターでドキュメントを開くたびに、**新しいウィンドウ**コマンドを編集ロックは、RDT でそのドキュメントに追加します。 編集ロックを設定するためには、ドキュメントか必要がありますの階層を持つ項目の id。|  
|読み取りロック数|読み取りロックを数します。 読み取りロックは、ウィザードなどのメカニズムによって、ドキュメントが読み取られていることを示します。 読み取りロックでは、ドキュメントを編集できないことを示すときに、RDT 内で有効で、ドキュメントを保持します。 ドキュメントが階層または項目の id。 していない場合でも、読み取りロックを設定することができます。 この機能を使用すると、メモリ内のドキュメントを開き、任意の階層によって所有されているドキュメントなし、RDT に入力できます。 この機能はほとんど使用されません。|  
|ロックの所有者|インスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>インターフェイスです。 ロックの所有者は、ウィザードを開き、エディターの外部でドキュメントの編集などの機能によって実装されます。 ロック所有者使用して、機能を引き続き編集中に閉じられてから、ドキュメントを防ぐためにドキュメントを編集ロックを追加します。 通常、編集のロックがドキュメント ウィンドウ (つまり、編集者) によってのみ追加します。|  
  
 RDT 内の各エントリは、一意の階層または一般に、プロジェクト内の 1 つのノードに対応する項目 ID に関連付けられているがします。 編集に使用できるすべてのドキュメントは通常、階層によって所有されます。 RDT で行ったエントリを制御するプロジェクトまたは — より正確に、どの階層が現在編集されているドキュメント データ オブジェクトを所有しています。 RDT で情報を使用して、IDE は、一度に 1 つ以上のプロジェクトで開かれるされないドキュメントをようにできます。  
  
 階層データの永続化を制御して、RDT で更新する情報を使用しても、**保存**と**名前を付けて保存** ダイアログ ボックス。 ユーザー ドキュメントを変更しを選択して、**終了**コマンドを**ファイル**メニュー、IDE プロンプトで、 **Save Changes**それらを表示するすべてのプロジェクト ダイアログ ボックス現在に変更されているプロジェクト アイテムです。 これにより、保存するドキュメントの中から選択できます。 保存するドキュメントの一覧 (つまり、変更を含んでいるドキュメント)、RDT から生成されます。 要求しているすべての項目、 **Save Changes**アプリケーションの終了時にダイアログ ボックスでは、RDT にレコードがあります。 どのドキュメントが保存され、保存についてユーザーを求めるかどうかを調整する、RDT 各ドキュメントのフラグのエントリで指定された値を使用して操作します。 RDT フラグの詳細については、次を参照してください。、<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>列挙します。  
  
## <a name="edit-locks-and-read-locks"></a>編集のロックと読み取りロック  
 編集のロックと読み取りロック、RDT に存在します。 ドキュメント ウィンドウのインクリメントおよびデクリメント、編集をロックします。 したがって、ユーザーを開くと、次のように新しいドキュメント ウィンドウ、編集ロック数 1 だけインクリメントします。 編集のロックの数には、ゼロに達すると、永続化または関連するドキュメントのデータを保存する階層が通知されます。 階層は、ファイル、またはリポジトリ内のアイテムとして永続化を含む、任意の方法でデータを保持し、ことができます。 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>編集ロックを追加し、読み取りロック、インターフェイスを<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>これらのロックを削除する方法です。  
  
 通常、エディターは、ドキュメント ウィンドウがインスタンス化されるときにウィンドウ フレーム内自動的に追加、編集ロックのドキュメントの RDT です。 ただし、ドキュメントのカスタム ビューを作成する場合を使用しない、標準のドキュメント ウィンドウ (つまり、実装していない、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイス)、独自の編集のロックを設定する必要があります。 たとえば、ウィザードでドキュメントをエディターで開かれることがなく編集します。 ウィザードと同様のエンティティによって開かれるドキュメントをロックするためには、これらのエンティティを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>インターフェイスです。 ドキュメントのロックの保持者を登録するには、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>メソッド、およびパスを<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>実装します。 これにより、RDT にドキュメントのロックの保持者を追加します。 ドキュメントのロックの保持者を実装するためのもう 1 つのシナリオは、特別なツール ウィンドウを使用してドキュメントを開くかどうかです。 このインスタンスでは、いないのドキュメントを閉じるツール ウィンドウにできます。 ただし、登録、RDT でドキュメントのロック所有者として、IDE 呼び出すことができますの実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>ドキュメントの終了を要求するメソッド。  
  
## <a name="other-uses-of-the-running-document-table"></a>実行中の Document テーブルの他の使用  
 IDE の他のエンティティは、ドキュメントに関する情報を取得、RDT を使用します。 たとえば、基になるコントロール マネージャーは、ファイルの最新バージョンを取得した後に、エディター内のドキュメントを再読み込みするのにことを指定するのに、RDT を使用します。 これを行うには、基になるコントロール マネージャーは、そのいずれかが開いているかどうかに表示する RDT 内のファイルを検索します。 している場合、ソース コントロール マネージャーは、階層を実装するを参照してください。 まず、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッドです。 プロジェクトを実装しない場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッド、そのソース制御マネージャーのチェックを実装するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>直接ドキュメント データ オブジェクトのメソッドです。  
  
 IDE も、RDT を使用して再び表面化 (前面に表示)、ユーザーがそのドキュメントを要求する場合の開いているドキュメントです。 詳細については、次を参照してください。 [、開いているファイルのコマンドを使用してファイルを表示する](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)です。 ファイルがを RDT で開いているかどうかを決定するには、次の手順をいずれか。  
  
-   については、項目が開いているドキュメント モニカー (つまり、ドキュメントの完全パス) を照会します。  
  
-   ドキュメントの完全パスが、プロジェクト システムを確認し、項目を RDT 内を検索して、階層、または項目の ID を使用します。  
  
## <a name="see-also"></a>参照  
 [RDT_ReadLock の使用方法](../../extensibility/internals/rdt-readlock-usage.md)   
 [ドキュメント テーブルの保存と実行](../../extensibility/internals/persistence-and-the-running-document-table.md)