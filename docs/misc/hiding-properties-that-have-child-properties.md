---
title: "子プロパティを持つ非表示のプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロパティ (Visual Studio SDK)、非表示"
  - "プロパティ ウィンドウ、子プロパティを持つプロパティの非表示"
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 子プロパティを持つ非表示のプロパティ
子プロパティを持つプロパティを非表示にする場合 :  
  
-   親プロジェクトをプログラムによって子プロジェクトの一部の側面を制御するプロジェクト入れ子になった。  
  
-   特殊なデザイナーでコントロールを使用する開発者がコントロールのすべてのプロパティへの完全なアクセス許可を与える必要があります。  
  
-   オブジェクトのスコープの所有権がプロパティのビューを制限する場合は。  
  
### 子プロパティを持つプロパティを非表示にするには  
  
1.  `FALSE` に <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> の `pfDisplay` のパラメーターを設定します。  
  
2.  `TRUE` に <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> の `pfHide` のパラメーターを設定します。  
  
## 参照  
 [プロパティ グリッドの表示\]](../extensibility/internals/properties-display-grid.md)