---
title: コマンド ルーティング アルゴリズム |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2a99fc6e87e59bf4cc0008c20905f9dc145102b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53965578"
---
# <a name="command-routing-algorithm"></a>コマンド ルーティング アルゴリズム
Visual Studio でのコマンドは、さまざまなコンポーネントによって処理されます。 コマンドは、現在の選択に基づいて、最も内側のコンテキストから最も外側の (グローバルとも呼ばれます) のコンテキストにルーティングされます。 詳細については、次を参照してください。[コマンド可用性](../../extensibility/internals/command-availability.md)します。  
  
## <a name="order-of-command-resolution"></a>コマンドの解像度の順序  
 コマンドは、レベルは次のコマンド コンテキストを介して渡されます。  
  
1.  アドインを使用します。環境は、最初に存在するすべてのアドイン コマンドを提供します。  
  
2.  コマンドの優先順位:これらのコマンドを使用して登録<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>します。 これらは、Visual Studio で、すべてのコマンドが呼び出され、登録された順序で呼び出されます。  
  
3.  コンテキスト メニューのコマンド:コンテキスト メニューにあるコマンドは最初に一般的なルーティングには、コンテキスト メニューとその後に提供されるコマンドの対象に提供されます。  
  
4.  ツールバーは、コマンド ターゲットを設定します。呼び出すときにこれらのコマンド ターゲットが登録されて<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>します。 `pCmdTarget`パラメーターを指定できます`null`します。 ない場合`null`を設定して、ツールバー上にある任意のコマンドを更新するコマンドは、このターゲットが使用されます。 シェルは、ツールバーで、設定し、として、ウィンドウ フレームを渡すかどうか、`pCmdTarget`できるように、ツールバー、ウィンドウ フレームを使ってフローをコマンドにすべての更新プログラムもない場合にフォーカスします。  
  
5.  ツール ウィンドウ:ツール ウィンドウで、通常、実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイスを実装する必要も、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスのツール ウィンドウがアクティブなウィンドウ、Visual Studio は、コマンド ターゲットを取得できます。 ただし、ツール ウィンドウを持つ場合は、フォーカスがある、**プロジェクト**ウィンドウで、次のコマンドにルーティング、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>選択した項目の共通の親であるインターフェイスです。 コマンドにルーティングしてこの選択は、複数のプロジェクトにまたがっている場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>階層。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスが含まれています、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>メソッドは、対応する各コマンドに似ている<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。  
  
6.  ドキュメント ウィンドウ:コマンドにある場合、`RouteToDocs`フラグの設定その *.vsct*のいずれかのドキュメント ビュー オブジェクトのコマンド ターゲットのインスタンスは、ファイル、Visual Studio、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>インターフェイスまたはドキュメントのインスタンス オブジェクト (通常、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>インターフェイスまたは<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>インターフェイス)。 Visual Studio のコマンドをルーティングするドキュメント ビューのオブジェクトが、コマンドをサポートしていない場合、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスが返されます。 (これは、ドキュメント データ オブジェクトのオプションのインターフェイスです)。  
  
7.  現在の階層。現在の階層がアクティブなドキュメント ウィンドウまたはで選択されている階層を所有しているプロジェクトを指定できます**ソリューション エクスプ ローラー**します。 Visual Studio が検索、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>現在、またはアクティブな階層に実装されているインターフェイス。 階層では、プロジェクト項目のドキュメント ウィンドウにフォーカスがある場合でも、階層がアクティブにされるたびに、有効なコマンドをサポートする必要があります。 ただし、コマンドの場合にのみ適用される**ソリューション エクスプ ローラー**を使用してフォーカスをサポートする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスとその<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>メソッド。  
  
     **切り取り**、**コピー**、**貼り付け**、**削除**、**の名前を変更**、**入力**、および**DoubleClick**コマンドが特別な処理が必要です。 処理する方法については**削除**と**削除**階層では、コマンドを参照してください、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>インターフェイス。  
  
8.  グローバル。Visual Studio が実装するコマンドを所有する VSPackage にルーティングしようとした場合は、前述のコンテキストでコマンドが処理されていない、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。 Visual Studio を呼び出すといない読み込まれる場合、VSPackage は既に読み込まれていない、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド。 場合にのみ、VSPackage が読み込まれる、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>メソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [コマンド デザイン](../../extensibility/internals/command-design.md)