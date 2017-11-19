---
title: "レガシ言語 Service1 を実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18ff0fef277967dcb446f62120843f476ddb4a3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-legacy-language-service"></a>レガシ言語サービスを実装します。
構文の強調表示、かっこの照合、および IntelliSense 入力候補など、さまざまな機能をサポートする従来の言語サービスを実装するのにマネージ パッケージ フレームワーク (MPF) 内のクラスを使用できます。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターおよび言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスの概要](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF でサポートされている言語サービスの機能の概要。  
  
 [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 MPF を使用して、言語サービスを実装するための要件について説明します。  
  
 [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 使用した MPF ベースの言語サービスを登録するために必要な手順について説明します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [従来の言語サービスのパーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 MPF を使用して、言語サービスのすべての機能を実装するために必要な 2 つのパーサーをについて説明します。  
  
 [チュートリアル: 従来の言語サービスの作成](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 VSPackage に MPF 言語サービスを実装するために必要な基本的な手順を提供します。  
  
 [チュートリアル: インストールされているコード スニペットの一覧の取得 (従来の実装)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 インストールされているコード スニペットの一覧を取得する方法を示します。  
  
 [レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)  
 必要な作業 MPF を使用して、言語サービスのすべての機能を実装する詳細トピックへのリンクを提供します。