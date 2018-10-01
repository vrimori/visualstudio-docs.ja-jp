---
title: 複数プロジェクトの接続設定の適用 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: cc2be78900e7bef33be138dfc8ed9dc1531af7c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534876"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>複数のプロジェクト接続全体への設定の適用
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[アプリケーションの設定で複数プロジェクトの接続](https://docs.microsoft.com/visualstudio/extensibility/internals/application-of-settings-across-multiple-project-connections)します。  
  
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

