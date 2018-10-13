---
title: 複数プロジェクトの接続設定の適用 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81d6a1f540314863e4e24b3b91c7f4112e0af8f0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197614"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>複数のプロジェクト接続全体への設定の適用
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理プラグインが複数のプロジェクトまたは複数の接続コンテキスト全体にわたって、同じソース管理の操作を実行するバッチ操作を使用してソース管理プラグイン API 1.2 を使用して構築できます。 バッチは、冗長、プロジェクトごとのユーザー エクスペリエンスからダイアログ ボックスを使用できます。  
  
 ユーザーは、ソース管理プラグイン API 1.1 (たとえば、2 つに Web プロジェクト別のファイル共有のマシン) を使用して構築された、ソース管理プラグインでは、複数の接続に属している複数の項目を選択し、チェック アウト、ユーザーには、同じダイアログ ボックスが表示されます。何度も何度も。 ユーザーがクリックした場合でもこれが発生、**すべてに適用**IDE の各接続のコンテキストの状態がリセットされるため、ボックスのダイアログ ボックスでを確認します。  
  
## <a name="new-capability-flag"></a>新しい機能フラグ  
 `SccBeginBatch` 関数のセット、`SCC_CAP_BATCH`バッチ操作が進行中であることを示すフラグ  
  
## <a name="new-functions"></a>新しい関数  
 次の新しい関数では、バッチ操作をサポートします。  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch`関数は、ソース管理操作のグループを開始します。 `SccEndBatch` グループを閉じます。 グループは、入れ子にできません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

