---
title: どのような&#39;ソース管理の新 |Microsoft Docs
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
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a108acb2ae32b64292cd819c75de4726f067a00
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752466"
---
# <a name="what39s-new-in-source-control"></a>どのような&#39;s ソース管理の新機能
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]深く統合ソース制御ソリューションをソース管理 VSPackage を実装することによって行うことができます。 このセクションでは、ソース管理 Vspackage の機能について説明し、実装の手順の概要を説明します。  
  
## <a name="the-source-control-vspackage"></a>ソース管理 VSPackage  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ソース管理ソリューションの 2 つの種類をサポートしています。 すべてのバージョンの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、ソース管理プラグイン API ベースを統合することができますもプラグイン。 深い統合を提供するソース管理 VSPackage を作成することもできます。[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]面の知識と自律性の高いレベルを必要とするソース管理ソリューションに適したパス。  
  
 VSPackage は、ほとんどの機能の種類を追加できます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 ソース管理 VSPackage の完全なソース制御機能を提供する[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、ソース管理システムとのバック エンド通信をユーザーに表示される UI から。  
  
 ソース管理 VSPackage の実装には、「全部かゼロか」の戦略が必要です。 ソース管理 VSPackage の作成者とインターフェイスでさまざまなソース コントロールのインターフェイスと (ダイアログ ボックス、メニューのおよびツールバー) 全体のソース管理機能をカバーする、新しい UI 要素を実装する作業量が大幅に投資する必要があります。すべてのパッケージと正常に統合するために必要な[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 次の手順では、ソース管理パッケージを実装するために必要なものの概要を提供します。 詳細については、次を参照してください。[ソース管理 VSPackage を作成する](../../extensibility/internals/creating-a-source-control-vspackage.md)します。  
  
1.  プライベート ソース管理サービスを proffers VSPackage を作成します。  
  
2.  によって提供される、ソース コントロールに関連するサービスで、インターフェイスを実装[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)](たとえば、<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>インターフェイス)。  
  
3.  ソース管理 VSPackage を登録します。  
  
4.  すべてのソース管理メニュー項目、ダイアログ ボックス、ツールバー、およびコンテキスト メニューを含め、UI を実装します。  
  
5.  すべてのソース コントロールに関連するイベントは、それがアクティブであり、VSPackage によって処理する必要があるときに、ソース管理 VSackage に渡されます。  
  
6.  ソース管理 VSPackage が実装するようなイベントをリッスンする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>トラック プロジェクト ドキュメント (TPD) のイベントとインターフェイス (によって実装される、<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>インターフェイス)、必要な操作をします。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概要](../../extensibility/internals/source-control-integration-overview.md)   
 [ソース管理 VSPackage の作成](../../extensibility/internals/creating-a-source-control-vspackage.md)

