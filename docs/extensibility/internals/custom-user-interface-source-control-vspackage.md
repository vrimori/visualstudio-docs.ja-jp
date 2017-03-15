---
title: "カスタム ユーザー インターフェイス (ソース コントロール VSPackage) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
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
ms.openlocfilehash: 0d4940ea62ac65671ffcb3bb29958e3d2e544c09
ms.lasthandoff: 02/22/2017

---
# <a name="custom-user-interface-source-control-vspackage"></a>カスタム ユーザー インターフェイス (ソース コントロールの vs パッケージ)
VSPackage では、Visual Studio コマンド テーブル (.vsct) ファイルをそのメニュー項目と既定の状態を宣言します。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage が読み込まれるまで統合開発環境 (IDE) に既定の状態でメニュー項目が表示されます。 その後、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>を有効にする、またはメニュー項目を無効にするメソッドが呼び出されます</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>。  
  
 コマンドのユーザー インターフェイス (UI) コンテキストに応じて、VSPackage を自動的に読み込まれなければ、VSPackage のレジストリ キーを設定する、ソース管理で通常 VSPackage を UI の特定のコンテキストを変更するだけではなくオンデマンドで読み込む必要があります。 AutoLoadPackages レジストリ キーの詳細については、次を参照してください。[管理 VSPackages](../../extensibility/managing-vspackages.md)します。  
  
## <a name="vspackage-ui"></a>VSPackage の UI  
 ソース管理パッケージは、VSPackage として実装されから UI を使用しない[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 ソース管理の VSPackage に固有のオプションの設定の各ソース管理 VSPackage にメニュー項目、メニュー グループ、ツール ウィンドウ、ツールバー、および必要な UI などの独自の UI 要素を指定してください。 これらの UI 要素は、静的または動的に有効にすることができます。 静的な UI 要素は、.vsct ファイルで定義されたされ、VSPackage が読み込まれるかどうかどうかに表示されます。 UI の動的な要素を参照できる特定のコマンドの UI コンテキストによってなど<xref:EnvDTE.Constants.vsContextNoSolution>の呼び出しの結果として、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:EnvDTE.Constants.vsContextNoSolution>。 動的な UI 要素の可視性は、Vspackage の遅延読み込みのための戦略と準拠しています。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>ソース コントロールの VSPackages に UI の制約  
 読み込まれた後、ソース管理 VSPackage を IDE から削除できません、ために、VSPackage で、非アクティブな状態に移行できる必要があります。 VSPackage active が不要になったという通知を受信した場合、VSPackage はその UI を無効にし、外部の IDE とのやり取りを無視します。 VSPackage の実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>VSPackage がアクティブでない場合は、メソッドにコマンドが非表示する必要があります</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>。  
  
 VSPackage を実装する必要がすべてのソース管理、`IVsSccProvider`インターフェイスです。 インターフェイスでは、2 つのメソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>、VSPackage で実装する必要があります</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>。  
  
 VSPackage がによって実装される各種の IDE イベントにサブスクライブしているソース管理、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>、という具合です</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>。 また、VSPackage がインターフェイスを実装したレジストリが有効なコールバック、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>など これは、必要がありますすべて無視されますアクティブでないとき。  
  
 次に、ソース管理 VSPackage のアクティブな状態に影響するインターフェイスを示します。  
  
-   プロジェクトのドキュメントのイベントを追跡します。  
  
-   ソリューションのイベントです。  
  
-   ソリューションの永続化のインターフェイス。 、非アクティブなときにパッケージする必要があります .sln および .suo ファイルに書き込みできません。  
  
-   プロパティのエクステンダー。  
  
 必要な<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>、およびソース管理 VSPackage がアクティブでないときもソース コントロールに関連付けられたすべての省略可能なインターフェイスは呼び出されません</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>。  
  
 ときに、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE を起動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド UI コンテキストを現在の既定のソース管理 VSPackage の id の ID に設定。 これにより、アクティブなソース コントロールが実際には、VSPackage を読み込むことがなく、IDE で表示される VSPackage の静的な UI です。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]登録する VSPackage の一時停止[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を通じて、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>うえで、vs パッケージへの呼び出しを行います</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>。  
  
 次の表では、特定の詳細を説明する方法について[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE には、さまざまな UI のアイテムが非表示にします。  
  
|UI 項目|説明|  
|-------------|-----------------|  
|メニューとツールバー|ソース管理パッケージはソース管理パッケージ ID に最初のメニューとツールバーの表示状態を設定する必要があります、 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct ファイルのセクションです。 これにより、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage を読み込んでの実装を呼び出すことがなくのメニュー項目の状態を適切に設定する IDE、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>。|  
|ツール ウィンドウ|ソース管理 VSPackage では、使用頻度の低いが行われると、所有するすべてのツール ウィンドウを非表示にします。|  
|ソース管理に固有の VSPackage のオプション ページ|HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts のレジストリ キーには、VSPackage を表示するには、そのオプション ページ必要とするコンテキストを設定することができます。 このキーの下のレジストリ エントリは、サービスのソース管理サービスの ID (SID) を使用し、1 の DWORD 値を割り当てることによって作成する必要があります。 UI イベントでは、VSPackage に登録されているソース管理のコンテキストで発生するたびに、アクティブな場合、VSPackage が呼び出されます。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution></xref:EnvDTE.Constants.vsContextNoSolution>   
 [Vspackage を管理します。](../../extensibility/managing-vspackages.md)
