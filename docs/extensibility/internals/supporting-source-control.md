---
title: ソース管理をサポートする |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ae3590a5d02c2b3f1d4b67f724d0177f671f7d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-source-control"></a>ソース管理をサポートします。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ファイルのチェック アウト、チェックイン、およびプロジェクトまたはエディターの他のソース管理操作をサポートしています。 ソース管理クライアントとして[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]など、ソース管理パッケージと対話するように設計された[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]、アーカイブ、バージョン管理、および、動的に定義された一連のファイル制御機能を提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ソース管理パッケージのモデル](../../extensibility/internals/model-for-source-control-packages.md)  
 プロジェクトの種類を実装する必要がありますインターフェイスについて説明をソース管理をサポートします。  
  
 [設計上の決定](../../extensibility/internals/source-control-design-decisions.md)  
 質問の回答を変更するプロジェクトの種類を実装する方法を提供します。  
  
 [構成の詳細](../../extensibility/internals/source-control-configuration-details.md)  
 プロジェクトの種類の実装がどのように変化ソース管理のサポートについて説明します。  
  
 [プロジェクトおよびエディターのガイドライン](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 プロジェクトの種類とエディターのベスト プラクティスをについて説明します。  
  
 [ランタイムの詳細](../../extensibility/internals/source-control-runtime-details.md)  
 ユーザーがソース管理システムに追加するときに、プロジェクトを登録する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 環境またはソース管理パッケージ ファイルをメモリ内で変更または保存することを示します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 プロジェクトおよびソース管理に登録し、ソース管理の状態に関する情報を取得する階層を使用できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 プロジェクト ファイルとプロジェクト項目のソース管理を提供するプロジェクト システムで実装されます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 アクセス許可を追加、削除、またはファイルまたはソリューション内のディレクトリの名前を変更するための環境を照会するプロジェクトで使用します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 プロジェクト ファイルまたはディレクトリに加えられた変更のクライアントに通知します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 基本的なビルド ブロックでプロジェクトの概要を示します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 プロジェクトがビルドとコードのコンパイルを制御する方法を説明する追加のトピックへのリンクが提供されます。