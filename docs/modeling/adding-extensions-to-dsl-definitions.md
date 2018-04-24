---
title: DSL 定義への拡張機能の追加
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7de01ec87ca4367dcd3453c41e38c653c5184beb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="add-extensions-to-dsl-definitions"></a>DSL 定義に拡張機能を追加します。

DSL 定義の拡張機能では、ドメイン固有言語 (DSL) の拡張機能のパッケージを作成することができます。 Visual Studio Integration Extension (VSIX) に含まれる、DSL の拡張機能は、DSL と同じ方法でユーザーのコンピューターにインストールできます。 追加の機能を動的に有効になっているし、実行時に無効になっています。 Dsl を明示的に拡張機能に合わせて設計する必要はありません、拡張機能以降、またはサード パーティによる拡張の DSL を変更することがなく設計します。

DSL の拡張機能は、次の機能を含めることができます。

-   モデル、およびプレゼンテーション要素のプロパティ

-   図形とコネクタのデコレーター

-   クラス、リレーションシップ、図形、およびコネクタ

-   検証制約

-   ツールボックス項目とタブ

拡張の DSL のユーザーでは、作成でき、追加の機能のインスタンスを含むモデルを保存することができます。 モデルは、適切な拡張機能をインストールしている他のユーザーが読み取ることができます。 拡張機能をインストールしていないユーザーは、追加の機能を使用できませんが、更新、追加の機能を失うことがなく、モデルを保存します。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>関連項目

- [関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
