---
title: "ソース管理プラグインを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 679559b70096dc7ec3baa792ea98c0c3fea7cc67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-source-control-plug-in"></a>ソース管理プラグインを作成します。
Visual Studio SDK が有効にするソース コントロールの機能を追加するリソースを提供して、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 このドキュメントに記載されているソース管理プラグイン API に準拠している任意のプラグイン DLL を使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 ソース管理プラグインをインストールする方法について説明して、現在使用可能なソース管理プラグイン API バージョンを強調表示します。  
  
 [アーキテクチャ](../../extensibility/internals/source-control-plug-in-architecture.md)  
 プラグイン ソース管理の統合を説明するアーキテクチャの図を使用して、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
 [ソース管理プラグイン向けのテスト ガイド](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 インストールし、ソース管理プラグインの操作をテストする方法についてガイダンスを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理 VSPackage の作成](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 ソース コントロールだけでなく、ソース管理機能の提供が置換される VSPackage を作成する方法について説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース UI コントロールです。  
  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン API 内のすべての要素の完全な一覧を提供します。  
  
 [ソース管理](../../extensibility/internals/source-control.md)  
 統合の機能としてソース管理を実装するためのオプションについて説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。