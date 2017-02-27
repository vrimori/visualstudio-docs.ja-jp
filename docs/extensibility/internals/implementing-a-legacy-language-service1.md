---
title: "レガシ言語 Service1 を実装します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マネージ言語サービス"
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 従来の言語サービスを実装します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

構文の強調表示、かっこの一致、および IntelliSense 補完など、さまざまな機能をサポートする従来の言語サービスを実装するのにマネージ パッケージ フレームワーク \(MPF\) 内のクラスを使用できます。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 言語サービスを実装する新しい方法の詳細については、次を参照してください。 [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## このセクションの内容  
 [従来の言語サービスの概要](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF でサポートされている言語サービスの機能の概要。  
  
 [言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 MPF を使用して、言語サービスを実装するための要件について説明します。  
  
 [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 MPF ベースの言語サービスを登録するために必要な手順について説明 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 MPF を使用して言語サービスのすべての機能を実装するために必要な 2 つのパーサーをについて説明します。  
  
 [チュートリアル: 従来の言語サービスの作成](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 VSPackage で MPF 言語サービスを実装するために必要な基本的な手順を示します。  
  
 [チュートリアル: インストールされているコード スニペット \(従来の実装\) の一覧を取得します。](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 インストールされているコード スニペットの一覧を取得する方法を示します。  
  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)  
 必要な作業 MPF を使用して言語サービスのすべての機能を実装する詳細トピックへのリンクを提供します。