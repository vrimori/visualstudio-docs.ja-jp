---
title: XSLT の既定のテンプレート |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b1d2f0a7102821041bf76f1e8dcd73ff01baacc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="xslt-default-templates"></a>XSLT の既定のテンプレート
XSLT 処理中、一致する明示的なテンプレート規則がスタイル シートに存在しない場合は既定のテンプレートが使用されます。 既定のテンプレートはビルトイン テンプレート規則とも呼ばれ、W3C 勧告『XSLT 1.0』のセクション 5.8 で定義されています。 XSLT プロセッサは、一致する明示的なテンプレート規則が存在しない場合でも、既定のテンプレートを使用することでノードを処理できます。 ただし、ビルトイン テンプレート規則は、スタイル シートで明示的に定義されているわけではないため、XSLT 変換で予期しない結果や紛らわしい結果が生じる場合があります。  
  
 XSLT デバッガーで、XSLT の既定のテンプレートのコードを表示できるようになりました。 XSLT 変換をステップ実行したときに、既定のテンプレートが使用された場合、デバッガーのウィンドウにはその既定のテンプレートが表示されます。 これにより、既定のテンプレートのコードをステップ実行したり、特定の命令にブレークポイントを設定したりできます。  
  
## <a name="see-also"></a>関連項目  
 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)