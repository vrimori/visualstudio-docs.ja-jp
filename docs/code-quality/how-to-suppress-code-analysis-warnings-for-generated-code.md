---
title: '方法: 生成されたコードに対するコード分析の警告を抑制する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac2c5d4a7aca3f77feabc0aaba75d7f56a751821
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>方法: 生成されたコードに対するコード分析の警告を抑制する
マネージ コード コンパイラは、多くの場合、迅速なコードの開発を容易にするためにプロジェクトに追加されるコードを生成します。 さらに、開発者は、アプリケーションをすばやく開発するのに役立つサード パーティ製ツールを使用する多くの場合にします。 これらのツールでは、プロジェクトに追加されるコードも生成します。

 生成されたコードでは、検出コード分析規則違反を表示する場合があります。 ただし場合に、表示し、違反を含むコードを維持することはできません参照しない可能性があります。

 **生成されたコードから結果を表示しない**コード分析のプロパティ ページで、プロジェクトのチェック ボックスでは、サード パーティ製ツールによって生成されたコードからコード分析の警告を表示するかどうかを選択することができます。

> [!NOTE]
>  このオプションは抑制コード分析エラーと警告が生成されたコードからフォームやテンプレートで、エラーと警告が表示される場合。 フォームまたはテンプレートのソース コードは表示することも保持することもできます。

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>プロジェクトで生成されたコードの警告を抑制します。

1.  ソリューション エクスプ ローラーでプロジェクトを右クリックし、をクリックして**プロパティ**です。

2.  をクリックして**コード分析**です。

3.  選択、**生成されたコードから結果を表示しない**チェック ボックスをオンします。