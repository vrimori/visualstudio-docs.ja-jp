---
title: "カスタム ユーザー インターフェイス (ソース コントロール VSPackage) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6138ffcd0c56b87e9e29a316aa2ae0ad9f982e18
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="custom-user-interface-source-control-vspackage"></a>カスタム ユーザー インターフェイス (ソース コントロール VSPackage)
VSPackage は、Visual Studio コマンド テーブル (.vsct) ファイルをそのメニュー項目とその既定の状態を宣言します。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) では、VSPackage が読み込まれるまでその既定の状態でメニュー項目を表示します。 その後、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>有効にするにまたはメニュー項目を無効にするメソッドが呼び出されます。  
  
 特定の UI コンテキストに切り替えるだけではなく要求時に VSPackage を読み込む必要がありますが、通常、ソースを制御、VSPackage は、コマンドのユーザー インターフェイス (UI) のコンテキストによって自動的に読み込むことができますので、VSPackage はレジストリ キーを設定できます。 AutoLoadPackages レジストリ キーの詳細については、次を参照してください。[を管理する Vspackage](../../extensibility/managing-vspackages.md)です。  
  
## <a name="vspackage-ui"></a>VSPackage の UI  
 ソース管理パッケージは、VSPackage として実装していません。 から UI[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 各ソース コントロールを VSPackage では、ソース管理 VSPackage に固有のオプションの設定のメニュー項目、メニュー グループ、ツール ウィンドウ、ツールバー、および、必須の UI など、独自の UI 要素を指定します。 これらの UI 要素は、静的または動的に有効にすることができます。 静的な UI 要素は、.vsct ファイルで定義されたれ、か、VSPackage が読み込まれるかどうかに表示されます。 UI 要素の動的な表示される可能性が、特定のコマンド UI コンテキストに応じてなど<xref:EnvDTE.Constants.vsContextNoSolution>、またはへの呼び出しの結果として、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドです。 動的な UI 要素の可視性は、Vspackage の遅延読み込みのための戦略に準拠しています。  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>ソース コントロールの Vspackage に UI 制約  
 読み込まれた後、ソース管理 VSPackage は、IDE から削除できません、ため、VSPackage が非アクティブな状態を入力できる必要があります。 VSPackage がアクティブなが不要になったという通知を受信すると、VSPackage は UI を無効にし、外部の IDE とのやり取りを無視します。 VSPackage の実装、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage がアクティブでない場合、メソッドはコマンドを隠す必要があります。  
  
 すべてのソース コントロールを VSPackage に実装する必要があります、`IVsSccProvider`インターフェイスです。 インターフェイスでは、2 つのメソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>、VSPackage によって実装する必要があります。  
  
 VSPackage を実装する、各種の IDE イベントにサブスクライブしている可能性があります、ソース管理、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>のようにします。 また、VSPackage がインターフェイスを実装レジストリが有効なコールバックなど、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>です。 これらすべて無視されなければなりませんアクティブでないとき。  
  
 次に、ソース管理の VSPackage のアクティブな状態によって影響を受けるインターフェイスを示します。  
  
-   プロジェクトのドキュメント イベントを追跡します。  
  
-   ソリューションのイベントです。  
  
-   ソリューションの永続化のインターフェイス。 ときに、使用頻度の低いパッケージする必要があります .sln および .suo のファイルに書き込まれません。  
  
-   プロパティ エクステンダーです。  
  
 必要な<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>、およびソース管理 VSPackage がアクティブでないときも、ソース管理に関連付けられている省略可能なインターフェイスは呼び出されません。  
  
 ときに、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE を起動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド UI コンテキストの現在の既定のソース管理 VSPackage の id ID を設定。 これにより、アクティブなソース管理に実際には、VSPackage を読み込むことがなく、IDE で表示される VSPackage の静的な UI です。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]登録する VSPackage の一時停止[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を通じて、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage に任意の呼び出しがなされる前にします。  
  
 次の表では、特定の詳細を説明する方法について[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE は、さまざまな UI アイテムを非表示にします。  
  
|UI 項目|説明|  
|-------------|-----------------|  
|メニューとツールバー|ソース管理パッケージはソース管理パッケージ ID に最初のメニューとツールバーの表示状態を設定する必要があります、 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) .vsct ファイルのセクションです。 これにより、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 、VSPackage を読み込むの実装を呼び出すことがなく、メニュー項目の状態を適切に設定する IDE、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドです。|  
|ツール ウィンドウ|VSPackage のソース管理には、非アクティブなが行われたときを所有している任意のツール ウィンドウが非表示にします。|  
|ソース管理 VSPackage に固有のオプション ページ|HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts のレジストリ キーには、VSPackage のオプション ページを表示する必要とするコンテキストを設定することができます。 このキーの下のレジストリ エントリは、サービスのソース管理サービスの ID (SID) を使用し、1 の DWORD 値を割り当てることによって作成する必要があります。 UI イベントは、VSPackage に登録されているソース管理のコンテキストで発生するたびにアクティブである場合、VSPackage が呼び出されます。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [VSPackage の管理](../../extensibility/managing-vspackages.md)