---
title: 複数プロジェクトの接続設定の適用 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d8b8d7d6dc1e596686a2fad7b53363b2387a47b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500044"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>複数プロジェクトの接続設定の適用
ソース管理プラグインが複数のプロジェクトまたは複数の接続コンテキスト全体にわたって、同じソース管理の操作を実行するバッチ操作を使用してソース管理プラグイン API バージョン 1.2 を使用して構築できます。 バッチは、冗長、プロジェクトごとのユーザー エクスペリエンスからダイアログ ボックスを使用できます。  
  
 ユーザーが同じ場合は、ユーザーは、ソース管理プラグイン API バージョン 1.1 (たとえば、2 つに web プロジェクト別のファイル共有のマシン) を使用して構築された、ソース管理プラグインで複数の接続に属している複数の項目を選択し、チェック アウト、ダイアログ ボックスの繰り返しです。 ユーザーがクリックした場合でも、このシナリオが発生した、**すべてに適用**IDE の各接続のコンテキストの状態がリセットされるため、ボックスのダイアログ ボックスでを確認します。  
  
## <a name="new-capability-flag"></a>新しい機能フラグ  
 `SccBeginBatch`機能セット、`SCC_CAP_BATCH`バッチ操作が進行中であることを示すフラグ。  
  
## <a name="new-functions"></a>新しい関数  
次の新しい関数では、バッチ操作をサポートします。  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  

  
`SCCBeginBatch`関数は、ソース管理操作のグループを開始します。 `SccEndBatch`関数は、グループを閉じます。 グループは、入れ子にできません。  
  
## <a name="see-also"></a>関連項目  
 [新機能については、ソース管理プラグイン API バージョン 1.2 です。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)