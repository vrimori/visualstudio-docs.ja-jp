---
title: "コード分析ツールを使用したアプリケーション品質の分析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.analysisresults"
helpviewer_keywords: 
  - "アプリケーション品質, 分析"
  - "コード分析"
  - "チーム ベースの開発, 分析 (アプリケーション品質を)"
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# コード分析ツールを使用したアプリケーション品質の分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## このセクションの内容  
 [マネージ コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 マネージ コードの Visual Studio コード分析を使用すると、Microsoft .NET Framework デザイン ガイドラインに規定されたプログラミングやデザインに関する規則違反など、マネージ アセンブリに関する情報を得ることができます。  警告メッセージは、プログラミングやデザイン上の問題を識別し、可能であれば問題の解決方法を提供します。  
  
 [C\/C\+\+ コードの品質の分析](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 C\/C\+\+ コード分析ツールは、C\/C\+\+ ソース コードの障害に関する情報を開発者に提供します。  このツールによってレポートされる一般的なコーディング エラーとしては、バッファー オーバーラン、初期化されていないメモリ、null ポインターの逆参照、メモリ リーク、リソース リークなどがあります。  
  
 [規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 *規則セット*を選択および作成し、プロジェクトに適用します。  
  
 [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)  
 コード分析機能のエラーを修正します。  
  
 [チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 Team Foundation バージョン管理 \(TFVC\) を使用すると、より優れたコードの記述や、より効率的なグループ開発につながる手法を実現する、チーム プロジェクト用のチェックイン ポリシーが作成できます。  チェックイン ポリシーとは、チーム プロジェクト レベルで設定され、コードをチェックインする前に開発者のコンピューターに適用される規則です。  
  
### ドライバーのコード分析  
 コード分析ツールでドライバーのソース コードを系統的に分析することにより、ドライバーの安定性と信頼性を向上させることができます。  
  
 [コード分析ツールを使用したドライバー品質の分析](http://go.microsoft.com/fwlink/?LinkId=227618)  
 ドライバーのコード分析は、C および C\+\+ プログラムの基本的なコーディング エラーを検出するコンパイル時の静的検証ツールで、主にカーネル モードのドライバー コードのエラーを検出するように設計された特殊なモジュールが含まれます。  静的ドライバー検証ツール \(SDV\) は、Windows カーネル モードのドライバーのソース コードを系統的に分析する静的検証ツールです。  SDV は、ドライバーが Windows オペレーティング システムのカーネルと適切にやり取りしているかどうかを判定します。  
  
 [ドライバー警告のコード分析](http://go.microsoft.com/fwlink/?LinkId=225920)  
 ドライバーのコード分析でドライバー コードに潜在的なエラーが検出されたときにレポートされる警告ついて説明します。  
  
## 関連タスク  
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 ここに説明を挿入します。  
  
 [コードの単体テスト](../test/unit-test-your-code.md)  
 ここに説明を挿入します。