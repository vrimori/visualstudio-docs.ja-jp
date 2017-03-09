---
title: "&lt;name&gt; is not a valid file name. | Microsoft Docs"
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
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid file name.
このエラーは、\[コマンド\] ウィンドウでファイルを新規作成しようとしたときに、サポートされていない文字をファイル名に含めた場合に発生します。  
  
 ファイル名には、以下の文字を含めることができません。  
  
-   シャープ記号 \(\#\)  
  
-   パーセント記号 \(%\)  
  
-   アンパサンド \(&\)  
  
-   アスタリスク \(\*\)  
  
-   縦棒 \(&#124;\)  
  
-   円記号 \(\\\)  
  
-   コロン \(:\)  
  
-   二重引用符 \("\)  
  
-   不等号 \(より小\) \(\<\)  
  
-   不等号 \(より大\) \(\>\)  
  
-   ピリオド \(.\)  
  
-   疑問符 \(?\)  
  
-   スラッシュ \(\/\)  
  
-   先行する空白または後続の空白 \(' '\)  
  
-   Windows または DOS の予約語 \(nul、aux、con、com1、lpt1 など\)  
  
### このエラーを解決するには  
  
-   上記の文字を含まない新しいファイル名を指定して、コマンドを入力します。  
  
## 参照  
 [NewFile コマンド](../ide/reference/new-file-command.md)   
 [Visual Studio コマンド](../ide/reference/visual-studio-commands.md)