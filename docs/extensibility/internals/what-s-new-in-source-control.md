---
title: どのような&#39;ソース管理の |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b46730ab1acac6605af2e1ff1c418dbe8c886406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-source-control"></a>どのような&#39;ソース コントロールの
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]ソース コントロール VSPackage の実装によって深く統合ソース管理ソリューションを提供できます。 このセクションでは、ソース管理の Vspackage の機能について説明し、実装の手順の概要を説明します。  
  
## <a name="the-source-control-vspackage"></a>ソース コントロール VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 2 つの種類のソース コントロールのソリューションをサポートしています。 すべてのバージョンで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、ソース管理プラグイン API ベースを統合することができますもプラグインします。 詳細な統合を提供するソース管理の VSPackage を作成することもできます。[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]ソース制御ソリューションを高いレベルの知識と自律性を必要とするのに適したパス。  
  
 VSPackage は、ほとんどの種類の機能を追加できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 ソース管理の VSPackage の完全なソース制御機能を提供する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、ソース管理システムとバック エンドの通信をユーザーに表示される UI からです。  
  
 ソース制御 VSPackage を実装するには、「すべてまたは nothing」の戦略が必要です。 ソース管理の VSPackage の作成者は、インターフェイスだけでなくさまざまなソース コントロールのインターフェイスと (ダイアログ ボックス、メニューのおよびツールバー) 全体のソース管理機能をカバーする新しい UI 要素を実装する作業量を大幅をかける必要があります。いずれかのパッケージが正常に統合するために必要な[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 次の手順では、ソース管理パッケージを実装するために必要な一般的な概要を説明します。 詳細については、「[ソース コントロールの VSPackage を作成する](../../extensibility/internals/creating-a-source-control-vspackage.md)です。  
  
1.  プライベートはソース管理サービスを proffers する VSPackage を作成します。  
  
2.  提供されるソース コントロールに関連するサービスでインターフェイスを実装[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](たとえば、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>インターフェイス)。  
  
3.  ソース管理 VSPackage を登録します。  
  
4.  すべてのソース管理メニュー項目、ダイアログ ボックス、ツールバー、およびコンテキスト メニューを含め、UI を実装します。  
  
5.  すべてのソース コントロールに関連するイベントは、アクティブな場合は、VSPackage によって処理される必要があります、ソース管理 VSackage に渡されます。  
  
6.  ソース管理 VSPackage が実装するようイベントをリッスンする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>トラック プロジェクト ドキュメント (TPD) イベントだけでなくインターフェイス (によって実装される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>インターフェイス) し、必要なアクションを実行します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概要](../../extensibility/internals/source-control-integration-overview.md)   
 [ソース管理 VSPackage の作成](../../extensibility/internals/creating-a-source-control-vspackage.md)