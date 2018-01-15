---
title: "DSL 定義への拡張機能の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b3abe11e747db81579fb3851a1d05562d3f2fd11
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="adding-extensions-to-dsl-definitions"></a>DSL 定義への拡張機能の追加
DSL 定義の拡張機能では、ドメイン固有言語 (DSL) の拡張機能のパッケージを作成することができます。 Visual Studio Integration Extension (VSIX) に含まれる、DSL の拡張機能は、DSL と同じ方法でユーザーのコンピューターにインストールできます。 追加の機能を動的に有効になっているし、実行時に無効になっています。 Dsl を明示的に拡張機能に合わせて設計する必要はありません、拡張機能後で、またはサード パーティによる拡張の DSL を変更することがなく設計します。  
  
 追加の機能を次に含めることができます。  
  
-   モデル、およびプレゼンテーション要素のプロパティ  
  
-   図形とコネクタのデコレーター  
  
-   クラス、リレーションシップ、図形とコネクタ  
  
-   検証制約  
  
-   ツールボックス項目とタブ  
  
 拡張の DSL のユーザーが作成および追加の機能のインスタンスを含むモデルを保存して、これらは、適切な拡張機能をインストールしている他のユーザーが読み取ることができます。 拡張機能をインストールしていないユーザーは、追加の機能を使用できませんが、更新、追加の機能を失うことがなく、モデルを保存します。  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>参照  
 [関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
