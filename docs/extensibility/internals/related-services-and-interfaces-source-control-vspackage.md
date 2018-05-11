---
title: 関連するサービスとインターフェイス (ソース コントロール VSPackage) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f9e8e90fdda61524a9af107df452bc2b13cd90c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>関連するサービスとインターフェイス (ソース コントロール VSPackage)
このセクションでは、ソース管理のインターフェイスの VSPackage に関連するすべて一覧表示、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。 ソース コントロール VSPackage では、これらのインターフェイスの一部を実装し、他のユーザーを使用してソース管理のタスクを実現します。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>インターフェイスによって、ソース コントロールの Vspackage の実装  
 次のインターフェイスが説明されている、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]、ソース管理 VSPackage が、その必要な機能セットによってそれらのサブセットを実装するとします。 一部のインターフェイスをマークとして必須であり、すべてのソース コントロール VSPackage によって実装する必要があります。  
  
 パッケージを実装しない、それらのインターフェイスの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]既定の実装を提供します。 既定の実装に対応している場合、VSPackage が登録されていないとプロジェクトは制御されていないときに注意してください。 適切に作成されたソース管理の VSPackage では、これらのインターフェイスの既定の実装を任せるのではなく、必要なすべてのインターフェイスを実装します。  
  
 ソース管理 VSPackage では、次のインターフェイスの一部またはすべてをカプセル化するプライベート サービスを実装しなければなりません。  
  
 インターフェイスは次のとおりです。  
  
-   必要です。 適切なエンティティ (プロジェクトのソース管理 VSPackage をソース コントロールのスタブ) インターフェイスを実装する必要があります。  
  
-   お勧めします。 エンティティはこのインターフェイスを実装する必要があります。それ以外の場合、ソース コントロールの機能が制限される可能性があります。  
  
-   省略可能: エンティティこのインターフェイスを実装、豊富な機能を提供します。  
  
|Interface|目的|によって実装されます。|実装しますか。|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|エディターでは、変更するか、またはファイルを保存する前にこのインターフェイスを呼び出します。 ソース管理 VSPackage ファイルをチェック アウトしたり、チェック アウトに失敗した場合、操作を拒否できます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|このインターフェイスは、登録しソース管理プロジェクトの登録を解除し、基本ソース コントロールのグリフのサポートを提供するなど、プロジェクトの基本的なソース管理の機能を提供します。|ソース管理 VSPackage|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|このインターフェイスがから取得した、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>を使用して、<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>関数、または単に実装するオブジェクトをキャストする`IVsHierarchy`に`IVsSccProject2`です。 または、現在のソース管理の状態または場所のプロジェクトを通知する、プロジェクトのソース管理下にあるファイルを取得するために使用されます。|プロジェクト|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|統合モジュールでは、このインターフェイスを使用、現在のアクティブな VSPackage を設定します。|ソース管理 VSPackage|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|このインターフェイスは、サブスクリプション model に基づいています。 ドキュメント イベントを受信し、有効期限が発生するイベントにシェルによって通知されるようにする必要があること、VSPackage のシグナルことができます。 実装およびによって処理される[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を実装するイベントを渡します`IVsTrackProjectDocumentsEvents2`VSPackage にします。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|このインターフェイスは、バッチ処理、読み取り/書き込みの同期操作、および高度な`OnQueryAddFiles`メソッドです。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**ソリューション エクスプ ローラー**プロジェクトが新しいファイルがプロジェクトに追加されたときに、またはファイルとフォルダーの名前を変更またはプロジェクトから削除されたときに、このインターフェイスを呼び出すとします。 ソース管理 VSPackage では、プロジェクト ファイルをチェック アウトしたり、操作をキャンセルすることができます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**ソリューション エクスプ ローラー**プロジェクトが IVstrackProjectDocuments3 インターフェイスのメソッドへの呼び出しに応答には、このインターフェイスを呼び出すとします。 VSPackage が同期されているバッチの操作を追跡できますソース管理読み取り/書き込み操作、および高度な使用`OnQueryAddFiles`メソッドです。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|このインターフェイスは、Web プロジェクトの参加リストの管理のサポートを提供します。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|このインターフェイスを使用して、プロジェクト内のソース管理の対象ファイルのツールヒントを取得します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|このインターフェイスは、名前空間の拡張機能のサポートを提供します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage では、このインターフェイスを使用して、名前空間の拡張機能を統合、**新規**、**開く**、または**保存** ダイアログ ボックス。 そのため、プロジェクトに自動的に作成時に、ソース管理に追加したり、保存時に、ソース管理に追加操作が有効になっています。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage では、このインターフェイスを使用して、内のノードのソース コントロールの記号として追加グリフを定義**ソリューション エクスプ ローラー**です。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**追加**Web プロジェクトのダイアログ ボックスは、このインターフェイスを使用します。 ソース管理の場所と以前にその場所でソース管理リポジトリに追加した Web プロジェクトを開くを参照するためのメソッドを提供します。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|このインターフェイスは、ソース管理からプロジェクトの読み込みの非同期 (バック グラウンド) のサポートを提供します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|このインターフェイスにより、プロジェクトによって開始される非同期の読み込みの進行状況を監視する<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>です。|プロジェクト|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|このインターフェイスは、アクティブなソース制御 VSPackage のクエリを実行するための IDE を使用します。 IDE は VSPackage の登録のアクティブなソース コントロールがない場合でも、意味を持つソース管理の設定の値を照会します。 このインターフェイスが実装されており、によって処理される[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|このインターフェイスは、ソース管理 VSPackage の登録で使用されます。|ソース コントロールのスタブ|必須|  
|<xref:EnvDTE.SourceControl>|このインターフェイスは、オートメーションで使用されます。 そのため、UI を表示することがなく実行できる機能のみを公開します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|このインターフェイスを使用すると、ソリューション (.sln) ファイルに、ソース管理の設定を保存します。 設定には、ソース管理の場所とソース コントロールの状態フラグが含まれます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|このインターフェイスを使用すると、ソリューションのオプション (.suo) ファイルにソース管理の設定を保存します。 これには、現在のユーザーの参加リストの場所などのユーザーに固有のソース管理の設定が含まれます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|このインターフェイスは、ソリューションを閉じるか、またはプロジェクトを開くときに、ソース管理から新しいファイルを取得する前にプロジェクト ファイルのチェックインなどの操作を実行するために使用イベントを監視します。|ソース管理 VSPackage|推奨|  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)