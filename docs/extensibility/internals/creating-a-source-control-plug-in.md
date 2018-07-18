---
title: ソース管理プラグインを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04c6125004aaf2740b54acdce91bef032647c6e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127864"
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