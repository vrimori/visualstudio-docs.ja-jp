---
title: カスタム ユーザー インターフェイス (ソース管理 VSPackage) |Microsoft Docs
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
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 237a79fe0225f54bd8be1f779f241bc54f13cd09
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728534"
---
# <a name="custom-user-interface-source-control-vspackage"></a>カスタム ユーザー インターフェイス (ソース管理 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage は、Visual Studio Command Table (.vsct) ファイルをそのメニュー項目と既定の状態を宣言します。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage が読み込まれるまで、統合開発環境 (IDE) が既定の状態でメニュー項目を表示します。 その後、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>を有効にするか、メニュー項目を無効にするメソッドが呼び出されます。  
  
 VSPackage では、コマンドのユーザー インターフェイス (UI) のコンテキストによって自動的に読み込むことができますので、VSPackage がレジストリ キーを設定できます、UI の特定のコンテキストに切り替えるだけではなく、オンデマンドで VSPackage を読み込む必要がありますが、通常、ソースを制御します。 AutoLoadPackages のレジストリ キーの詳細については、次を参照してください。[管理 Vspackage](../../extensibility/managing-vspackages.md)します。  
  
## <a name="vspackage-ui"></a>VSPackage の UI  
 ソース管理のパッケージは、VSPackage として実装されから UI を使用しない[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 各ソース管理 VSPackage では、ソース管理 VSPackage に固有のオプションの設定のメニュー項目、メニュー グループ、ツール ウィンドウ、ツールバー、および必要な UI など、独自の UI 要素を指定する必要があります。 これらの UI 要素は、静的または動的に有効にすることができます。 静的な UI 要素は、.vsct ファイルで定義されてし、か、VSPackage が読み込まれるかどうかが表示されます。 UI の動的な要素があります、特定のコマンドの UI コンテキストに応じて表示など<xref:EnvDTE.Constants.vsContextNoSolution>、または呼び出しの結果として、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド。 動的な UI 要素の可視性は、Vspackage の遅延読み込みのための戦略に準拠します。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>ソース管理 Vspackage の UI の制約  
 ソース管理 VSPackage は、それが読み込まれた後、IDE から削除できません、ため、VSPackage が非アクティブな状態を入力できる必要があります。 VSPackage では、active は不要になったという通知を受信すると、VSPackage はその UI を無効にし、外部の IDE の操作を無視します。 VSPackage の実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドは、VSPackage がアクティブでないときにコマンドを隠す必要があります。  
  
 すべてのソース コントロールを VSPackage に実装する必要があります、`IVsSccProvider`インターフェイス。 インターフェイスでは、2 つのメソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>、VSPackage によって実装する必要があります。  
  
 ソース管理 VSPackage はによって実装される、さまざまな IDE イベントにサブスクライブしている可能性があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>など。 また、VSPackage 可能性がありますが実装レジストリが有効なコールバック インターフェイスなど、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>します。 これらすべて無視するアクティブでないとします。  
  
 次に、ソース管理 VSPackage のアクティブな状態の影響を受けるインターフェイスを示します。  
  
- プロジェクトのドキュメントのイベントを追跡します。  
  
- ソリューションのイベントです。  
  
- ソリューションの永続化のインターフェイス。 アクティブでないと、は、パッケージは .sln および .suo のファイルには記述しないでください。  
  
- エクステンダーのプロパティ。  
  
  必要な<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>、およびソース管理 VSPackage がアクティブでないときも、ソース管理に関連付けられている省略可能なインターフェイスは呼び出されません。  
  
  ときに、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE を起動[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]コマンドの UI コンテキストの現在の既定のソース管理 VSPackage の id ID に設定。 これにより、アクティブなソース コントロールが実際には、VSPackage を読み込むことがなく、IDE で表示される VSPackage の静的な UI です。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage を登録するを一時停止[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を通じて、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage の呼び出しの前にします。  
  
  次の表では、特定の詳細を説明する方法について[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE は、さまざまな UI 項目を非表示にします。  
  
|UI 項目|説明|  
|-------------|-----------------|  
|メニューとツールバー|ソース管理パッケージは、ソース管理パッケージ ID に最初のメニューとツールバーの表示状態を設定する必要があります、 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct ファイルのセクション。 これにより、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 、VSPackage の読み込みとの実装を呼び出すことがなく、メニュー項目の状態を適切に設定する IDE、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッド。|  
|ツール ウィンドウ|ソース管理 VSPackage では、非アクティブなが行われると、所有する任意のツール ウィンドウを非表示にします。|  
|ソース管理 VSPackage に固有のオプション ページ|HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts レジストリ キーには、VSPackage のオプション ページに表示される必要とするコンテキストを設定することができます。 このキーの下のレジストリ エントリは、サービスのソース管理サービス ID (SID) を使用して、1 の DWORD 値を割り当てることによって作成される必要があります。 UI のイベントは、VSPackage に登録されているソース管理のコンテキストで発生するたびにアクティブになっている場合、VSPackage が呼び出されます。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [VSPackage の管理](../../extensibility/managing-vspackages.md)

