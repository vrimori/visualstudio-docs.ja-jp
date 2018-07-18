---
title: 入力候補の単語がレガシ言語サービス |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72ddf4e7c755fdecf562f4c190abfb145e6f9819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141514"
---
# <a name="word-completion-in-a-legacy-language-service"></a>レガシ言語サービスでの単語補完
入力語の完了は、部分的に型指定された単語の文字がない場合に格納します。 1 つだけの補完候補があると、入力候補の文字を入力するときに、単語は完了します。 単語の一部には、複数の可能性が一致すると、候補の一覧が表示されます。 入力候補の文字は、識別子の使用されていない任意の文字を指定できます。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="implementation-steps"></a>実装手順  
  
1.  ユーザーが選択すると**入力候補**から、 **IntelliSense**  メニュー、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>コマンド言語サービスに送信されます。  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter>クラスは、コマンド ウィンドウと呼び出しをキャッチ、<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>解析理由をつけてメソッド<xref:Microsoft.VisualStudio.Package.ParseReason>です。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source>クラス、呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>可能性がある単語の入力候補およびを使用して、ツール ヒント内の単語の一覧表示の一覧を取得するメソッド、<xref:Microsoft.VisualStudio.Package.CompletionSet>クラスです。  
  
     1 つだけの一致する単語がある場合、<xref:Microsoft.VisualStudio.Package.Source>クラスがという単語を完了します。  
  
 代わりに、スキャナーがトリガー値を返す場合<xref:Microsoft.VisualStudio.Package.TokenTriggers>識別子の最初の文字を入力すると、<xref:Microsoft.VisualStudio.Package.Source>クラスは、これを検出し、呼び出し、<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>解析理由をつけてメソッド<xref:Microsoft.VisualStudio.Package.ParseReason>です。 この場合、パーサーはメンバーの選択範囲の文字の存在を検出し、メンバーの一覧を指定する必要があります。  
  
## <a name="enabling-support-for-the-complete-word"></a>入力候補のサポートを有効にします。  
 単語の入力候補のセットのサポートを有効にする、`CodeSense`名前付きパラメーターに渡される、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>言語パッケージに関連付けられているユーザーの属性です。 これにより設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>プロパティを<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラスです。  
  
 解析理由の値への応答、パーサーが宣言の一覧を返す必要があります<xref:Microsoft.VisualStudio.Package.ParseReason>、動作する word 完了します。  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource メソッドで入力候補の実装  
 単語の候補の<xref:Microsoft.VisualStudio.Package.Source>クラスの呼び出し、<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>メソッドを<xref:Microsoft.VisualStudio.Package.AuthoringScope>可能性がある単語の一致結果の一覧を取得するクラス。 派生したクラスの一覧を実装する必要があります、<xref:Microsoft.VisualStudio.Package.Declarations>クラスです。 参照してください、<xref:Microsoft.VisualStudio.Package.Declarations>クラスについては、メソッドを実装する必要があります。  
  
 一覧には、1 つの単語のみが含まれている場合、<xref:Microsoft.VisualStudio.Package.Source>クラスが自動的に単語の一部の代わりにその単語を挿入します。 一覧には、1 つ以上の単語が含まれている場合、<xref:Microsoft.VisualStudio.Package.Source>クラスは、ユーザーが適切な選択肢を選択できるツール ヒントの一覧を表示します。  
  
 例を見ても、<xref:Microsoft.VisualStudio.Package.Declarations>クラスの実装で[レガシ言語サービスでメンバー補完](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)です。