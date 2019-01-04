---
title: ドキュメントの読み込みの遅延 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27edc56516293ff6502f0708a02faa7bae1e3719
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940363"
---
# <a name="delayed-document-loading"></a>ドキュメントの読み込みの遅延
ユーザーは、Visual Studio ソリューションを再度開き、ときに関連付けられているドキュメントのほとんどはすぐに読み込まれません。 ドキュメント ウィンドウ フレームが初期化保留中の状態で作成され、(スタブ フレームと呼ばれます) のプレース ホルダーのドキュメントが実行されているドキュメント テーブル (RDT) に配置されます。  
  
For Visual Studio 全体のメモリ使用量を増やすことができますが、それらが読み込まれる前に、ドキュメント内の要素のクエリを実行して不必要に読み込まれるプロジェクト ドキュメント、拡張機能があります。  
  
## <a name="document-loading"></a>ドキュメントの読み込み  
スタブのフレームとドキュメントは、ユーザーにアクセスすると、ドキュメントなど、ウィンドウ フレームのタブをクリックして完全に初期化されます。 ドキュメントは、ドキュメントのデータを取得するには、直接 RDT へのアクセスまたはない、RDT に直接アクセスする、次の呼び出しの 1 つのいずれかのドキュメントのデータを要求する拡張機能でも初期化できます。  
  
- ウィンドウ フレーム<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>メソッド。  
  
- ウィンドウ フレーム<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>メソッドを次のプロパティのいずれか。  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
- 場合は、拡張機能は、マネージ コードを使用して、呼び出す必要はありません<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>が特定される場合は、初期化保留中の状態では、ドキュメントまたはドキュメントが完全に初期化します。 理由は、メソッドは常にドキュメントを返すために必要な場合は作成、データ オブジェクト。 代わりを呼び出す必要がありますのいずれかで、`IVsRunningDocumentTable4`インターフェイス。  
  
- 拡張機能は、C++ を使用している場合は、渡す`null`したくないパラメーター。  
  
- 不要なドキュメントの他のプロパティを要求する前に、関連するプロパティを要求する前に、次のメソッドのいずれかを呼び出すことで読み込みを回避できます。  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>します。  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>。 このメソッドが戻る、<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>オブジェクトの値を含む<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>ドキュメントが初期化されていない場合。  
  
ドキュメントが完全に初期化されるときに発生する RDT イベントをサブスクライブして、ドキュメントが読み込まれたときに確認できます。 これには 2 つの可能性があります。  
  
- イベント シンクが実装されている場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>、購読できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>、  
  
- サブスクライブする場合は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>します。  
  

 次の例では、仮想的なドキュメントへのアクセスのシナリオを示します。拡張機能が開いているドキュメントに関する情報を表示する Visual Studio、インスタンスの編集をロック カウントとドキュメントのデータについて何か。 RDT を使用して、ドキュメントに列挙<xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>、呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>ドキュメントごとに、編集のロック カウントとドキュメント データを取得するためにします。 ドキュメントが、初期化保留中の状態にある場合、ドキュメント データを要求が不必要に初期化されます。  
  
 ドキュメントへのアクセスのより効率的な方法は、使用する<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A>編集のロック カウントを取得し、使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>ドキュメントが初期化されているかどうかを判断します。 フラグが含まれない場合<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>、ドキュメントは既に初期化されていると、ドキュメント データを要求し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A>不要な初期化は行われません。 フラグが含まれる場合<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>、拡張機能では、ドキュメントが初期化されるまでドキュメント データを要求しないようにする必要があります。 この初期化で検出できる、`OnAfterAttributeChange(Ex)`イベント ハンドラー。  
  
## <a name="test-extensions-to-see-if-they-force-initialization"></a>かどうか、強制的に初期化して拡張機能をテストします。  
 初期化かどうか、拡張機能で強制的に確認することは難しいために、ドキュメントが初期化されているかどうかを示すためにキューを表示することはありません。 テキストを完全に初期化されていないすべてのドキュメントのタイトルが発生するために、容易に確認するレジストリ キーを設定できます *[Stub]* タイトルにします。  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**設定**StubTabTitleFormatString**に *{0} [Stub]* します。