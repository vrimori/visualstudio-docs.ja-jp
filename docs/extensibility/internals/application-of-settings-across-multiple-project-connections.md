---
title: 複数プロジェクトの接続設定の適用 |Microsoft ドキュメント
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
ms.openlocfilehash: 0dff30ea80fb2de9bf4d90ffa48cd2f9b3d40756
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="application-of-settings-across-multiple-project-connections"></a>複数プロジェクトの接続設定の適用
ソース管理プラグインが複数のプロジェクトまたは複数の接続コンテキスト全体にわたって、同じソース管理の操作を実行するバッチ操作を使用してソース管理プラグイン API 1.2 を使用して作成できます。 バッチは、重複除去、プロジェクトごとのユーザー エクスペリエンス ダイアログ ボックスを使用できます。  
  
 ユーザーが、同じダイアログ ボックスを表示する場合は、ユーザーは、ソース管理プラグイン API 1.1 (たとえば、次の 2 つに Web プロジェクトを別のファイル共有のマシン) を使用して構築された、ソース管理プラグインで複数の接続に属している複数の項目を選択し、チェック アウトして、何度も何度も。 これは、ユーザーがクリックした場合でも、**すべてに適用**でチェック ボックス、ダイアログ ボックスで、IDE の各接続のコンテキストの状態がリセットされるためです。  
  
## <a name="new-capability-flag"></a>新しい機能フラグ  
 `SccBeginBatch` 関数のセット、`SCC_CAP_BATCH`バッチ操作が進行中であることを示すフラグ  
  
## <a name="new-functions"></a>新しい関数  
 次の新しい関数では、バッチ操作をサポートします。  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch`関数は、ソース管理操作のグループを開始します。 `SccEndBatch` グループを閉じます。 グループは、入れ子にできません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)