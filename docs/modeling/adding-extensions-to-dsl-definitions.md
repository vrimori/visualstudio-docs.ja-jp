---
title: DSL 定義への拡張機能の追加
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9e4c80dee056d559822006627c86f4b4884942c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991137"
---
# <a name="add-extensions-to-dsl-definitions"></a>DSL 定義に拡張機能を追加する

DSL 定義の拡張機能では、ドメイン固有言語 (DSL) の拡張機能のパッケージを作成できます。 Visual Studio Integration Extension (VSIX) に含まれている、DSL の拡張機能は、DSL と同じ方法でユーザーのコンピューターにインストールできます。 追加の機能を動的に有効になっている、実行時に無効になっています。 Dsl を拡張機能を明示的に設計する必要はありません、拡張機能、後で、またはサード パーティが拡張の DSL を変更することがなく設計します。

DSL の拡張機能は、次の機能を含めることができます。

-   モデルとプレゼンテーション要素のプロパティ

-   シェイプとコネクタのデコレーター

-   クラス、リレーションシップ、図形、およびコネクタ

-   検証制約

-   ツールボックス項目とタブ

拡張の DSL のユーザーは、作成し、追加の機能のインスタンスを含むモデルを保存します。 適切な拡張機能がインストールされている他のユーザーでは、モデルを読み取ることができます。 拡張機能をインストールしていないユーザーは、追加の機能を使用できませんが、更新、追加の機能を失うことがなく、モデルを保存します。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>関連項目

- [関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
