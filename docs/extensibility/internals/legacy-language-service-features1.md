---
title: レガシ言語サービス Features1 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c931147d20454a920e20cec61e1f6000a9b043d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-features"></a>レガシ言語サービス機能
マネージ パッケージ フレームワーク (MPF) 言語サービスは、1 つ以上をサポートできる[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]構文の強調表示、IntelliSense、ブレークポイントの検証などの機能です。 各機能は、互いに独立して実装できますが、パーサーとスキャナーのみを必要とするスキャナー構文の強調表示を除くすべて必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスでのかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 かっこの照合とも呼ばれる、一致する言語のペアをサポートするための要件について説明します。  
  
 [従来の言語サービスのコメント コード](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 コメントを付けると、選択したコードのコメントを解除をサポートするための要件について説明します。  
  
 [従来の言語サービスのカスタム ドキュメント プロパティ](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 ソース ファイルに埋め込まれているドキュメントのプロパティをサポートするための要件について説明します。  
  
 [従来の言語サービスのアウトライン](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 非表示領域の実装をアウトライン表示をサポートするために必要な事項について説明します。  
  
 [従来の言語サービスの再フォーマット コード](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 コードの再フォーマットをサポートするための要件について説明します。  
  
 [従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 コード スニペットが挿入され、編集できるコードのセグメントをサポートするための要件について説明します。  
  
 [従来の言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 メソッドの入力には、メソッドのシグネチャを表示するため、IntelliSense パラメーター ヒント 操作をサポートするための要件について説明します。  
  
 [従来の言語サービスのクイック ヒント](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 識別子に関する情報を表示するため、intellisense によるクイック ヒントの操作をサポートするために必要な事項について説明します。  
  
 [従来の言語サービスでのメンバー補完](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 名前空間のメンバーを一覧から選択する場合、IntelliSense メンバー完了操作をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスでの単語補完](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 部分的に型指定された単語を完了するため、IntelliSense の入力候補の操作をサポートするための要件について説明します。  
  
 [従来の言語サービスでの自動変数ウィンドウのサポート](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 言語サービス行える操作をサポートするについて説明します、 **[自動変数]**ウィンドウは、デバッグ中です。  
  
 [従来の言語サービスでのナビゲーション バーのサポート](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 使用する方法について説明します、**ナビゲーション バー**クイック ナビゲーションを任意の種類とそのビューに表示されるファイル内のメンバーを提供するエディターのビューの上部にまたがって.  
  
 [従来の言語サービスでの構文の配色変更](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 ソース コードの構文の強調表示をサポートするための要件について説明します。  
  
 [従来の言語サービスでのブレークポイントの検証](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 言語サービスが行える、デバッガーの外部の検証のブレークポイントをサポートするについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [従来の言語サービスのパーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 パーサーと、マネージ パッケージ フレームワークを使用する言語サービスのすべての機能を実装するために必要なスキャナーについて説明します。  
  
 [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 MPF を使用して、言語サービスを実装するための要件について説明します。  
  
 [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 使用した MPF ベースの言語サービスを登録するために必要な手順について説明します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [IntelliSense の使用](../../ide/using-intellisense.md)  
 IntelliSense のしくみの言語リファレンスに簡単にアクセスについて説明します。  
  
 [レガシ言語サービスを実装します。](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Managed package framework (MPF) を使用してマネージ コードで言語の全機能を備えたサービスを実装する方法について説明します。