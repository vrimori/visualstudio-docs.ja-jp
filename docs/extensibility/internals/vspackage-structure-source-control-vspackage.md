---
title: VSPackage の構造 (ソース コントロール VSPackage) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13b811b504259bf10440419b3cb4029a4c239c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142790"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage の構造 (ソース コントロール VSPackage)
ソース コントロールのパッケージの SDK を提供する VSPackage を作成するためのガイドラインと自分のソース管理機能を統合するソース コントロールの実行者を許可する、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。 VSPackage は、COM コンポーネントによって、要求時に読み込まれた通常、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) は、そのレジストリ エントリで、パッケージによって提供されているサービスに基づいています。 すべての VSPackage を実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>です。 VSPackage によって提供されるサービスを通常使用する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE proffers、独自のいくつかのサービスとします。  
  
 VSPackage では、そのメニュー項目を宣言し、.vsct ファイルを使用して既定の項目の状態を確立します。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE では、VSPackage が読み込まれるまでこの状態のメニュー項目を表示します。 後で、VSPackage の実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>有効にするにまたはメニュー項目を無効にするメソッドが呼び出されます。  
  
## <a name="source-control-package-characteristics"></a>ソース コントロールのパッケージの特性  
 VSPackage が密接に統合されたソース管理[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 VSPackage のセマンティクスは次のとおりです。  
  
-   VSPackage によって実装されるインターフェイス (、`IVsPackage`インターフェイス)  
  
-   UI コマンドの実装 (.vsct ファイルとの実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス)  
  
-   VSPackage の登録[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 ソース管理 VSPackage と通信する必要これら他の[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]エンティティ。  
  
-   プロジェクト  
  
-   エディター  
  
-   ソリューション  
  
-   Windows  
  
-   実行中のドキュメント テーブル  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio 環境のサービス利用できる可能性があります。  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider サービス  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP インターフェイス実装され、呼び出されます  
 ソース管理パッケージは、VSPackage とそのために登録されているその他の Vspackage と直接対話できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 広範なソース管理機能を提供するために、ソース管理 VSPackage 対処できるプロジェクトまたはシェルによって提供されるインターフェイス。  
  
 すべてのプロジェクトで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>内のプロジェクトとして認識されるように、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。 このインターフェイスがない特殊なただし、ソース管理に十分なです。 ソースの下に必要なプロジェクト管理の実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>です。 そのコンテンツのプロジェクトのクエリを実行して、グリフとバインディング情報 (必要な情報、サーバーの場所とディスクの場所の下にあるプロジェクトの間の接続を確立するために提供することをソース コントロール VSPackage によってこのインターフェイスを使用します。ソース コントロールの場合)。  
  
 VSPackage の実装、ソース管理、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>、それによってプロジェクトをソース管理に登録し、そのステータス グリフを取得します。  
  
 ソース管理 VSPackage に考慮する必要がありますのあるインターフェイスの一覧については、次を参照してください。[関連サービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)です。  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [関連するサービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)