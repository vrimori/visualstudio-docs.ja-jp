---
title: 従来の言語サービスの開発 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 801a349b588a1dd7612b573fcc97b4b344a69452
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746795"
---
# <a name="developing-a-legacy-language-service"></a>従来の言語サービスの開発
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このセクションにリンクする際に役立つトピックへは、従来の言語サービスを作成します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 言語サービスを実装する新しい方法の詳細についてを参照してください。[エディターと言語サービス拡張](../../extensibility/editor-and-language-service-extensions.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [従来の言語サービスのモデル](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 モデルの最小言語サービスの提供、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]のコア エディター。 このモデルは、独自の言語サービスを作成するためのガイドとして使用できます。  
  
 [従来の言語サービスのインターフェイス](../../extensibility/internals/legacy-language-service-interfaces.md)  
 言語サービスを実装するために必要なオブジェクトについて説明し、構文の強調表示、メソッドのデータ、およびその他の機能を提供するのに使用できるその他のオブジェクトの一覧を提供します。  
  
 [従来の言語サービスのコマンドの受信](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 コマンドのフィルターをインターセプト コマンド テキスト ビューの処理とそれ以外の場合に、言語サービスに挿入する方法について説明します。  
  
 [従来の言語サービスの登録](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 使用して、言語サービスを登録する方法についての情報を提供します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 [デバッグのための言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)  
 言語サービスが、デバッガーをサポートする機能を提供する方法について説明します。  
  
 [チェック リスト: 従来の言語サービスの作成](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 作成すると、コア エディターの言語サービスを統合する手順について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [従来の言語サービスでの構文の色分け表示](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 言語サービスで構文の強調表示を実装する方法について説明します。  
  
 [従来の言語サービスでのステートメント入力補完](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 ステートメント入力候補、言語サービスにより、ユーザーの言語キーワードまたは入力が開始要素を完了するプロセスについて説明します。  
  
 [従来の言語サービスのパラメーター ヒント](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 オーバー ロードされた関数とメソッドのメソッドのヒントを提供する方法について説明します。  
  
 [方法: 従来の言語サービスでの隠し文字サポートの提供](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 非表示のテキスト領域の目的について説明し、非表示のテキスト領域を実装する方法について説明します。  
  
 [方法: 従来の言語サービスでのアウトラインの拡張サポートの提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 お使いの言語をサポートしている以外のアウトラインのサポートを拡張する 2 つのオプションについて説明します、*定義に折りたたむ*コマンド。

