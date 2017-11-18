---
title: "ドキュメントの読み込みを遅延 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 794eccaf59b65044840d459bbde2e17eab8684a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="delayed-document-loading"></a>ドキュメントの読み込みの遅延
ユーザーは、Visual Studio ソリューションを再度、ときに関連付けられているドキュメントのほとんどはすぐに読み込まれません。 ドキュメント ウィンドウ フレームが初期化保留中の状態で作成され、(スタブ フレームと呼ばれます) のプレース ホルダーのドキュメントを実行しているドキュメント テーブル (RDT) では配置されます。  
  
 プロジェクトのドキュメントを読み込むことができませんが不必要に読み込まれる前に、ドキュメント内の要素のクエリを実行して、拡張機能があります。 これにより、Visual Studio の全体的なメモリ使用量が向上します。  
  
## <a name="document-loading"></a>ドキュメントの読み込み  
 スタブのフレームとドキュメントが完全に初期化される、ユーザーにアクセスした場合、ドキュメントでは、たとえばウィンドウ フレームのタブをクリックしています。 ドキュメントは、ドキュメント データを取得するには、直接 RDT へのアクセスまたはない、RDT に直接アクセスする、次の呼び出しの 1 つで、ドキュメントのデータを要求する拡張機能により初期化できます。  
  
-   ウィンドウ フレームの show メソッド:<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>です。  
  
-   ウィンドウ フレーム GetProperty メソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>で、次のプロパティ。  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 場合は、拡張機能は、マネージ コードを使用して、呼び出す必要はありません<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>初期化保留中の状態では、ドキュメントまたはドキュメントが完全に初期化することを確認してから、. これは、このメソッドは常にドキュメントを返すので、データ オブジェクト、必要な場合は作成します。 代わりに、メソッドのいずれかを IVsRunningDocumentTable4 インターフェイスで呼び出す必要があります。  
  
 拡張機能は、C++ を使用する場合は、渡す`null`したくないパラメーターです。  
  
 関連するプロパティを要求する前に、次のメソッドのいずれかを呼び出すことによって、不要なドキュメントの読み込みを回避できます。 その他のプロパティを要求する前にします。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>です。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>。 このメソッドが戻る、<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>オブジェクトの値を含む<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>ドキュメントが初期化されていない場合。  
  
 ドキュメントを完全に初期化されるときに発生する RDT イベントにサブスクライブすることで、ドキュメントが読み込まれたときに調べることができます。 これには 2 つの可能性があります。  
  
-   イベント シンクを実装する場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>、サブスクライブするには<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>、  
  
-   それ以外の場合、サブスクライブするには<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>します。  
  
 仮定のドキュメントのアクセスのシナリオを次に示します。 拡張機能が開いているドキュメントに関する情報を表示する Visual Studio、インスタンスの編集をロック数と、ドキュメント データについて何か。 RDT を使用して、ドキュメントが列挙<xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>、しを呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>ドキュメントごとに、編集のロック カウントとドキュメント データを取得するためにします。 このドキュメントは、初期化保留中の状態では場合、ドキュメント データを要求しているが不必要に初期化されます。  
  
 使用するにはこの実行の方法がより効率的<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A>編集ロック数を取得し、使用して<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>ドキュメントが初期化されているかどうかを決定します。 フラグが含まれない場合<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>、ドキュメントは既に初期化されていると、ドキュメント データを要求して<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A>不要な初期化は行われません。 フラグは含まれている場合<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>ドキュメントが初期化されるまで、ドキュメントのデータを要求する、拡張機能を避ける必要があります。 これは、OnAfterAttributeChange(Ex) イベント ハンドラーで検出できます。  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>表示かどうかは、強制的に初期化する拡張機能のテスト  
 初期化かどうか、拡張機能で強制的に確認するが困難にするため、ドキュメントが初期化されているかどうかを示すためにキューを表示することはありません。 簡単に検証、レジストリ キーを設定するには、テキストが、完全に初期化されていないすべてのドキュメントのタイトルが発生するため`[Stub]`タイトルにします。  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**設定、 **StubTabTitleFormatString**に**{0} [スタブ]**です。