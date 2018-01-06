---
title: "レガシ言語サービスの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 05805e5cf4b21f4c7d233cab7dd8421ee76f626f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-overview"></a>レガシ言語サービスの概要
言語サービスが特定の実装できるエディターのサポートを提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]機能します。 Managed Package Framework (MPF) 言語のサービス クラスは、頻繁に使用される機能とその他の機能の部分的なサポートを完全にサポートを提供します。  
  
## <a name="fully-supported-features-in-the-mpf"></a>MPF で完全にサポートされる機能  
 MPF 言語サービス クラスは、次の機能をサポートします。  
  
-   構文の強調表示  
  
-   アウトライン  
  
-   コードのブロックのコメントを付ける  
  
-   中かっこの一致  
  
-   コード スニペット  
  
-   カスタム ドキュメント プロパティ  
  
-   IntelliSense のパラメーター情報  
  
-   IntelliSense クイック ヒント  
  
-   IntelliSense のメンバーの完了  
  
-   IntelliSense の単語補完  
  
## <a name="partially-supported-features-in-the-mpf"></a>MPF で部分的にサポートされる機能  
 MPF は、次の機能のみ部分的なサポートを提供します。 つまり、MPF によって呼び出されるメソッドを実装する必要があります。  
  
-   コードの再フォーマットします。 再フォーマットを実装するコードを入力します。  
  
-   範囲の有効なコードを識別することによってブレークポイントを検証しています。 コードの範囲を識別するコードを入力します。  
  
-   デバッガーをサポートする**[自動変数]**変数を表示するためのウィンドウ。 ウィンドウに表示するものを決定するコードを入力します。  
  
-   サポートする、**ナビゲーション バー**クイック型およびメンバーの間で移動できるようにします。 実装しに含まれる一覧を設定するヘルパー クラスを返す、**ナビゲーション バー**コンボ ボックス。  
  
## <a name="implementation"></a>実装  
 言語サービス自体と、対象の言語をサポートする言語サービスの機能を実装するいくつかの手順を完了する必要があります。 次の手順は、次のトピックで説明します。  
  
-   [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [従来の言語サービスでの構文の配色変更](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスのアウトライン](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスのコメント コード](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスの再フォーマット コード](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスのカスタム ドキュメント プロパティ](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのナビゲーション バーのサポート](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでの単語補完](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのメンバー補完](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [従来の言語サービスのクイック ヒント](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでの自動変数ウィンドウのサポート](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのブレークポイントの検証](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>参照  
 [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [従来の言語サービスの機能拡張](../../extensibility/internals/legacy-language-service-extensibility.md)