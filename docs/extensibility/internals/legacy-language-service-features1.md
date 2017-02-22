---
title: "従来の言語サービスの機能 | Microsoft Docs"
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
  - "言語サービス [マネージ パッケージ framework]"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスの機能
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

マネージ パッケージ フレームワーク \(MPF\) の言語サービスは構文を強調表示しIntelliSense やブレークポイントの検証などの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の一つ以上の機能をサポートできます。  各機能は他の実行された依存しないようにできますが強調表示はすべてパーサーおよびスキャナーをスキャナーで実現できる構文を除く必要です。  
  
## このセクションの内容  
 [従来の言語サービスにおけるかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 かっこの一致 \(または必要な一致するペア言語をサポートするために必要な処理について説明します。  
  
 [レガシ言語サービス内のコメント行のコード](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 必要な選択されているコードのコメントと uncommenting をサポートするために必要な処理について説明します。  
  
 [従来の言語サービスでカスタム ドキュメント プロパティ](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 必要なソース ファイルに埋め込まれているドキュメント プロパティをサポートするために必要な処理について説明します。  
  
 [従来の言語サービスでのアウトライン](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 必要な非表示の領域の実装によってアウトラインをサポートするために必要な処理について説明します。  
  
 [従来の言語サービス内のコードを再フォーマット](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 必要なコードを再設定するようにサポートするために必要な処理について説明します。  
  
 [従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 必要な挿入編集できるコードであるコードスニペットをサポートするために必要な処理について説明します。  
  
 [従来の言語サービスでパラメーター情報](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 メソッドが入力されるたびに必要なシグネチャを表示するための IntelliSense の \[パラメーター ヒント\] 操作をサポートするために必要な処理について説明します。  
  
 [従来の言語サービスのクイック ヒント](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 必要な識別子に関する情報を表示するための IntelliSense のクイック ヒントの操作をサポートするために必要な処理について説明します。  
  
 [従来の言語サービスでのメンバーの完了](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 必要な一覧から名前空間のメンバーを選択するための IntelliSense メンバーの操作をサポートするために必要な処理について説明します。  
  
 [従来の言語サービスでの単語の入力候補](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 必要な部分的に入力されたテキストを完了するための IntelliSense の入力候補の操作をサポートするために必要な処理について説明します。  
  
 [従来の言語サービスの \[自動変数\] ウィンドウのサポート](../Topic/Support%20for%20the%20Autos%20Window%20in%20a%20Legacy%20Language%20Service.md)  
 デバッグ中 ENT0ENT \[出力\] ウィンドウをサポートする言語サービスが実行できる操作を記述します。  
  
 [従来の言語サービス内のナビゲーション バーのサポート](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 エディター ビューの上部に  **ナビゲーション バー**  を型にすばやく検索またはそのビューで表示されるファイルのメンバーを指定する方法について説明します。  
  
 [従来の言語サービスでの構文の色分け](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 必要なソース・コードの構文の強調表示をサポートするために必要な処理について説明します。  
  
 [従来の言語サービス内のブレークポイントを検証します。](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 デバッガーの外部でブレークポイントの検証をサポートする言語サービスが実行できる操作を記述します。  
  
## 関連項目  
 [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 マネージ パッケージ フレームワークを使用する言語サービスのすべての機能を実行するために必要なスキャナー フェーズとパーサーについて説明します。  
  
 [言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 必要な言語サービスを実行するために必要な処理に MPF を使用してついて説明します。  
  
 [言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の MPF ベースの言語サービスを登録するために必要な手順について説明します。  
  
 [IntelliSense の使用方法](../../ide/using-intellisense.md)  
 IntelliSense の言語リファレンスのアクセスを簡単にする方法について説明します。  
  
 [従来の言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 マネージ パッケージ フレームワーク \(MPF\) がマネージ コードの機能を備えた言語サービスを実行する方法について説明します。