---
title: ソース コントロール Essentials の統合 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc3cfd145b35729362a30c3055806ba769782ef2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961547"
---
# <a name="source-control-integration-essentials"></a>ソース管理の統合の基本情報
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 2 種類のソース管理の統合をサポートしています: ソース管理プラグインを基本的な機能を提供し、ソース コントロールのプラグイン API (旧称 MSSCCI API)、および VSPackage に基づくソース制御の統合ソリューションを使用してビルドします。堅牢な機能を提供します。  
  
## <a name="source-control-plug-in"></a>ソース管理プラグイン  
 ソース管理のプラグインは、ソース管理プラグイン API を実装する DLL として書き込まれます。 登録とソースのコントロールの統合機能は、API を通じて提供されます。 このアプローチはソース管理 VSPackage でよりも実装が簡単に使用して、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理操作のほとんどのユーザー インターフェイス (UI)。  
  
 ソース コントロールが、ソース管理プラグイン API を使用してプラグインを実装するには、次の手順に従います。  
  
1. 指定された関数を実装する DLL を作成する[ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)します。  
  
2. 」の説明に従って、適切なレジストリ エントリを作成して、DLL を登録[方法。ソース管理プラグインをインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)します。  
  
3. ヘルパー UI を作成し、ソース コントロール アダプターのパッケージが表示されたときに表示 (、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理プラグインをソース管理機能を扱うコンポーネントです)。  
  
   詳細については、次を参照してください。[をソース管理プラグインを作成する](../../extensibility/internals/creating-a-source-control-plug-in.md)します。  
  
## <a name="source-control-vspackage"></a>ソース管理 VSPackage  
 ソース管理 VSPackage 実装では、カスタマイズされた代替を作成できる、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース UI コントロールです。 このアプローチは、ソース管理の統合を完全に制御を提供する UI 要素を提供し、それ以外の場合、プラグインのアプローチの下に指定するソース コントロールのインターフェイスを実装する必要しますが、あります。  
  
 ソース管理 VSPackage を実装するには、次の必要があります。  
  
1. 作成し、」の説明に従って、独自のソース管理、VSPackage を登録[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)します。  
  
2. カスタム UI では、既定のソース管理 UI を置き換えます。 参照してください[カスタム ユーザー インターフェイス](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)します。  
  
3. 使用して、処理するグリフを指定**ソリューション エクスプ ローラー**グリフ イベント。 参照してください[グリフ コントロール](../../extensibility/internals/glyph-control-source-control-vspackage.md)します。  
  
4. ように、クエリを編集し、クエリの保存のイベントを処理[クエリ編集のクエリの保存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)します。  
  
   詳細については、次を参照してください。[ソース管理 VSPackage を作成する](../../extensibility/internals/creating-a-source-control-vspackage.md)します。  
  
## <a name="see-also"></a>関連項目  
 [概要](../../extensibility/internals/source-control-integration-overview.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [ソース管理 VSPackage の作成](../../extensibility/internals/creating-a-source-control-vspackage.md)