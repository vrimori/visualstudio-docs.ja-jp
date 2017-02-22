---
title: "ソース管理をサポートします。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース コントロール [Visual Studio SDK] をサポートします。"
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース管理をサポートします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のサポートはプロジェクトまたはエディターでチェック アウトチェックインおよびそのほかのソース管理操作を許可します。  ソース管理クライアントとして[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] がアーカイブを提供するソース管理パッケージによって[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] のような相互作用するために動的に定義された一連のファイルのバージョン管理機能と設計されています。  
  
## このセクションの内容  
 [ソース管理パッケージのモデル](../../extensibility/internals/model-for-source-control-packages.md)  
 ソース管理をサポートするためにプロジェクトを実行する必要があるインターフェイスを定義します。  
  
 [設計上の決定](../../extensibility/internals/source-control-design-decisions.md)  
 プロジェクトを実行すると答えが変更する問題を示します。  
  
 [構成の詳細](../../extensibility/internals/source-control-configuration-details.md)  
 ソース管理のサポートがプロジェクトの種類の実装が変化する方法について説明します。  
  
 [プロジェクトおよびエディターの他のガイドライン](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 プロジェクトの種類とエディターのベスト プラクティスについて説明します。  
  
 [ランタイムの詳細](../../extensibility/internals/source-control-runtime-details.md)  
 ユーザーがソース管理システムに追加するときにプロジェクトを登録する方法について説明します。  
  
## 関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 ファイルがメモリに変更するかまたは保存されるソース管理の環境またはパッケージに示します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 ソース管理とに登録しソース管理の状態に関する情報を取得するとプロジェクト階層。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 プロジェクト ファイルおよびプロジェクト項目のソース管理を提供するためにプロジェクト システムで実行されます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 ソリューション ファイルまたはディレクトリを追加削除または名前を変更するアクセス許可の環境を照会プロジェクトによって使用されます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 プロジェクト ファイルまたはディレクトリに加えられた変更をクライアントに通知します。  
  
## 関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の統合開発環境の基本的なビルド ブロックとしてプロジェクトの概要について \(IDE\) 説明します。  リンクがどのように管理プロジェクト ビルドのコンパイル コードの説明するそのほかのトピックについて説明します。