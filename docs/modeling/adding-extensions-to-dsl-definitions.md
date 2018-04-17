---
title: DSL 定義への拡張機能の追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a689d902a58eb747cbaec0bf7cebd740ade3e9bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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

## <a name="see-also"></a>関連項目  
 [関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
