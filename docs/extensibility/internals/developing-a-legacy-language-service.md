---
title: "レガシ言語サービスの開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords: language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e05fb3f0a33c0f033733c40b17d636243c18ee22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="developing-a-legacy-language-service"></a>レガシ言語サービスの開発
このセクションにリンクするのに役立つトピックでは、従来の言語サービスを作成します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターおよび言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスのモデル](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 モデルの最小限の言語サービスの提供、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コア エディターです。 言語サービスを作成するためのガイドとしてこのモデルを使用できます。  
  
 [従来の言語サービスのインターフェイス](../../extensibility/internals/legacy-language-service-interfaces.md)  
 言語サービスの実装に必要なオブジェクトについて説明し、構文の強調表示、メソッドのデータ、およびその他の機能を提供に使用できるその他のオブジェクトの一覧を提供します。  
  
 [従来の言語サービスのコマンドの受信](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 コマンドのフィルターをインターセプト コマンド テキスト ビューの処理とそれ以外の場合に、言語サービスに挿入する方法について説明します。  
  
 [レガシ言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 使用して、言語サービスを登録する方法に関する情報を提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [デバッグのための言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)  
 言語サービスが、デバッガーをサポートする機能を提供する方法について説明します。  
  
 [チェック リスト: 従来の言語サービスの作成](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 作成およびコア エディターの言語サービスを統合するための手順を説明します。  
  
## <a name="related-sections"></a>関連項目  
 [従来の言語サービスでの構文の色分け表示](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 言語サービスで構文の強調表示を実装する方法について説明します。  
  
 [従来の言語サービスでのステートメント入力補完](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 ステートメント入力候補、言語サービスやすく言語キーワードまたは入力が開始されている要素の終了プロセスについて説明します。  
  
 [従来の言語サービスでのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 オーバー ロードされた関数およびメソッドのメソッドのヒントを提供する方法について説明します。  
  
 [方法: 従来の言語サービスでの隠し文字サポートの提供](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 非表示のテキスト領域の目的について説明しを非表示のテキスト領域を実装する方法について説明します。  
  
 [方法: 従来の言語サービスでのアウトラインの拡張サポートの提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 使用する言語をサポートする以外のアウトラインのサポートを拡張する 2 つのオプションについて説明します、*定義に縮小*コマンド。