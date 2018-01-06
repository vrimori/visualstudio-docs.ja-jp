---
title: "ソース コントロール Essentials の統合 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d474e00186cf2110dd8e701d980a1a4562beb8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-integration-essentials"></a>ソース コントロール Essentials の統合
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理の統合の 2 つの種類をサポートします: ソース管理プラグインを基本的な機能を提供し、使用して (旧称 MSSCCI API)、ソース管理プラグイン API と VSPackage に基づくソース コントロールの統合ソリューションをビルドします。堅牢な機能を提供します。  
  
## <a name="source-control-plug-in"></a>ソース管理プラグイン  
 ソース管理プラグインは、ソース管理プラグイン API を実装する DLL として書き込まれます。 登録とソース管理の統合機能は、API を通じて提供されます。 この方法は簡単にソース コントロール VSPackage よりも実装を使用して、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理操作のほとんどのユーザー インターフェイス (UI)。  
  
 プラグイン ソース管理プラグイン API を使用してソース管理を実装するのには、次の手順を実行します。  
  
1.  指定された関数を実装する DLL を作成する[ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)です。  
  
2.  」の説明に従って、適切なレジストリ エントリをすることで、DLL を登録[する方法: ソース管理プラグインをインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)です。  
  
3.  ヘルパー UI を作成し、ソース コントロール アダプター パッケージによってメッセージが表示されたらそれを表示します (、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理プラグインをソース管理機能を処理するコンポーネント)。  
  
 詳細については、次を参照してください。[ソース管理プラグインを作成する](../../extensibility/internals/creating-a-source-control-plug-in.md)です。  
  
## <a name="source-control-vspackage"></a>ソース コントロールの VSPackage  
 ソース管理 VSPackage 実装では、代わりにカスタマイズを開発することができます、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース UI コントロールです。 これにより、ソース管理の統合を完全に制御が、UI 要素を提供し、それ以外の場合、プラグインのアプローチの下で提供がソース コントロールのインターフェイスを実装する必要があります。  
  
 ソース管理の VSPackage を実装するのには、次の必要があります。  
  
1.  作成し、独自のソース管理、VSPackage を登録」の説明に従って[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)です。  
  
2.  既定のソース管理 UI をカスタムの UI に置き換えます。 参照してください[カスタム ユーザー インターフェイス](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)です。  
  
3.  使用して、処理するグリフを指定**ソリューション エクスプ ローラー**グリフ イベント。 参照してください[グリフ コントロール](../../extensibility/internals/glyph-control-source-control-vspackage.md)です。  
  
4.  ように、クエリを編集し、クエリの保存のイベントを処理[クエリ編集のクエリの保存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)です。  
  
 詳細については、次を参照してください。[ソース コントロールの VSPackage を作成する](../../extensibility/internals/creating-a-source-control-vspackage.md)です。  
  
## <a name="see-also"></a>参照  
 [概要](../../extensibility/internals/source-control-integration-overview.md)   
 [ソース管理プラグインを作成します。](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [ソース管理 VSPackage の作成](../../extensibility/internals/creating-a-source-control-vspackage.md)