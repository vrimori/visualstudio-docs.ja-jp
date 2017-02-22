---
title: "入れ子になったプロジェクトを AddItem] ダイアログ ボックスのフィルター処理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フィルター処理、入れ子になったプロジェクト"
  - "入れ子になったプロジェクトでは、AddItem] ダイアログ ボックスのフィルター処理"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 入れ子になったプロジェクトを AddItem] ダイアログ ボックスのフィルター処理
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

入れ子になったプロジェクトの \[ENT0ENT\] ダイアログ ボックスを表示するときに親プロジェクトは項目がダイアログ ボックスに表示するかを制御できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> のインターフェイスは ENT0ENT \[出力\] ダイアログ ボックスにあるノードをフィルター処理することができます。  子プロジェクトが ENT6ENT \[出力\] ダイアログ ボックスを表示するときに親が `IVsFilterAddProjectItemDlg` のインターフェイスを実装し子のプロジェクトで他に表示される項目をフィルター処理できます。  
  
 プロジェクトが親プロジェクトの下の関数によってグループ化するとユーザーが入れ子になったプロジェクトのショートカット メニューの \[ENT0ENT\] を選択すると `IVsFilterAddProjectItemDlg` を実行できます。  `IvsFilterAddProjectItemDlg displays` を実行して特定のグループにのみ項目またはファイルを参照してください。  他のグループのプロジェクト項目はダイアログ ボックスから同じディレクトリに格納されても除外されます。  
  
 ユーザーが子の ENT0ENT \[出力\] ダイアログ ボックスを開くと親プロジェクトの `IVsFilterAddProjectItemDlg` のインターフェイスの実装が呼び出されます。  
  
 `IVsFilterAddProjectItemDlg` インターフェイスはカテゴリでフィルター処理を実行できます。  詳細については、「[項目を追加、新しい項目の追加\] ダイアログ ボックス](../Topic/Adding%20Items%20to%20the%20Add%20New%20Item%20Dialog%20Boxes.md)」および「[プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [項目を追加、新しい項目の追加\] ダイアログ ボックス](../Topic/Adding%20Items%20to%20the%20Add%20New%20Item%20Dialog%20Boxes.md)   
 [プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [入れ子のプロジェクト](../../extensibility/internals/nesting-projects.md)