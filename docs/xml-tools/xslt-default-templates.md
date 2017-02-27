---
title: "XSLT の既定のテンプレート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# XSLT の既定のテンプレート
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XSLT 処理中、一致する明示的なテンプレート規則がスタイル シートに存在しない場合は既定のテンプレートが使用されます。既定のテンプレートはビルトイン テンプレート規則とも呼ばれ、W3C 勧告『XSLT 1.0』のセクション 5.8 で定義されています。XSLT プロセッサは、一致する明示的なテンプレート規則が存在しない場合でも、既定のテンプレートを使用することでノードを処理できます。ただし、ビルトイン テンプレート規則は、スタイル シートで明示的に定義されているわけではないため、XSLT 変換で予期しない結果や紛らわしい結果が生じる場合があります。  
  
 XSLT デバッガーで、XSLT の既定のテンプレートのコードを表示できるようになりました。XSLT 変換をステップ実行したときに、既定のテンプレートが使用された場合、デバッガーのウィンドウにはその既定のテンプレートが表示されます。これにより、既定のテンプレートのコードをステップ実行したり、特定の命令にブレークポイントを設定したりできます。  
  
## 参照  
 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)