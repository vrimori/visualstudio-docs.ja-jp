---
title: 従来の言語サービスの概要 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 29d98bd0e474a503b84cb21a1bca25cb2836a433
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989601"
---
# <a name="legacy-language-service-overview"></a>従来の言語サービスの概要
言語サービスは、特定の実装することができますエディターのサポートを提供します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]機能します。 マネージ パッケージ フレームワーク (MPF) 言語のサービス クラスは、頻繁に使用される機能とその他の機能の部分的なサポートについての完全なサポートを提供します。  
  
## <a name="fully-supported-features-in-the-mpf"></a>MPF で完全にサポートされる機能  
 MPF 言語サービスのクラスは、次の機能をサポートします。  
  
-   構文の強調表示  
  
-   アウトライン  
  
-   コードのコメント ブロック  
  
-   かっこの一致  
  
-   コード スニペット  
  
-   カスタム ドキュメント プロパティ  
  
-   IntelliSense のパラメーター情報  
  
-   IntelliSense クイック ヒント  
  
-   IntelliSense メンバー入力候補  
  
-   IntelliSense の単語補完  
  
## <a name="partially-supported-features-in-the-mpf"></a>MPF で部分的にサポートされる機能  
 MPF は、次の機能のみ部分的にサポートを提供します。 つまり、MPF によって呼び出されるメソッドを実装する必要があります。  
  
-   コードの再フォーマットします。 再フォーマットを実装するコードを入力します。  
  
-   範囲の有効なコードを識別することによってブレークポイントを検証しています。 コードの範囲を識別するコードを入力します。  
  
-   デバッガーをサポートしている **[自動変数]** 変数を表示するためのウィンドウ。 ウィンドウに表示するアクションを決定するコードを入力します。  
  
-   サポートしている、**ナビゲーション バー**型とメンバー間ですばやく移動します。 実装しに含まれる一覧を設定するヘルパー クラスを返す、**ナビゲーション バー**コンボ ボックス。  
  
## <a name="implementation"></a>実装  
 言語サービス自体と、言語をサポートする言語サービスの機能を実装するいくつかの手順を完了する必要があります。 次の手順は、次のトピックについて説明します。  
  
-   [従来の言語サービスの実装](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [従来の言語サービスの登録](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
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
  
-   [従来の言語サービスのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [従来の言語サービスのクイック ヒント](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでの自動変数ウィンドウのサポート](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのブレークポイントの検証](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [従来の言語サービスの機能拡張](../../extensibility/internals/legacy-language-service-extensibility.md)