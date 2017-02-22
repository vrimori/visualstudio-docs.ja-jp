---
title: "コードのコンテキスト | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] コンテキストのデバッグ"
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# コードのコンテキスト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の  **コード   コンテキスト** :  
  
-   デバッグ エンジン \(DE\) に認識されるようにコードの場所の抽象化を提供します。  今日ほとんどのランタイム アーキテクチャではコード コンテキストはプログラムの命令ストリームのアドレスと考えることができます。  コードの命令によって表されない場合は従来とは異なり言語ではコードのコンテキストでは他の方法で表すことがあります。  
  
-   デバッグするプログラムの実行ストリームの現在位置を示します。  
  
-   プログラムがブレークポイントで停止した場合のみ存在します。  
  
-   関連するドキュメントのコンテキストがあります。  
  
-   [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) のインターフェイスが実装されます。  
  
## 参照  
 [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)   
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)