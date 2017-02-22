---
title: "言語サービスを開発します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.vsip.LangServWiz.langtoks"
  - "vs.vsip.LangServWiz.welcome"
  - "vs.vsip.LangServWiz.langSpec"
  - "vs.vsip.LangServWiz.langInfo"
  - "vs.vsip.LangServWiz.langServOpts"
helpviewer_keywords: 
  - "開発言語サービス"
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# 言語サービスを開発します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このセクションにリンクするのに役立つトピックでは、従来の言語サービスを作成します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 言語サービスを実装する新しい方法の詳細については、次を参照してください。 [エディターと言語サービスの拡張機能](../../extensibility/editor-and-language-service-extensions.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## このセクションの内容  
 [従来の言語サービスのモデル](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 モデルの最小言語サービスの提供、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] コア エディターです。 言語サービスを作成するためのガイドとしてこのモデルを使用できます。  
  
 [従来の言語サービス インターフェイス](../../extensibility/internals/legacy-language-service-interfaces.md)  
 言語サービスの実装に必要なオブジェクトについて説明し、構文の強調表示、メソッドのデータ、およびその他の機能を提供に使用できるその他のオブジェクトの一覧を提供します。  
  
 [従来の言語サービスのコマンドを受信](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 テキスト ビューでは自動化切片コマンドに、言語サービスにコマンドのフィルターを挿入する方法について説明します。  
  
 [従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 使用して、言語サービスを登録する方法に関する情報を提供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
 [デバッグのための言語サービスのサポート](../../extensibility/internals/language-service-support-for-debugging.md)  
 言語サービスが、デバッガーをサポートする機能を提供する方法について説明します。  
  
 [チェックリスト: 従来の言語サービスを作成します。](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 作成およびコア エディターの言語サービスを統合するための手順を説明します。  
  
## 関連項目  
 [構文の色分けで従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 言語サービスで構文の強調表示を実装する方法について説明します。  
  
 [従来の言語サービスでのステートメント入力候補](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 ステートメント入力候補、言語サービスにより、ユーザーの言語のキーワードまたはキー入力を開始する要素が終了するプロセスについて説明します。  
  
 [従来の言語サービスでパラメーター情報](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 オーバー ロードされた関数とメソッドのメソッドのヒントを提供する方法について説明します。  
  
 [方法: レガシ言語サービスで非表示のテキストをサポート](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 非表示のテキスト領域の目的について説明し、非表示のテキスト領域を実装する方法について説明します。  
  
 [方法: レガシ言語サービスでの展開のアウトライン サポートを提供](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 使用する言語をサポートする以外のアウトラインのサポートを拡張する 2 つのオプションについて説明します、 *定義に縮小* コマンドです。