---
title: "&#39;Class_Initialize&#39; イベントはサポートされなくなりました | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42001"
  - "bc42001"
helpviewer_keywords: 
  - "BC42001"
ms.assetid: 31e7c383-894e-416c-b834-3688cc340ccf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Class_Initialize&#39; イベントはサポートされなくなりました
'Class\_Initialize' イベントはサポートされなくなりました。 クラスを初期化するには、' Sub New' を使用します。  
  
 以前のバージョンの [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の `Class_Initialize` イベントは、クラス コンストラクターに置き換えられています。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC42001  
  
### このエラーを解決するには  
  
-   `New` という名前の `Sub` プロシージャを 1 つ以上宣言してクラスを初期化します。 クラス インスタンスが新しく作成されると、`Sub New` が呼び出されます。  
  
## 参照  
 [Class\_Initialize Changes in Visual Basic](http://msdn.microsoft.com/ja-jp/2cd023cf-2869-4836-b08d-43822294beeb)   
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/ja-jp/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [ビルド内にありません: コンストラクターとデストラクターの使用](http://msdn.microsoft.com/ja-jp/548eebe1-86c4-4377-b2f5-447cb8be3d90)