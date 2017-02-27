---
title: "ソース管理の新機能します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新しい [Visual Studio SDK] ソース管理とは"
  - "ソース管理 [Visual Studio SDK] の新機能"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# ソース管理の新機能します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] VSPackage でソース管理を実装することにより深く統合ソース管理されたソリューションを提供できます。  ここではVSPackage のソース管理機能と実装の手順の概要を説明します。  
  
## ソース管理 VSPackage  
 ソース管理のサポート [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ソリューションの 2 種類。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のすべてのバージョンではソース管理プラグイン API ベースのプラグインを統合できます。  また洗練深統合と自主性の高レベルを必要とするソリューションをソース管理に適した [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] パスを指定するソース管理の VSPackage を作成できます。  
  
 VSPackage はほとんどの種類 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に機能を追加できます。  ソース管理 VSPackage はソース管理システムへのバック エンドの通信にユーザーに表示される UI からの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に完全なソース管理機能を提供します。  
  
 ソース管理 VSPackage を実行するとすべて 「または」何も計画する必要はありません。  ソース管理の作成者はVSPackage のソース管理機能をカバーするためのさまざまなソース管理インターフェイスと新しい UI 要素 \(ダイアログ ボックスメニューやツール バーなどの実行にかなりの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が正常に統合するすべてのパッケージで必要な工数インターフェイスを費やしたする必要があります。  
  
 次の手順は必要なソース管理パッケージを実行する内容の概要を示します。  詳細については、「[ソース コントロール VSPackage を作成します。](../../extensibility/internals/creating-a-source-control-vspackage.md)」を参照してください。  
  
1.  プライベート ソース管理サービスを提供する VSPackage を作成します。  
  
2.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] によって提供されるソース コントロールの関連のサービス インターフェイスを実装します \(たとえば<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> インターフェイス\)。  
  
3.  ソース管理 VSPackage を登録します。  
  
4.  メニュー項目ダイアログ ボックスツール バーおよびコンテキスト メニューを含むすべてのソース管理の UI を実行します。  
  
5.  すべてのソース コントロールに関連するイベントはソース管理 VSackage にアクティブなVSPackage で扱うときに渡されます。  
  
6.  \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> のインターフェイスが実装するソース管理 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> VSPackage はインターフェイスを実装するような \(TPD\) イベントをリッスンするまたはトラックのプロジェクトの文書のイベントと必要なアクションを実行する。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [概要](../../extensibility/internals/source-control-integration-overview.md)   
 [ソース コントロール VSPackage を作成します。](../../extensibility/internals/creating-a-source-control-vspackage.md)