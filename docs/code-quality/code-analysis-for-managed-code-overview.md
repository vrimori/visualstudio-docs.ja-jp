---
title: "マネージ コードに対するコード分析の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectpropertypages.codeanalysis"
helpviewer_keywords: 
  - "コード分析、マネージ コード"
  - "マネージ コード、コード分析"
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 35
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# マネージ コードに対するコード分析の概要
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マネージ コードのコード分析を使用すると、マネージ アセンブリを分析し、Microsoft .NET Framework デザイン ガイドラインに規定されたプログラミングやデザインに関する規則違反など、アセンブリに関する情報をレポートとして得ることができます。  
  
 分析ツールは、分析中に実行するチェック項目を警告メッセージとして表示します。  警告メッセージは、プログラミングやデザイン上の問題を識別し、可能であれば問題の解決方法を提供します。  
  
## IDE \(統合開発環境\) の統合  
 開発者は、プロジェクトに対してコード分析を自動的に実行できるだけでなく、手動で実行することもできます。  
  
 プロジェクトをビルドするたびにコード分析を実行するには、プロジェクトのプロパティ ページで **\[ビルドに対するコード分析の有効化 \(定数 CODE\_ANALYSIS を定義\)\]** をオンにします。  詳細については、「[方法: 自動コード分析を有効\/無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)」を参照してください。  
  
 プロジェクトに対してコード分析を手動で実行するには、**\[分析\]** メニューの **\[*ProjectName* でコード分析を実行\]** をクリックします。  詳細については、「[方法: 自動コード分析を有効\/無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)」を参照してください。  
  
## 規則セット  
 マネージ コード用のコード分析規則は、*規則セット*にグループ化されています。  Microsoft の標準の規則セットのいずれかを使用するか、特定のニーズを満たす独自の規則セットを作成することができます。  詳細については、「[規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)」を参照してください。  
  
## ソース内抑制  
 警告が適用されないことを示すと役に立つことがよくあります。  これによって、開発者や、そのコードを後で確認する担当者は、その警告が既に調査済みであり、抑制されるのかまたは無視されるのかがわかります。  
  
 警告のソース内抑制は、カスタム属性を使用して実装します。  警告を抑制するには、次の例のように、属性 `SuppressMessage` をソース コードに追加します。  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 詳細については、「[SuppressMessage 属性を使用した警告の抑制](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)」を参照してください。  
  
## チェックイン ポリシーの一部としてのコード分析の実行  
 組織的な取り決めとして、チェックインされるすべてのコードが、特定のポリシーを満たしていることが必要な場合があります。  たとえば、次のようなポリシーが考えられます。  
  
-   チェックイン対象のコードにビルド エラーが存在しないこと。  
  
-   最近のビルドでコード分析が実行されていること。  
  
 これは、チェックイン ポリシーを指定することにより実現できます。  詳細については、「[チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)」を参照してください。  
  
## チーム ビルドの統合  
 ビルド システムの統合機能を使用すると、分析ツールをビルド プロセスの一環として実行できます。  詳細については、「[アプリケーションのビルド](../Topic/Build%20the%20application.md)」を参照してください。  
  
## 参照  
 [規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [方法: 自動コード分析を有効\/無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)