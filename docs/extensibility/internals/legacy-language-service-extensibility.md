---
title: "従来の言語サービスの拡張機能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "言語サービス"
  - "Visual Studio 言語サービス"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
caps.handback.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスの拡張機能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

言語サービスは、IDE でソース コードを編集するため、言語固有のサポートを提供します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 言語サービスを実装する新しい方法の詳細については、次を参照してください。 [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)します。  
  
 このセクションでは、構造と従来の言語サービスの実装について説明します。  
  
## このセクションの内容  
 [従来の言語サービスを移行します。](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Visual Studio 2008 から最新バージョンの言語サービスを更新する方法について説明します。  
  
 [従来の言語サービスの基礎](../../extensibility/internals/legacy-language-service-essentials.md)  
 Visual Studio プログラミング言語に統合する言語サービスを開発する方法に関する重要な情報を提供します。  
  
 [言語サービスを開発します。](../../extensibility/internals/developing-a-legacy-language-service.md)  
 言語サービスを作成するのに役立つトピックへのリンクを提供します。  
  
 [構文の色分けで従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 言語サービスで構文の強調表示をサポートする方法についてを説明します。  
  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 マネージ パッケージ フレームワーク \(MPF\) を使用して、マネージ コードでフル機能の言語サービスを実装する方法について説明します。  
  
 [シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 ライブラリと、IDE 内のシンボルのツリー ビューを参照するためのツールについて説明します。  
  
## 関連項目  
 [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)  
 Visual Studio エディターの概要を示します。  
  
 [デバッグのための言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)  
 Visual Studio Debugging SDK を作成し、プログラムをデバッグするためのデバッガー コンポーネントのカスタマイズに必要な情報が含まれてをに関する情報とリンクを提供します。