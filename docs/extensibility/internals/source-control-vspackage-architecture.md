---
title: コントロールの VSPackage のアーキテクチャをソース |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a423b270eb8a26e9573f957da48915db37bf6851
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-vspackage-architecture"></a>ソース コントロールの VSPackage のアーキテクチャ
ソース管理パッケージは、サービスを使用して、VSPackage、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE を提供します。 代わりに、ソース管理パッケージは、ソース管理サービスとしての機能を提供します。 さらに、ソース管理パッケージは、ソース管理プラグインにソース管理を統合するためのよりも柔軟性の高い代替[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 厳密なコントラクトは、ソース管理プラグイン ソース管理プラグイン API を実装します。 たとえば、プラグインを置換できません既定[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザー インターフェイス (UI)。 さらに、ソース管理プラグイン API は有効にしません、独自のソース コントロールのモデルを実装するプラグイン。 ただし、ソース管理パッケージでは、これらの制限の両方は解決します。 ソース管理パッケージが、ソース管理のエクスペリエンスを完全に制御を[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザー。 さらに、ソース管理パッケージ独自ソース コントロールのモデル、および使用できますロジック、すべてのソース コントロールに関連するユーザー インターフェイスを定義できます。  
  
## <a name="source-control-package-components"></a>ソース管理パッケージのコンポーネント  
 アーキテクチャの図に示すように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース コントロールのスタブをという名前のコンポーネントは、VSPackage を使用してソース管理パッケージを統合する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 ソース コントロールのスタブは、次のタスクを処理します。  
  
-   ソース管理パッケージの登録に必要な共通の UI を提供します。  
  
-   ソース管理パッケージを読み込みます。  
  
-   ソース管理パッケージをアクティブ/非アクティブとして設定します。  
  
 ソース コントロールのスタブは、ソース管理パッケージのアクティブなサービスを検索し、そのパッケージに IDE から受信したすべてのサービス呼び出しをルーティングします。  
  
 ソース管理アダプター パッケージは、特別なソース管理パッケージを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を提供します。 このパッケージは、ソース管理プラグインをソース コントロールのプラグイン API に基づいてをサポートするための中央コンポーネントです。 ソース管理プラグインは、アクティブなプラグインが、ソース コントロールのスタブは、ソース管理アダプター パッケージにそのイベントを送信します。 さらに、ソース管理アダプターのパッケージを使用して、ソース管理プラグイン API を使用して、ソース管理プラグイン通信も、既定値はすべてソース管理プラグインで一般的な UI を提供します。  
  
 ソース管理パッケージがアクティブなパッケージの場合は、その一方で、ソース コントロールのスタブと直接通信するパッケージを使用して、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]パッケージのソース管理のインターフェイスです。 ソース管理パッケージは、独自のソース管理 UI をホストします。  
  
 ![ソース管理アーキテクチャ グラフィック](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 ソース管理パッケージ[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コントロールのソース コードまたは統合するための API に指定されていません。 これに記載されているアプローチに対し[ソース管理プラグインを作成する](../../extensibility/internals/creating-a-source-control-plug-in.md)ソース管理プラグインが固定された一連の関数とコールバックを実装するを必要です。  
  
 ソース管理パッケージとは、VSPackage のように、COM オブジェクトを使用して作成できる`CoCreateInstance`です。 VSPackage、自体利用できるように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]実装することによって IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>です。 VSPackage がサイトのポインターを受け取るインスタンスが作成されると、および<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>VSPackage へのアクセス、利用可能なサービスと、IDE でインターフェイスを提供するインターフェイスです。  
  
 ソース管理プラグイン API ベースを作成するよりもより高度なプログラミングの専門知識を必要とソース コントロールを VSPackage に基づくパッケージの書き込みプラグインします。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [はじめに](../../extensibility/internals/getting-started-with-source-control-vspackages.md)