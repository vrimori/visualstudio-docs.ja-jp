---
title: "複数プロジェクトの接続設定の適用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9750d946a941e86a6c0a6973661f00f8f44cf9b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="application-of-settings-across-multiple-project-connections"></a>複数プロジェクトの接続設定の適用
ソース管理プラグインが複数のプロジェクトまたは複数の接続コンテキスト全体にわたって、同じソース管理の操作を実行するバッチ操作を使用してソース管理プラグイン API 1.2 を使用して作成できます。 バッチは、重複除去、プロジェクトごとのユーザー エクスペリエンス ダイアログ ボックスを使用できます。  
  
 ユーザーが、同じダイアログ ボックスを表示する場合は、ユーザーは、ソース管理プラグイン API 1.1 (たとえば、次の 2 つに Web プロジェクトを別のファイル共有のマシン) を使用して構築された、ソース管理プラグインで複数の接続に属している複数の項目を選択し、チェック アウトして、何度も何度も。 これは、ユーザーがクリックした場合でも、**すべてに適用**でチェック ボックス、ダイアログ ボックスで、IDE の各接続のコンテキストの状態がリセットされるためです。  
  
## <a name="new-capability-flag"></a>新しい機能フラグ  
 `SccBeginBatch`関数のセット、`SCC_CAP_BATCH`バッチ操作が進行中であることを示すフラグ  
  
## <a name="new-functions"></a>新しい関数  
 次の新しい関数では、バッチ操作をサポートします。  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch`関数は、ソース管理操作のグループを開始します。 `SccEndBatch`グループを閉じます。 グループは、入れ子にできません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)