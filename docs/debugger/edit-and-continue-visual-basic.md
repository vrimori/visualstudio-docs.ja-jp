---
title: "エディット コンティニュ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "VB"
helpviewer_keywords: 
  - "64-bit ディット コンティニュ"
  - "デバッグ [Visual Basic], エディット コンティニュ"
  - "エディット コンティニュ [Visual Basic]"
  - "エディット コンティニュ, 64 ビット"
  - "Visual Basic, エディット コンティニュ"
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 40
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エディット コンティニュ (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディット コンティニュは、中断モードでの実行中にコードを変更できるようにするための、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 用デバッグ機能です。  コードの編集を適用した後で、新しい編集でコードの実行を再開して編集結果を確認できます。  
  
 エディット コンティニュ機能は、中断モードで使用できます。  中断モードでは、命令ポインター \(ソース ウィンドウ内の黄色の矢印\) はメソッドまたはプロパティの本体内の実行可能なステートメント上にあり、次に実行される行を指します。  中断モードでは、ほとんどの種類の変更を実行可能なステートメントに加えることができます。この変更は、基になるプロジェクトに取り込まれます。  ただし、一般に、中断モードでは、パブリック メソッド、パブリック フィールド、クラス宣言などの宣言ステートメントの変更はできません。  
  
 許可されない編集を行った場合は、その変更に紫色の波下線が表示され、タスク一覧にタスクが表示されます。  エディット コンティニュを引き続き使用するには、許可されない編集を元に戻さなければなりません。  エディット コンティニュの外部であれば、許可されない編集が認められる場合もあります。  そのような許可されない編集の結果を保持するには、デバッグを停止してアプリケーションを再起動する必要があります。  
  
 エディット コンティニュは、.NET Framework 4.5.1 を対象にする 64 ビット プロジェクトでサポートされています。  
  
 **\[プロセスにアタッチ\]** を使用してデバッグを開始した場合は、エディット コンティニュはサポートされません。  エディット コンティニュは、最適化されたコード、マネージ コードとネイティブ コードの混合コード、または Compact Framework \(スマート デバイス\) プロジェクトではサポートされていません。  
  
 このセクションの各トピックでは、この機能の使用方法と許可されない種類の変更について詳しく説明します。  
  
## このセクションの内容  
 [方法 : エディット コンティニュの中断モード時に編集を適用する](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 中断モードにおいてコードの編集を適用する方法について説明します。  
  
 [Visual Basic エディット コンティニュでサポートされていない編集](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] エディット コンティニュで実行できない編集の種類について説明します。  
  
## 関連項目  
 [エディット コンティニュ](../debugger/edit-and-continue.md)  
 エディット コンティニュに関するトピックの一覧を提供します。