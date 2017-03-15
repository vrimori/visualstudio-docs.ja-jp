---
title: "例外のトラブルシューティング : System.Exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Exception 例外"
  - "基底クラス、例外"
  - "例外、基底クラス"
ms.assetid: fc15931a-9323-47c6-a42f-55d0534b939a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Exception
アプリケーションの実行中に発生したエラーを表します。 これは、すべての例外の基底クラスです。  
  
## 関連するヒント  
 **InnerException プロパティで詳細を確認する**  
 このエラーを修復するには、現在の例外を引き起こした内部例外 \(前回の例外\) に関する情報が必要です。 内部例外は、現在の例外の <xref:System.Exception.InnerException%2A> プロパティに格納されます。**\[例外処理アシスタント\]** ダイアログ ボックスの **\[詳細の表示\]** リンクを使用すると、<xref:System.Exception.InnerException%2A> プロパティにアクセスできます。  
  
 **マイ コードのみのデバッグを一時的にオフにする**  
 この例外は、自分が作成していないコードで発生した可能性があります。 そのコードをデバッグするには、マイ コードのみのデバッグをオフにする必要があります。 詳細については、「[\[全般\] \(\[オプション\] ダイアログ ボックス \- \[デバッグ\]\)](../Topic/General,%20Debugging,%20Options%20Dialog%20Box.md)」を参照してください。  
  
## 参照  
 <xref:System.Exception>   
 <xref:System.Exception.InnerException%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [方法 : 例外がスローされたときに中断する](../misc/how-to-break-when-an-exception-is-thrown.md)   
 [\[全般\] \(\[オプション\] ダイアログ ボックス \- \[デバッグ\]\)](../Topic/General,%20Debugging,%20Options%20Dialog%20Box.md)