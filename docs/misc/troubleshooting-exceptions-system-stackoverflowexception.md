---
title: "例外のトラブルシューティング : System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "StackOverflowException クラス"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.StackOverflowException
入れ子のメソッド呼び出しが多すぎて実行スタックがオーバーフローすると、<xref:System.StackOverflowException> 例外がスローされます。  
  
## 関連するヒント  
 無限ループや無限再帰がないことを確認します。  
 一般に再帰が深いか、無限再帰の場合にメソッド呼び出しが過剰になります。  
  
## コメント  
 例外処理コードがスタックを必要とする場合があるため、スタック オーバーフロー例外をキャッチできません。 標準的なアプリケーションでスタック オーバーフローが発生すると、共通言語ランタイム \(CLR: Common Language Runtime\) がプロセスを終了します。  
  
 CLR をホストするアプリケーションは、既定の動作を変更して、例外が発生してもプロセスを続行させるアプリケーション ドメインを CLR がアンロードするように指定できます。 詳細については、「[ICLRPolicyManager インターフェイス](../Topic/ICLRPolicyManager%20Interface.md)」を参照してください。  
  
## 参照  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Loop Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/loop-structures)