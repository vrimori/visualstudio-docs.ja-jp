---
title: "64 ビット アプリケーションの配置のための必要条件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64 ビット [Visual Studio]"
  - "64 ビット アプリケーション [Visual Studio]"
  - "64 ビット プログラミング [Visual Studio]"
  - "配置 (アプリケーションを) [Visual Studio], 64 ビット"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 64 ビット アプリケーションの配置のための必要条件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce の配置では、 64 ビット プラットフォームのアプリケーションのインストールをサポートします。  対象プラットフォームは、32 ビット プラットフォームの場合は **x86**、AMD64 命令セットと EM64T 命令セットをサポートするコンピューターの場合は **x64**、64 ビットの Itanium プロセッサの場合は **Itanium** です。  
  
## 必須コンポーネント  
 64 ビット アプリケーションのインストール時の必須コンポーネントとして使用できる再頒布可能パッケージを次の表に示します。  
  
 64 ビット コンポーネントを含まない必須コンポーネントを選択した場合、選択したパッケージは 64 ビット プラットフォームで使用できないことを示す警告が表示される可能性があります。  
  
|再頒布可能パッケージ|x64 サポート|IA64 サポート|  
|----------------|--------------|---------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|○|Ｘ|  
|Visual C\+\+ 2010 ランタイム ライブラリ \(IA64\)|Ｘ|○|  
|Visual C\+\+ 2010 ランタイム ライブラリ \(x64\)|○|Ｘ|  
|Microsoft .NET Framework 4 \(x86 および x64\)|○||  
|Microsoft .NET Framework 4 Client Profile \(x86 および x64\)|○||  
  
## 参照  
 [アプリケーション、サービス、およびコンポーネントの配置](../deployment/deploying-applications-services-and-components.md)   
 [方法 : ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [64 ビット アプリケーション](../Topic/64-bit%20Applications.md)