---
title: "F# のデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [F#]"
  - "F#, デバッグ"
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# F# のデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

F\# のデバッグは、他のマネージ言語のデバッグとほとんど同じですが、次の例外があります。  
  
-   **\[自動変数\]** ウィンドウに F\# 変数は表示されません。  
  
-   F\# ではエディット コンティニュはサポートされません。  デバッグ セッション中に F\# コードを編集することは可能ですが、そのような操作は避けてください。  コードの変更はデバッグ セッション中は適用されないため、デバッグ中に F\# コードを編集すると、ソース コードとデバッグ中のコードが一致しなくなります。  
  
-   デバッガーは F\# 式を認識しません。  F\# のデバッグ中にデバッガー ウィンドウまたはダイアログ ボックスに式を入力するには、式を C\# の構文に変換する必要があります。  F\# の式を C\# に変換するときは、C\# では等価を示す比較演算子として \=\= を使用しますが、F\# では単一の \= を使用することに注意してください。  
  
## 参照  
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)