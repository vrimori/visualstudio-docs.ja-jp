---
title: "従来の言語サービスの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "言語サービスは、言語サービス [マネージ パッケージ framework]"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 従来の言語サービスの概要
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

言語サービスは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の特定の機能を実行できるようにするエディターをサポートします。  マネージ パッケージ フレームワーク \(MPF\) の言語サービス クラスはよく使用される機能を完全にサポートなどの機能を部分的なサポートが用意されています。  
  
## MPF の完全にサポートされている機能  
 MPF の言語サービス クラスは次の機能をサポートします :  
  
-   構文の強調表示  
  
-   アウトライン  
  
-   コードのコメント ブロック  
  
-   かっこの一致  
  
-   コード スニペット  
  
-   カスタム ドキュメント プロパティ  
  
-   IntelliSense のパラメーター情報  
  
-   IntelliSense でクイック ヒント  
  
-   IntelliSense のメンバーの完了  
  
-   IntelliSense の単語の入力候補  
  
## MPF 部分的にサポートされている機能  
 MPF は次の機能を部分的なサポートが用意されています。  これはMPF によって呼び出されるメソッドを実装する必要があります。  
  
-   コードの書式が再設定すること。  再設定するように実行するコードを指定します。  
  
-   ブレークポイントを有効なコード範囲を識別して検証します。  コード範囲を識別するコードを指定します。  
  
-   変数を表示するには\[出力\] ウィンドウ ENT0ENT なデバッガーをサポートします。  ウィンドウに表示される例外の処理を決定するコードを記述します。  
  
-   型とメンバー間ですばやく検索の  **ナビゲーション バー**  のサポート。   **ナビゲーション バー**  のコンボ ボックスのリストに設定するヘルパー クラスを実装して返します。  
  
## 実装  
 使用する言語をサポートする言語サービスの機能および言語サービス自体を実装するためにいくつかの手順を実行する必要があります。  これらの手順を次のトピックで説明します :  
  
-   [言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスにおけるかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのアウトライン](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [レガシ言語サービス内のコメント行のコード](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [従来の言語サービス内のコードを再フォーマット](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでカスタム ドキュメント プロパティ](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [従来の言語サービス内のナビゲーション バーのサポート](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでの単語の入力候補](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでのメンバーの完了](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスでパラメーター情報](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [従来の言語サービスのクイック ヒント](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [従来の言語サービスの \[自動変数\] ウィンドウのサポート](../Topic/Support%20for%20the%20Autos%20Window%20in%20a%20Legacy%20Language%20Service.md)  
  
-   [従来の言語サービス内のブレークポイントを検証します。](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## 参照  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [従来の言語サービスの拡張機能](../../extensibility/internals/legacy-language-service-extensibility.md)