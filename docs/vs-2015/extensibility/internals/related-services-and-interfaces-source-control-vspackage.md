---
title: 関連サービスとインターフェイス (ソース管理 VSPackage) |Microsoft Docs
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
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05ee2b91204c9dca07f59e088ab07db7ee9ceaca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210133"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>関連サービスとインターフェイス (ソース管理 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このセクションでは、ソース管理 VSPackage に関連するインターフェイスすべて一覧表示、[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]します。 ソース管理 VSPackage では、これらのインターフェイスの一部を実装し、他のユーザーを使用してソース管理のタスクを実現します。  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>インターフェイス、およびソース管理 Vspackage の実装  
 次のインターフェイスが記載されて、 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]、し、ソース管理 VSPackage が、その目的の機能セットによってそれらのサブセットを実装します。 一部のインターフェイスがマークされていると必要なだけですべてのソース管理 VSPackage によって実装する必要があります。  
  
 パッケージを実装していない、それらのインターフェイスの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]既定の実装を提供します。 既定の実装に対応している場合は、VSPackage が登録されていないと、プロジェクトを制御していないときに注意してください。 正しく記述のソース管理 VSPackage では、これらのインターフェイスの既定の実装にしておくのではなく、すべての必要なインターフェイスを実装します。  
  
 ソース管理 VSPackage では、次のインターフェイスの一部またはすべてをカプセル化するプライベートのサービスを実装する必要があります。  
  
 インターフェイスは次のとおりです。  
  
-   必要です。 適切なエンティティ (プロジェクトのソース管理 VSPackage、ソース コントロールのスタブ) インターフェイスを実装する必要があります。  
  
-   推奨: エンティティはこのインターフェイスを実装する必要があります。それ以外の場合、ソース コントロールの機能が制限される可能性があります。  
  
-   省略可能: エンティティ インターフェイスを実装できますこの豊富な機能を提供します。  
  
|Interface|目的|によって実装されます。|実装します。|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|エディターでは、変更、またはファイルを保存する前にこのインターフェイスを呼び出します。 ソース管理 VSPackage ファイルをチェック アウトしたり、チェック アウトが失敗した場合、操作を拒否できます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|このインターフェイスは、プロジェクトでは、登録、登録を解除するソース管理を使用したプロジェクトと基本ソース コントロールのグリフのサポートを提供するなどの基本的なソース管理機能を提供します。|ソース管理 VSPackage|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|このインターフェイスがから取得した、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>を使用して、<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>関数、または単に実装するオブジェクトをキャストすることによって`IVsHierarchy`に`IVsSccProject2`します。 または、プロジェクトの現在のソース管理の状態または場所を通知するプロジェクトでソース管理下にあるファイルを取得するために使用されます。|プロジェクト|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|統合モジュールは、現在アクティブな VSPackage を設定するのにこのインターフェイスを使用します。|ソース管理 VSPackage|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|このインターフェイスは、サブスクリプション モデルに基づいています。 すべての VSPackage では、ドキュメントのイベントを受け取るし、発生されるイベントで、シェルによって了承する必要があることを通知できます。 実装され、によって処理される[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、実装するイベントを順番に渡す、 `IVsTrackProjectDocumentsEvents2` VSPackage にします。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|このインターフェイスは、バッチ処理、同期読み取り/書き込み操作、および高度な`OnQueryAddFiles`メソッド。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**ソリューション エクスプ ローラー**プロジェクトが新しいファイルがプロジェクトに追加されたときに、またはファイルとフォルダーの名前を変更またはプロジェクトから削除されたときに、このインターフェイスを呼び出すとします。 ソース管理 VSPackage では、プロジェクト ファイルをチェック アウトしたり、操作をキャンセルすることができます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**ソリューション エクスプ ローラー**プロジェクト IVstrackProjectDocuments3 インターフェイスのメソッドへの呼び出しに応答には、このインターフェイスを呼び出します。 ソース管理 VSPackage は、同期のバッチ操作を追跡できます読み取り/書き込み操作とより高度な使用`OnQueryAddFiles`メソッド。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|このインターフェイスは、参加リストの管理の Web プロジェクトのサポートを提供します。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|このインターフェイスは、プロジェクトのソース管理ファイルのツールヒントを取得するに使用されます。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|このインターフェイスは、名前空間の拡張機能のサポートを提供します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage では、このインターフェイスを使用して、名前空間の拡張機能を統合、**新規**、**オープン**、または**保存** ダイアログ ボックス。 その結果、プロジェクトに自動的に作成時に、ソース管理に追加したり、保存時に、ソース管理に追加操作が有効になります。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage では、このインターフェイスを使用して、ソース コントロールのグリフでのノードとして追加のグリフを定義**ソリューション エクスプ ローラー**します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|**追加**Web プロジェクト ダイアログ ボックスは、このインターフェイスを使用します。 ソース管理の場所とその場所でソース管理リポジトリに追加した Web プロジェクトを開くを参照するためのメソッドを提供します。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|このインターフェイスは、ソース管理からプロジェクトの読み込みを非同期 (バック グラウンド) のサポートを提供します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|このインターフェイスを使用するプロジェクトによって開始された非同期の読み込みの進行状況を監視する<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>します。|プロジェクト|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|このインターフェイスは、アクティブなソース管理 VSPackage のクエリを実行するための IDE を使用します。 IDE では、VSPackage の登録のアクティブなソース コントロールがない場合でも、意味を持つソース管理設定の値を照会します。 このインターフェイスが実装されており、によって処理される[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。|ソース コントロールのスタブ|必須|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|このインターフェイスは、ソース管理 VSPackage の登録に使用されます。|ソース コントロールのスタブ|必須|  
|<xref:EnvDTE.SourceControl>|このインターフェイスは、automation で使用されます。 そのため、UI を表示せずに実行できる機能のみを公開します。|ソース管理 VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|このインターフェイスは、ソリューション (.sln) ファイルで、ソース管理の設定を保存に使用されます。 設定には、ソース管理の場所とソース コントロールの状態フラグが含まれます。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|このインターフェイスは、ソリューションのオプション (.suo) ファイルでのソース管理の設定の保存に使用されます。 これには、現在のユーザーの参加リストの場所などのユーザーに固有のソース管理設定があります。|ソース管理 VSPackage|推奨|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|このインターフェイスは、イベントを監視するソリューションを閉じるか、またはプロジェクトを開くときに、新しいファイルをソース管理から取得する前にプロジェクト ファイルのチェックインなどの操作を実行するために使用されます。|ソース管理 VSPackage|推奨|  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)

