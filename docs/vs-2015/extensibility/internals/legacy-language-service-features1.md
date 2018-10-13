---
title: 従来の言語サービスの特徴 1 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e864f9899c274fe58da16cdb5581058dd20f725
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185398"
---
# <a name="legacy-language-service-features"></a>従来の言語サービスの機能
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

マネージ パッケージ フレームワーク (MPF) の言語サービスは、1 つ以上をサポートできる[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]構文の強調表示、IntelliSense、ブレークポイントの検証などの機能です。 各機能は独立して実装できますが、パーサーとスキャナーのみを必要とするスキャナー構文の強調表示を除くすべてが必要です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスでのかっこの一致](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 かっこの一致とも呼ばれる、一致する言語のペアをサポートするために必要なものについて説明します。  
  
 [従来の言語サービスのコメント コード](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 選択したコードのコメントを解除、注釈をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスのカスタム ドキュメント プロパティ](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 ソース ファイルに埋め込まれているドキュメントのプロパティをサポートするために必要なものについて説明します。  
  
 [従来の言語サービスのアウトライン](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 アウトラインの非表示の領域の実装をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスの再フォーマット コード](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 コードの再フォーマットをサポートするために必要なものについて説明します。  
  
 [従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 挿入され、編集できるコードのセグメントであるコード スニペットをサポートするために必要なものについて説明します。  
  
 [従来の言語サービスのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 メソッドの入力には、メソッド シグネチャを表示するためのパラメーター情報の IntelliSense 操作をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスのクイック ヒント](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 識別子に関する情報を表示するための IntelliSense によるクイック ヒントの操作をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスでのメンバー補完](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 名前空間のメンバーを一覧から選択するため、IntelliSense のメンバー入力候補の操作をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスでの単語補完](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 部分的に型指定された単語を完了するため、IntelliSense の入力候補の操作をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスでの自動変数ウィンドウのサポート](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 説明の言語サービスの実行をサポートすることができます、 **[自動変数]** ウィンドウは、デバッグ中です。  
  
 [従来の言語サービスでのナビゲーション バーのサポート](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 使用する方法について説明します、**ナビゲーション バー**任意の型またはそのビューに表示されるファイル内のメンバーに迅速なナビゲーションを提供するエディター ビューの上部に.  
  
 [従来の言語サービスでの構文の配色変更](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 ソース コードの構文の強調表示をサポートするために必要なものについて説明します。  
  
 [従来の言語サービスでのブレークポイントの検証](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 言語サービスが、デバッガーの外部の検証のブレークポイントをサポートするために行うことができますをについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [従来の言語サービスのパーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Managed package framework を使用する言語サービスのすべての機能を実装するために必要なスキャナーとパーサーについて説明します。  
  
 [従来の言語サービスの実装](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 MPF を使用して、言語サービスを実装するために必要なものについて説明します。  
  
 [従来の言語サービスの登録](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 MPF ベースの言語サービスを登録するために必要な手順について説明します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 [IntelliSense の使用](../../ide/using-intellisense.md)  
 IntelliSense のしくみの言語リファレンスに簡単にアクセスについて説明します。  
  
 [従来の言語サービスの実装](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Managed package framework (MPF) を使用して、マネージ コードでのフル機能の言語サービスを実装する方法について説明します。

