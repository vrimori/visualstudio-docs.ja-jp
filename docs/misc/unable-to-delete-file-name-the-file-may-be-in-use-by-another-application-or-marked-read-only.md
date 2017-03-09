---
title: "Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_DELETEFILEFAILED"
  - "vs.message.0x800A00A2"
ms.assetid: 5c425dca-1d28-47a8-a11c-6a890be10baf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only.
このエラーが発生するのは一般的に、削除するために選択したキーボード スキームが使用中かまたは読み取り専用である場合です。  
  
### このエラーを解決するには  
  
1.  指定したファイルを別のアプリケーションが使用している場合は、そのアプリケーションを閉じます。  
  
     または  
  
     ファイルが読み取り専用の場合は、読み取り専用属性を解除します。  ファイルのプロパティ ダイアログ ボックスの読み取り専用属性、ファイル エクスプローラーで使用できるを変更できます。  
  
## 参照  
 [キーボード ショートカットの識別とカスタマイズ](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)