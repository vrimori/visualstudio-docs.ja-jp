---
title: Document テーブルを実行している |。Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd7b8cd44c72ea058f71575bdd1774efafa86731
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746294"
---
# <a name="running-document-table"></a>ドキュメント テーブルの実行
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE では、実行中のドキュメント テーブル (RDT) と呼ばれる内部構造内のすべての現在開いているドキュメントの一覧を保持します。 この一覧には、これらのドキュメントの現在編集されているかどうかに関係なく、メモリ内のすべての開いているドキュメントが含まれています。 ドキュメントでは、プロジェクトまたはメイン プロジェクト ファイル (.vcxproj ファイルなど) でファイルを含む、保存されている任意の項目です。  
  
## <a name="elements-of-the-running-document-table"></a>実行中の Document テーブルの要素  
 実行中のドキュメント テーブルには、次のエントリが含まれています。  
  
|要素|説明|  
|-------------|-----------------|  
|ドキュメント モニカー|ドキュメント データ オブジェクトを一意に識別する文字列。 ファイル (たとえば、C:\MyProject\MyFile) を管理するプロジェクト システムのファイルの絶対パスになります。 この文字列は、データベース内のストアド プロシージャなど、ファイル システム以外のストアに保存されているプロジェクトに対しても使用されます。 この場合、プロジェクト システムが認識してドキュメントを格納する方法を決定する可能性がある解析する一意の文字列の在庫のことができます。|  
|階層の所有者|によって表される、ドキュメントを所有する hierarchy オブジェクト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイス。|  
|項目 ID|階層内の特定の項目の項目の識別子。 この値はこのドキュメントを所有している階層内のすべてのドキュメント間で一意ですが、この値は、さまざまな階層間で一意であることは保証されません。|  
|ドキュメント データ オブジェクト|これは、少なくとも、 `IUnknown`<br /><br /> オブジェクト。 IDE は、特定のインターフェイスを超えるを必要としない、`IUnknown`カスタム エディターのドキュメント データ オブジェクトのインターフェイス。 ただし、標準のエディター用のエディターの実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>インターフェイスは、プロジェクトからファイルの永続化の呼び出しを処理するために必要です。 詳細については、次を参照してください。[標準ドキュメントの保存](../../extensibility/internals/saving-a-standard-document.md)します。|  
|フラグ|ドキュメントを保存するかどうか、読み取りまたは編集のロックが適用されるかどうかを制御するフラグは、RDT にエントリを追加指定できます。 詳細については、<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 列挙型のページをご覧ください。|  
|ロックの数を編集します。|編集のロックの数。 編集のロックをするには、いくつかのエディターがドキュメントを開いて編集することを示します。 編集のロックの数を 0 にへの移行が変更された場合、ドキュメントを保存する、ユーザーが表示されます。 たとえばを使用して、エディターでドキュメントを開くたびに、**新しいウィンドウ**コマンドを RDT でそのドキュメントの編集のロックが追加されます。 編集のロックを設定するためには、ドキュメントか必要があります階層がある項目の id。|  
|読み取りロック数|読み取りロックを数します。 読み取りロックでは、ウィザードなどのメカニズムによって、ドキュメントが読み取られることを示します。 読み取りロックでは、ドキュメントを編集できないことを示すときに、RDT では有効なドキュメントを保持します。 ドキュメントから階層があるまたは項目の id。 ない場合でも、読み取りロックを設定できます。 この機能を使用すると、メモリ内、ドキュメントを開き、任意の階層によって所有されているドキュメントなし、RDT に入力できます。 この機能はほとんど使用されません。|  
|ロックの所有者|インスタンス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>インターフェイス。 ロックの所有者は、ウィザードを開き、エディター外でドキュメントを編集するなどの機能によって実装されます。 ロックの所有者は、ドキュメントがまだ編集中に閉じられていることを防ぐためにドキュメントに、編集のロックを追加する機能を使用できます。 通常、編集のロックはドキュメント ウィンドウ (つまり、エディター) でのみ追加されます。|  
  
 RDT の各エントリは、一意の階層をまたはそれに関連付けられている、一般的に、プロジェクトの 1 つのノードに対応する項目 ID があります。 編集に利用できるすべてのドキュメントでは、階層通常が所有します。 RDT で作成されたエントリは、プロジェクトを制御または -より正確に、どの階層が現在編集対象のドキュメント データ オブジェクトを所有しています。 RDT の情報を使用して、IDE は、一度に 1 つ以上のプロジェクトで開かれているからドキュメントを防ぐことができます。  
  
 階層データの永続化を制御して更新する、RDT の情報を使用しても、**保存**と**付けて** ダイアログ ボックス。 ユーザーがドキュメントの変更し、選択し、**終了**コマンドから、**ファイル**メニュー、IDE でプロンプト、**変更の保存**それらのすべてのプロジェクトを表示する ダイアログ ボックスプロジェクトの変更は現在の項目。 これにより、保存するドキュメントの中から選択できます。 保存するドキュメントの一覧 (つまり、変更が存在するそれらのドキュメント)、RDT から生成されます。 すべての項目を参照するくださいと想定している、**変更の保存**アプリケーションの終了時にダイアログ ボックスで、RDT のレコードがあります。 どのドキュメントが保存され、保存についてユーザーに求めるかどうかを調整する、RDT 各ドキュメントのフラグのエントリで指定された値を使用して操作します。 RDT フラグの詳細については、次を参照してください。、<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>列挙体。  
  
## <a name="edit-locks-and-read-locks"></a>編集のロックとロックの読み取り  
 編集のロックと読み取りロックが、RDT 内に存在します。 ドキュメント ウィンドウのインクリメントとデクリメント、編集をロックします。 そのため、ユーザーでは、新しいドキュメント ウィンドウが開いたら、編集のロックは 1 つずつをカウントします。 編集のロックの数がゼロに達すると、永続化または関連付けられているドキュメントのデータを保存する階層が通知されます。 階層は、次に、ファイル、またはリポジトリ内の項目として永続化など、何らかの方法でデータを保持できます。 使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A>メソッドで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>編集のロックを追加し、読み取りロックでは、インターフェイス、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A>これらのロックを削除する方法。  
  
 通常、エディターのドキュメント ウィンドウがインスタンス化されるときにウィンドウ フレーム自動的に追加のドキュメントの編集のロックを RDT の。 ただし、ドキュメントのカスタム ビューを作成する場合を使用しない標準のドキュメント ウィンドウ (つまり、実装していない、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>インターフェイス)、独自の編集のロックを設定する必要があります。 たとえば、ウィザードで文書をエディターで開かれることがなく編集します。 ウィザードと同種のエンティティによって開かれているドキュメントのロックのためには、これらのエンティティを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>インターフェイス。 ドキュメント ロックの保持者を登録するには、呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A>メソッド、およびパスで、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>実装します。 これにより、ドキュメント ロック ホルダーを RDT に追加します。 ドキュメント ロック ホルダーを実装するためのもう 1 つのシナリオでは、特別なツール ウィンドウを使用してドキュメントを開くかどうかです。 このインスタンスでできないドキュメントを閉じるツール ウィンドウにします。 ただしに、RDT のドキュメント ロック ホルダーとして登録する IDE は実装を呼び出すの<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A>ドキュメントの終了を要求するメソッド。  
  
## <a name="other-uses-of-the-running-document-table"></a>実行中の Document テーブルの他の使用  
 IDE の他のエンティティは、ドキュメントに関する情報を取得、RDT を使用します。 たとえば、ソース コントロールのマネージャーは、ファイルの最新バージョンを取得した後に、エディターでドキュメントを再読み込みするのにシステムに指示するのに、RDT を使用します。 これを行うには、ソース コントロールのマネージャーは、これらのいずれかが開いている RDT 内のファイルを検索します。 ソース コントロール マネージャーは、まず、階層を実装することを確認する場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッド。 プロジェクトが実装していない場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>メソッド、そのソース制御マネージャーのチェックの実装については、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>ドキュメント データ オブジェクトを直接のメソッド。  
  
 IDE が再び表面化することも、RDT を使用 (、最前面へ移動)、ユーザーがそのドキュメントを要求した場合、開いているドキュメント。 詳細については、次を参照してください。 [Open File コマンドを使用してファイルを表示する](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)します。 ファイルが、RDT で開いているかどうかを判断するには、1 つは、以下します。  
  
-   項目が開いているを確認するには、ドキュメント モニカー (つまり、ドキュメントの完全パス) を照会します。  
  
-   階層または項目の ID を使用して、プロジェクト システムを完全なドキュメントのパス、要求を RDT を項目を検索します。  
  
## <a name="see-also"></a>関連項目  
 [RDT_ReadLock の使用法](../../extensibility/internals/rdt-readlock-usage.md)   
 [ドキュメント テーブルの保存と実行](../../extensibility/internals/persistence-and-the-running-document-table.md)

