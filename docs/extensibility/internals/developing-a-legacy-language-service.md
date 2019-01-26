---
title: 従来の言語サービスの開発 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20a2d36ef9ddfd27bfa41619bccc36bd53c1ed6d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941668"
---
# <a name="develop-a-legacy-language-service"></a>従来の言語サービスを開発します。
このセクションにリンクする際に役立つトピックへは、従来の言語サービスを作成します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターと言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスのモデル](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 モデルの最小言語サービスの提供、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]のコア エディター。 このモデルは、独自の言語サービスを作成するためのガイドとして使用できます。  
  
 [従来の言語サービスのインターフェイス](../../extensibility/internals/legacy-language-service-interfaces.md)  
 言語サービスを実装するために必要なオブジェクトについて説明し、構文の強調表示、メソッドのデータ、およびその他の機能を提供するのに使用できるその他のオブジェクトの一覧を提供します。  
  
 [従来の言語サービスのコマンドをインターセプトします。](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 コマンドのフィルターをインターセプト コマンド テキスト ビューの処理とそれ以外の場合に、言語サービスに挿入する方法について説明します。  
  
 [従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 使用して、言語サービスを登録する方法についての情報を提供します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 [デバッグのための言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)  
 言語サービスが、デバッガーをサポートする機能を提供する方法について説明します。  
  
 [チェックリスト:従来の言語サービスを作成します。](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 作成すると、コア エディターの言語サービスを統合する手順について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [構文の色分け、従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 言語サービスで構文の強調表示を実装する方法について説明します。  
  
 [従来の言語サービスで入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 ステートメント入力候補、言語サービスにより、ユーザーの言語キーワードまたは入力が開始要素を完了するプロセスについて説明します。  
  
 [従来の言語サービスのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 オーバー ロードされた関数とメソッドのメソッドのヒントを提供する方法について説明します。  
  
 [方法: 従来の言語サービスで非表示のテキストのサポートを提供します。](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 非表示のテキスト領域の目的について説明し、非表示のテキスト領域を実装する方法について説明します。  
  
 [方法: 従来の言語サービスでのアウトラインの拡張のサポートを提供します。](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 お使いの言語をサポートしている以外のアウトラインのサポートを拡張する 2 つのオプションについて説明します、*定義に折りたたむ*コマンド。