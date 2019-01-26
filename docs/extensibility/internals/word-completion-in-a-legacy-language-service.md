---
title: 従来の言語サービスで word の完了 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f89027e69c319c74e9c61ceb053edd9c2428548d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040805"
---
# <a name="word-completion-in-a-legacy-language-service"></a>従来の言語サービスでの単語補完
単語補完は、部分的に型指定された単語の文字がない場合に格納します。 補完候補の 1 つだけがあると、入力候補の文字が入力されると、word は完了します。 単語の一部には、1 つ以上の可能性が一致すると、候補の一覧が表示されます。 終了文字には、識別子が使用されない任意の文字を指定できます。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 詳細については、次を参照してください。[エディターと言語サービス拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="implementation-steps"></a>実装手順  
  
1. ユーザーが選択すると**入力候補**から、 **IntelliSense** ] メニューの [、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>コマンド言語サービスに送信されます。  
  
2. <xref:Microsoft.VisualStudio.Package.ViewFilter>クラスは、コマンド ウィンドウと呼び出しをキャッチ、<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>メソッドの解析の理由で<xref:Microsoft.VisualStudio.Package.ParseReason>します。  
  
3. <xref:Microsoft.VisualStudio.Package.Source>呼び出し、クラス、その、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>可能性がある単語の入力候補とツール ヒント内の単語の一覧を使用して、表示の一覧を取得するメソッド、<xref:Microsoft.VisualStudio.Package.CompletionSet>クラス。  
  
    1 つだけに一致する単語がある場合、<xref:Microsoft.VisualStudio.Package.Source>クラスがという単語を完了します。  
  
   または、スキャナーは、トリガーの値を返す場合<xref:Microsoft.VisualStudio.Package.TokenTriggers>識別子の最初の文字を入力すると、<xref:Microsoft.VisualStudio.Package.Source>クラスは、これを検出し、呼び出し、<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>メソッドの解析の理由で<xref:Microsoft.VisualStudio.Package.ParseReason>。 この場合、パーサーはメンバーの選択範囲の文字の存在を検出し、メンバーの一覧を指定する必要があります。  
  
## <a name="enabling-support-for-the-complete-word"></a>入力候補のサポートを有効にします。  
 単語の入力候補のセットのサポートを有効にする、`CodeSense`名前付きパラメーターに渡される、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>言語パッケージに関連付けられているユーザーの属性。 これにより設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>プロパティを<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。  
  
 パーサーが解析理由の値への応答の宣言の一覧を返す必要がある<xref:Microsoft.VisualStudio.Package.ParseReason>、単語補完の動作をします。  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource メソッドに入力候補を実装します。  
 単語補完、<xref:Microsoft.VisualStudio.Package.Source>クラスが呼び出す、<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>メソッドを<xref:Microsoft.VisualStudio.Package.AuthoringScope>可能性がある単語の一致項目の一覧を取得するクラス。 派生したクラスの一覧を実装する必要があります、<xref:Microsoft.VisualStudio.Package.Declarations>クラス。 参照してください、<xref:Microsoft.VisualStudio.Package.Declarations>クラスについては、メソッドを実装する必要があります。  
  
 一覧には、1 つの単語が含まれている場合、<xref:Microsoft.VisualStudio.Package.Source>クラスは、単語の一部の代わりにその単語を自動的に挿入します。 一覧には、1 つ以上の単語が含まれている場合、<xref:Microsoft.VisualStudio.Package.Source>クラスには、ユーザーが適切な選択肢を選択できるツール ヒントの一覧が表示されます。  
  
 例を見ても、<xref:Microsoft.VisualStudio.Package.Declarations>クラスの実装で[従来の言語サービスでのメンバー補完](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)します。