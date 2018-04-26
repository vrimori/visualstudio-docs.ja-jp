---
title: XSLT の既定のテンプレート
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee9356724d9915bf3e19d8a892fb1a4b12c4fd16
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="xslt-default-templates"></a>XSLT の既定のテンプレート

XSLT 処理中、一致する明示的なテンプレート規則がスタイル シートに存在しない場合は既定のテンプレートが使用されます。 既定のテンプレートはビルトイン テンプレート規則とも呼ばれ、W3C 勧告『XSLT 1.0』のセクション 5.8 で定義されています。 XSLT プロセッサは、一致する明示的なテンプレート規則が存在しない場合でも、既定のテンプレートを使用することでノードを処理できます。 ただし、ビルトイン テンプレート規則は、スタイル シートで明示的に定義されているわけではないため、XSLT 変換で予期しない結果や紛らわしい結果が生じる場合があります。

XSLT デバッガーで、XSLT の既定のテンプレートのコードを表示できるようになりました。 XSLT 変換をステップ実行したときに、既定のテンプレートが使用された場合、デバッガーのウィンドウにはその既定のテンプレートが表示されます。 これにより、既定のテンプレートのコードをステップ実行したり、特定の命令にブレークポイントを設定したりできます。

## <a name="see-also"></a>関連項目

- [XSLT のデバッグ](../xml-tools/debugging-xslt.md)