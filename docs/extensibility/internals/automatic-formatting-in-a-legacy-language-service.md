---
title: "自動レガシ言語サービスで書式設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "言語サービス、自動の書式設定"
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 自動レガシ言語サービスで書式設定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

オートフォーマットによって言語サービスではユーザーが既知のコード コンストラクターの入力を開始するとコードのスニペットを挿入します。  
  
## オートフォーマットの動作  
 たとえば`if` を入力すると言語サービスが自動的に対応する中かっこが挿入または Enter キーを押すと前の行は新しいスコープを作成することも言語サービスは適切なインデント レベルに新しい行にカーソルをによって強制的に実行します。  
  
 言語サービスの他に使用するコマンドのフィルターはオートフォーマットに使用できます。  または <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> を呼び出して対応する中かっこが強調表示できます。  
  
## 参照  
 [言語サービスを開発します。](../../extensibility/internals/developing-a-legacy-language-service.md)