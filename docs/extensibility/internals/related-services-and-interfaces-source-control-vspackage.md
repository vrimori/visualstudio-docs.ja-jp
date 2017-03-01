---
title: "関連するサービスとインターフェイス (ソース コントロール VSPackage) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
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
ms.openlocfilehash: 6d16e8eb229cd5187ae91630d9330a0e0f24eda2
ms.lasthandoff: 02/22/2017

---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>関連するサービスとインターフェイス (ソース コントロールの vs パッケージ)
このセクションでは、ソース管理のインターフェイスを VSPackage に関連するすべて一覧表示、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。 ソース管理 VSPackage では、これらのインターフェイスの一部を実装して、他のユーザーを使用してソース管理のタスクを実現します。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>ソース コントロールのある Vspackage で実装されたインターフェイス  
 次のインターフェイスは「 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]、ソース管理 VSPackage によっては、必要な機能セットには、それらの一部を実装してします。 一部のインターフェイスがマークされているために必要な済みとすべてのソース コントロール VSPackage によって実装される必要があります。  
  
 パッケージが実装されていない、これらのインターフェイスの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]既定の実装を提供します。 既定の実装に対応している場合は、VSPackage が登録されていないと、プロジェクトを制御していないときに注意してください。 適切に作成されたソース管理の VSPackage では、これらのインターフェイスの既定の実装を任せるのではなく、すべての必要なインターフェイスを実装します。  
  
 ソース管理 VSPackage では、次のインターフェイスの一部またはすべてをカプセル化するプライベート サービスを実装する必要があります。  
  
 インターフェイスは次のとおりです。  
  
-   必要です。 適切なエンティティ (プロジェクトのソース管理 VSPackage をソース コントロールのスタブ) インターフェイスを実装する必要があります。  
  
-   お勧めします。 エンティティはこのインターフェイスを実装する必要があります。それ以外の場合、ソース コントロールの機能が制限される可能性があります。  
  
-   省略可能: エンティティこのインターフェイスを実装、豊富な機能を提供します。  
  
|インターフェイス|目的|実装先|実装します。|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|エディターでは、変更したり、ファイルを保存する前にこのインターフェイスを呼び出します。 ソース管理 VSPackage ファイルをチェック アウトしたり、チェック アウトが失敗した場合、操作を拒否できます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|このインターフェイスは、プロジェクトでプロジェクトをソース管理の登録を解除して基本ソース コントロールのグリフのサポートを提供する登録などの基本的なソース管理機能を提供します。|ソース管理 VSPackage|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|このインターフェイスはから取得した、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>を使用して、<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>関数、または実装するオブジェクトにキャストするだけで`IVsHierarchy`に`IVsSccProject2`</xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 または、プロジェクトの現在のソース管理ステータスまたは場所を通知する、プロジェクトのソース管理下にあるファイルを取得するために使用されます。|プロジェクト|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|統合モジュールは、このインターフェイスを使用し、現在アクティブな vs パッケージを設定します。|ソース管理 VSPackage|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|このインターフェイスは、サブスクリプション モデルに基づきます。 ドキュメントのイベントを受信し、シェルによって発生されるイベントのことに注意して必要であるすべての VSPackage に通知できます。 実装およびによって処理される[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を実装するイベントを順番に渡して、 `IVsTrackProjectDocumentsEvents2` VSPackage にします。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|このインターフェイスは、バッチ処理、読み取り/書き込みの同期操作および高度な`OnQueryAddFiles`メソッドです。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**ソリューション エクスプ ローラー**し、プロジェクトが新しいファイルがプロジェクトに追加されるとき、またはファイルとフォルダーを名前変更またはプロジェクトから削除された場合、このインターフェイスを呼び出します。 ソース管理 VSPackage では、プロジェクト ファイルをチェック アウトしたり、操作をキャンセルすることができます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**ソリューション エクスプ ローラー**プロジェクトは、このインターフェイスを IVstrackProjectDocuments3 インターフェイスのメソッドへの呼び出しに応答を呼び出すとします。 VSPackage が同期のバッチ操作を追跡できるソース管理読み取り/書き込み操作とより高度な操作`OnQueryAddFiles`メソッドです。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|このインターフェイスは、Web プロジェクトの参加リストの管理のサポートを提供します。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|このインターフェイスは、プロジェクトでソース管理ファイルのツールヒントを取得する使用されます。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|このインターフェイスは、名前空間の拡張機能のサポートを提供します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage では、このインターフェイスを使用して、名前空間の拡張機能を統合、**新規**、**開く**、または**保存**ダイアログ ボックス。 その結果、プロジェクトに自動的に作成時に、ソース管理に追加したり、保存時に、ソース管理に追加操作が有効になっています。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage では、このインターフェイスを使用して、他の字形をソース コントロールのグリフ内のノードとして定義を**ソリューション エクスプ ローラー**します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**追加**Web プロジェクト ダイアログ ボックスは、このインターフェイスを使用します。 ソース管理の場所とその場所でソース管理リポジトリに追加した Web プロジェクトを開くために参照するためのメソッドを提供します。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|このインターフェイスは、ソース管理からプロジェクトの読み込みを非同期 (バック グラウンド) のサポートを提供します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|このインターフェイスを使用する<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>によって開始される非同期の読み込みの進行状況を監視するプロジェクト|プロジェクト|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|このインターフェイスは、アクティブなソース管理 VSPackage を照会するための IDE を使用します。 IDE では、VSPackage が登録されているアクティブなソース コントロールがない場合でも意味を持つソース管理設定の値を照会します。 このインターフェイスが実装されており、によって処理される[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|このインターフェイスは、VSPackage ソース コントロールの登録で使用されます。|ソース コントロールのスタブ|必須|  
|<xref:EnvDTE.SourceControl></xref:EnvDTE.SourceControl>|このインターフェイスは、オートメーションで使用されます。 そのため、UI を表示することがなく実行できる機能のみを公開します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|このインターフェイスを使用して、ソリューション (.sln) ファイルで、ソース管理の設定を保存します。 設定には、ソース管理の場所とソース コントロールの状態フラグが含まれます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|このインターフェイスを使用して、ソリューションのオプション (.suo) ファイルにソース管理の設定を保存します。 これには、現在のユーザーの参加リストの場所などの特定のユーザーのソース管理設定が含まれます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|このインターフェイスは、ソリューションを閉じるか、プロジェクトを開くときに、ソース管理から新しいファイルを取得する前にプロジェクト ファイルのチェックインなどの操作を実行するために使用イベントを監視します。|ソース管理 VSPackage|推奨|  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)
