---
title: VSPackage 構造 (ソース管理 VSPackage) |Microsoft Docs
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
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63c1eae7d53050f1763ba868d8d545ab7f326a34
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906924"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 構造 (ソース管理 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース コントロールのパッケージの SDK には、VSPackage を作成するためのガイドラインにより、ソースのコントロール実装側で自分のソース管理機能を統合する、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境。 VSPackage は、COM コンポーネントからの要求時に読み込まれた通常、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]統合開発環境 (IDE) は、そのレジストリ エントリで、パッケージによって提供されているサービスに基づいています。 すべての VSPackage を実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>します。 VSPackage は、通常によって提供されるサービスを消費、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE proffers、独自の一部のサービスとします。  
  
 VSPackage では、そのメニュー項目を宣言し、.vsct ファイルを使用して既定の項目の状態を確立します。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE では、VSPackage が読み込まれるまでこの状態のメニュー項目を表示します。 その後、VSPackage の実装の<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>を有効にするか、メニュー項目を無効にするメソッドが呼び出されます。  
  
## <a name="source-control-package-characteristics"></a>ソース コントロール パッケージの特性  
 ソース管理 VSPackage は、密接に統合されて[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 VSPackage のセマンティクスは次のとおりです。  
  
- あること、VSPackage によって実装されるインターフェイス (、`IVsPackage`インターフェイス)  
  
- UI コマンドの実装 (.vsct ファイルとの実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス)  
  
- VSPackage の登録[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
  ソース管理 VSPackage 通信する必要がこれら他[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]エンティティ。  
  
- プロジェクト  
  
- エディター  
  
- ソリューション  
  
- Windows  
  
- 実行中の document テーブル  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>使用できる visual Studio 環境のサービス  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 SVsRegisterScciProvider サービス  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP インターフェイス実装され、呼び出されます  
 ソース管理のパッケージは、VSPackage とそのために登録されているその他の Vspackage と直接やり取りできる[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 ソース管理機能一式を提供するためにソース管理 VSPackage 扱うことができるプロジェクトまたはシェルによって提供されるインターフェイス。  
  
 すべてのプロジェクトで[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>内のプロジェクトとして認識されるように、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。 ただし、このインターフェイスがない特殊化されたソース管理には十分です。 ソースの下に必要なプロジェクト管理の実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>します。 このインターフェイスは、その内容にプロジェクトを照会して、グリフとバインディング情報 (必要な情報、サーバーの場所とディスクの場所の下にあるプロジェクトの間の接続を確立するために提供することをソース管理 VSPackage によって使用されます。ソース管理の場合)。  
  
 ソース管理 VSPackage の実装、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>、さらにプロジェクトをソース管理に登録し、その状態のグリフを取得できます。  
  
 ソース管理 VSPackage が考慮する必要があるインターフェイスの完全な一覧を参照してください。[関連サービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)します。  
  
## <a name="see-also"></a>関連項目  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [関連サービスとインターフェイス](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

