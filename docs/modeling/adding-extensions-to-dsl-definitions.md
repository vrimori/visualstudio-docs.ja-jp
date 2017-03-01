---
title: "DSL 定義への拡張機能の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.lasthandoff: 02/22/2017

---
# <a name="adding-extensions-to-dsl-definitions"></a>DSL 定義への拡張機能の追加
DSL 定義の拡張機能では、ドメイン固有言語 (DSL) の拡張機能のパッケージを作成することができます。 Visual Studio Integration Extension (VSIX) 含まれている DSL の拡張機能は、DSL と同じ方法でユーザーのコンピューターにインストールできます。 追加の機能を動的に有効になっている、実行時に無効にできます。 Dsl を拡張機能では、明示的に設計する必要はありません、拡張後で、またはサード パーティによる拡張の DSL を変更することがなく設計します。  
  
 追加の機能を次に含めることができます。  
  
-   モデルとプレゼンテーション要素のプロパティ  
  
-   図形とコネクタのデコレータ  
  
-   クラス、リレーションシップ、図形とコネクタ  
  
-   検証制約  
  
-   ツールボックス項目やタブ  
  
 拡張の DSL のユーザーを作成して、追加の機能のインスタンスを含むモデルを保存し、これらは、適切な拡張機能をインストールした他のユーザーで読み取ることができます。 拡張機能をインストールしていないユーザーが追加機能を使用できませんが、更新および追加の機能を失うことがなく、モデルを保存することができます。  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>関連項目  
 [関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

